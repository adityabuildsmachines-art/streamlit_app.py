# streamlit_app.py
def __init__(self):
    # FIX: Added self. to make it accessible across the class
    self.domains = ["Logic", "Spatial", "Linguistic"]

def process_input(self, domain, raw_data, limits=0):
    """
    1. Logical: parse the raw values of the limits and the telemetry values 
    2. Spatial: Converting the given Data into 3D analogies 
    3. Linguistic: Professional Pitwall jargon extraction
    """
    
    # FIX: Defined metrics using raw_data since raw_delta was undefined
    metrics = re.findall(r'\d+', str(raw_data))

    # Step 2: Spatial Anchoring
    node_id = f"DT_{domain[:3]}_{len(metrics)}"

    # Step 3: Linguistic Structuring (Fixing JSON commas and colons)
    packet = {
        "Domain": domain if domain in self.domains else "GENERAL",
        "logical": {
            "raw_delta": raw_data - limits if isinstance(raw_data, (int, float)) else 0,
            "extracted_values": metrics,
            "node": node_id
        },
        "status": "DETERMINISTIC" if metrics else "VAGUE"
    }
    return packet
