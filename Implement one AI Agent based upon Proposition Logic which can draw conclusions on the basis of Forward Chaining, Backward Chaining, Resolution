class KnowledgeBase:
    def _init_(self):
        self.facts = set()
        self.rules = []

    def tell(self, fact):
        self.facts.add(fact)

    def add_rule(self, premises, conclusion):
        self.rules.append((premises, conclusion))

    def forward_chaining(self):
        inferred = set()
        while True:
            new_facts = set()
            for rule in self.rules:
                premises, conclusion = rule
                if all(p in self.facts.union(inferred) for p in premises) and conclusion not in self.facts:
                    new_facts.add(conclusion)
            if not new_facts:
                break
            inferred.update(new_facts)
            self.facts.update(new_facts)
        return inferred
def backward_chaining(self, goal, visited=None):
        if visited is None:
            visited = set()
        if goal in self.facts:
            return True
        if goal in visited:
            return False
        visited.add(goal)
        for premises, conclusion in self.rules:
            if conclusion == goal:
                if all(self.backward_chaining(p, visited) for p in premises):
                    return True
        return False

    def resolution(self, query):
        clauses = [set(self.facts)]
        for premises, conclusion in self.rules:
            clause = set(premises)
            clause.add('-' + conclusion)
            clauses.append(clause)
        clauses.append({query})
while True:
            new_clauses = []
            for i in range(len(clauses)):
                for j in range(i+1, len(clauses)):
                    resolvents = self._resolve(clauses[i], clauses[j])
                    if set() in resolvents:
        return True
                    new_clauses.extend(resolvents)
            if not new_clauses:
                return False
            clauses.extend(new_clauses)
            if len(clauses) > 1000:  # Set a threshold to avoid infinite loops
                return False
def _resolve(self, clause1, clause2):
        new_clauses = []
        for literal1 in clause1:
            for literal2 in clause2:
                if literal1 == '-' + literal2 or '-' + literal1 == literal2:
                    resolvent = (clause1 - {literal1}) | (clause2 - {literal2})
                    if resolvent not in new_clauses:
                        new_clauses.append(resolvent)
        return new_clauses
# Example usage:
kb = KnowledgeBase()
# Add facts
kb.tell("A")
kb.tell("B")
kb.add_rule(["A", "B"], "G")
kb.add_rule(["C"], "D")
kb.add_rule(["-D"], "H")
kb.add_rule(["G"], "E")
# Forward Chaining
print("Forward Chaining")
print(kb.forward_chaining())
# Backward Chaining
print("\nBackward Chaining")
print(kb.backward_chaining("E"))

# Resolution
print("\nResolution")
print(kb.resolution("E"))
