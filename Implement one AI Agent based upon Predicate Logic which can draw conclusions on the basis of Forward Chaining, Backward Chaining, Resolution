class PredicateLogicAgent:
    def __init__(self, knowledge_base):
        self.knowledge_base = knowledge_base
    def forward_chaining(self, query)
         inferred = set()
        agenda = [query]
        while agenda:
            current = agenda.pop(0)
            if current not in inferred:
                inferred.add(current)
                for rule in self.knowledge_base:
                    if all(condition in inferred for condition in rule['conditions']):
                        agenda.append(rule['conclusion'])
        return inferred
    def backward_chaining(self, query):
        return self.backward_chaining_helper(query, set())
    def backward_chaining_helper(self, query, inferred):
        if query in inferred:
            return True
        for rule in self.knowledge_base:
            if query == rule['conclusion']:
                if all(self.backward_chaining_helper(condition, inferred) for condition in rule['conditions']):
                    inferred.add(query)
                    return True
        return False
    def resolution(self, query):
        clauses = [self.negate(query)]
        clauses.extend([self.negate(conclusion) for rule in self.knowledge_base for conclusion in rule['conditions']])
        while True:
            new_clauses = []
            for i in range(len(clauses)):
                for j in range(i + 1, len(clauses)):
                    resolvents = self.resolve(clauses[i], clauses[j])
                    if [] in resolvents:
                        return True  # Query is entailed
                    new_clauses.extend(resolvents)
            if set(new_clauses).issubset(set(clauses)):
                return False  # No new clauses were added, and query is not entailed
            clauses.extend(new_clauses)
    def resolve(self, clause1, clause2):
        resolvents = []
        for literal1 in clause1:
            for literal2 in clause2:
                if self.is_complement(literal1, literal2):
                    resolvent = [l for l in (clause1 + clause2) if l != literal1 and l != literal2]
                    resolvents.append(resolvent)
        return resolvents
    def is_complement(self, literal1, literal2):
        return literal1[0] == '~' and literal2 == literal1[1:] or literal2[0] == '~' and literal1 == literal2[1:]
    def negate(self, literal):
        return literal if literal[0] == '~' else '~' + literal
# Example usage:
knowledge_base = [
    {'conditions': ['P', 'Q'], 'conclusion': 'R'},
    {'conditions': ['~R'], 'conclusion': 'S'},
    {'conditions': ['P'], 'conclusion': 'Q'},
]
agent = PredicateLogicAgent(knowledge_base)
# Forward Chaining
result_forward_chaining = agent.forward_chaining('S')
print(f"Forward Chaining: {'S' in result_forward_chaining}")

# Backward Chaining
result_backward_chaining = agent.backward_chaining('S')
print(f"Backward Chaining: {result_backward_chaining}")
# Resolution
result_resolution = agent.resolution('S')
print(f"Resolution: {result_resolution}")
