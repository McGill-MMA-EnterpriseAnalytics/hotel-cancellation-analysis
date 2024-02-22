# Problem Statement

The hospitality industry frequently grapples with the twin challenges of overbooking and stringent cancellation policies, which, while designed to mitigate losses from cancellations, can inadvertently tarnish a hotel's reputation and diminish future revenue streams. In addressing the delicate balance of **maximizing occupancy** and **maintaining customer goodwill**, the implementation of a data-driven predictive model and a causal model with CATE emerge as pivotal solutions. This approach leverages predictive and causal inference models, offering a sophisticated method to evaluate the specific impact of management strategies on cancellation rates.

# Example ROI Estimation based on Causal Inference

## ROI Estimation for First-Time Guests Deposit Requirement

To estimate the ROI for implementing a deposit requirement for first-time guests, we will follow these steps:

1. **Determine the Average Revenue Per Booking (ARB)**: 
   This is the average revenue generated from each non-cancelled booking by a first-time guest. 
   - Let's assume an ARB of `$200`. (Source: )

2. **Estimate the Increase in Non-Cancellation Rates (INCR)**: 
   The CATE estimate suggests a reduction in cancellations by requiring a deposit.
   - Given CATE estimate of `-0.56`, the INCR is `56%`. (From CATE calculation)

3. **Calculate the Average Deposit Amount (ADA)**: 
   This is the average deposit required from first-time guests.
   - We will use an ADA of `$50`. (Source: )

4. **Estimate the Number of First-Time Bookings (NFB)**: 
   The total number of bookings by first-time guests in a given period.
   - Suppose we have `1000` NFB. (Arbitrary number)

5. **Calculate the Increased Revenue from Reduced Cancellations (IRRC)**:

   \[
   IRRC = ARB \times INCR \times NFB
   \]

   Plugging in our values:

   \[
   IRRC = $200 \times 0.56 \times 1000 = $112,000
   \]

6. **Calculate the Total Deposit Amount Collected (TDAC)**:

   \[
   TDAC = ADA \times NFB
   \]

   Again, using our values:

   \[
   TDAC = $50 \times 1000 = $50,000
   \]

7. **Estimate Costs Associated with Deposits (CAD)**:
   Additional costs due to the deposit policy. Assuming it's `10%` of the ADA: (Source: )

   \[
   CAD = 0.10 \times TDAC = 0.10 \times $50,000 = $5,000
   \]

8. **Calculate Net Gain from Deposits (NGD)**:

   \[
   NGD = TDAC - CAD = $50,000 - $5,000 = $45,000
   \]

9. **Estimate ROI**:

   \[
   ROI = \frac{IRRC + NGD}{CAD}
   \]

   With our values:

   \[
   ROI = \frac{$112,000 + $45,000}{$5,000} = \frac{$157,000}{$5,000} = 31.4
   \]

The ROI of `31.4` indicates that for every dollar spent on managing the deposit process, the hotel earns back `$31.40` in increased revenue and net gains from deposits. This calculation is an estimate based on assumptions provided by references and should be refined with more detailed data for precise planning.

# References: 

