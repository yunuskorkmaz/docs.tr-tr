---
title: ODBC Şema Koleksiyonları
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: f0240e99d2420b0956d3c144f837b39e094bb78a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794723"
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="139f8-102">ODBC Şema Koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="139f8-102">ODBC Schema Collections</span></span>

<span data-ttu-id="139f8-103">Bu bölümde Microsoft SQL Server, Oracle ve Microsoft Jet için ODBC sürücüleri için şema koleksiyonu desteği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="139f8-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>

## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="139f8-104">Microsoft SQL Server ODBC sürücüsü</span><span class="sxs-lookup"><span data-stu-id="139f8-104">Microsoft SQL Server ODBC Driver</span></span>

<span data-ttu-id="139f8-105">Microsoft SQL Server ODBC sürücüsü, ortak şema koleksiyonlarına ek olarak aşağıdaki belirli şema koleksiyonlarını destekler:</span><span class="sxs-lookup"><span data-stu-id="139f8-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="139f8-106">Takvimleri</span><span class="sxs-lookup"><span data-stu-id="139f8-106">Tables</span></span>

- <span data-ttu-id="139f8-107">Dizinlerde</span><span class="sxs-lookup"><span data-stu-id="139f8-107">Indexes</span></span>

- <span data-ttu-id="139f8-108">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="139f8-108">Columns</span></span>

- <span data-ttu-id="139f8-109">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="139f8-109">Procedures</span></span>

- <span data-ttu-id="139f8-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="139f8-110">ProcedureColumns</span></span>

- <span data-ttu-id="139f8-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="139f8-111">ProcedureParameters</span></span>

- <span data-ttu-id="139f8-112">Görünümler</span><span class="sxs-lookup"><span data-stu-id="139f8-112">Views</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="139f8-113">Tablolar ve görünümler</span><span class="sxs-lookup"><span data-stu-id="139f8-113">Tables and Views</span></span>

|<span data-ttu-id="139f8-114">Tation</span><span class="sxs-lookup"><span data-stu-id="139f8-114">ColumnName</span></span>|<span data-ttu-id="139f8-115">DataType</span><span class="sxs-lookup"><span data-stu-id="139f8-115">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="139f8-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="139f8-116">TABLE_CAT</span></span>|<span data-ttu-id="139f8-117">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-117">String</span></span>|
|<span data-ttu-id="139f8-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="139f8-118">TABLE_SCHEM</span></span>|<span data-ttu-id="139f8-119">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-119">String</span></span>|
|<span data-ttu-id="139f8-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="139f8-120">TABLE_NAME</span></span>|<span data-ttu-id="139f8-121">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-121">String</span></span>|
|<span data-ttu-id="139f8-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="139f8-122">TABLE_TYPE</span></span>|<span data-ttu-id="139f8-123">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-123">String</span></span>|
|<span data-ttu-id="139f8-124">AÇIKLAMALARININ</span><span class="sxs-lookup"><span data-stu-id="139f8-124">REMARKS</span></span>|<span data-ttu-id="139f8-125">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-125">String</span></span>|

### <a name="indexes"></a><span data-ttu-id="139f8-126">Dizinlerde</span><span class="sxs-lookup"><span data-stu-id="139f8-126">Indexes</span></span>

|<span data-ttu-id="139f8-127">Tation</span><span class="sxs-lookup"><span data-stu-id="139f8-127">ColumnName</span></span>|<span data-ttu-id="139f8-128">DataType</span><span class="sxs-lookup"><span data-stu-id="139f8-128">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="139f8-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="139f8-129">TABLE_CAT</span></span>|<span data-ttu-id="139f8-130">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-130">String</span></span>|
|<span data-ttu-id="139f8-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="139f8-131">TABLE_SCHEM</span></span>|<span data-ttu-id="139f8-132">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-132">String</span></span>|
|<span data-ttu-id="139f8-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="139f8-133">TABLE_NAME</span></span>|<span data-ttu-id="139f8-134">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-134">String</span></span>|
|<span data-ttu-id="139f8-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="139f8-135">NON_UNIQUE</span></span>|<span data-ttu-id="139f8-136">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-136">Int16</span></span>|
|<span data-ttu-id="139f8-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="139f8-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="139f8-138">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-138">String</span></span>|
|<span data-ttu-id="139f8-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="139f8-139">INDEX_NAME</span></span>|<span data-ttu-id="139f8-140">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-140">String</span></span>|
|<span data-ttu-id="139f8-141">TÜRÜYLE</span><span class="sxs-lookup"><span data-stu-id="139f8-141">TYPE</span></span>|<span data-ttu-id="139f8-142">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-142">Int16</span></span>|
|<span data-ttu-id="139f8-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="139f8-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="139f8-144">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-144">Int16</span></span>|
|<span data-ttu-id="139f8-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="139f8-145">COLUMN_NAME</span></span>|<span data-ttu-id="139f8-146">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-146">String</span></span>|
|<span data-ttu-id="139f8-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="139f8-147">ASC_OR_DESC</span></span>|<span data-ttu-id="139f8-148">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-148">String</span></span>|
|<span data-ttu-id="139f8-149">ITE</span><span class="sxs-lookup"><span data-stu-id="139f8-149">CARDINALITY</span></span>|<span data-ttu-id="139f8-150">Int32</span><span class="sxs-lookup"><span data-stu-id="139f8-150">Int32</span></span>|
|<span data-ttu-id="139f8-151">SAYFALARI</span><span class="sxs-lookup"><span data-stu-id="139f8-151">PAGES</span></span>|<span data-ttu-id="139f8-152">Int32</span><span class="sxs-lookup"><span data-stu-id="139f8-152">Int32</span></span>|
|<span data-ttu-id="139f8-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="139f8-153">FILTER_CONDITION</span></span>|<span data-ttu-id="139f8-154">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-154">String</span></span>|
|<span data-ttu-id="139f8-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="139f8-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="139f8-156">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-156">String</span></span>|
|<span data-ttu-id="139f8-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="139f8-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="139f8-158">Bayt</span><span class="sxs-lookup"><span data-stu-id="139f8-158">Byte</span></span>|

### <a name="columns"></a><span data-ttu-id="139f8-159">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="139f8-159">Columns</span></span>

|<span data-ttu-id="139f8-160">Tation</span><span class="sxs-lookup"><span data-stu-id="139f8-160">ColumnName</span></span>|<span data-ttu-id="139f8-161">DataType</span><span class="sxs-lookup"><span data-stu-id="139f8-161">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="139f8-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="139f8-162">TABLE_CAT</span></span>|<span data-ttu-id="139f8-163">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-163">String</span></span>|
|<span data-ttu-id="139f8-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="139f8-164">TABLE_SCHEM</span></span>|<span data-ttu-id="139f8-165">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-165">String</span></span>|
|<span data-ttu-id="139f8-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="139f8-166">TABLE_NAME</span></span>|<span data-ttu-id="139f8-167">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-167">String</span></span>|
|<span data-ttu-id="139f8-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="139f8-168">COLUMN_NAME</span></span>|<span data-ttu-id="139f8-169">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-169">String</span></span>|
|<span data-ttu-id="139f8-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="139f8-170">DATA_TYPE</span></span>|<span data-ttu-id="139f8-171">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-171">Int16</span></span>|
|<span data-ttu-id="139f8-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="139f8-172">TYPE_NAME</span></span>|<span data-ttu-id="139f8-173">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-173">String</span></span>|
|<span data-ttu-id="139f8-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="139f8-174">COLUMN_SIZE</span></span>|<span data-ttu-id="139f8-175">Int32</span><span class="sxs-lookup"><span data-stu-id="139f8-175">Int32</span></span>|
|<span data-ttu-id="139f8-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="139f8-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="139f8-177">Int32</span><span class="sxs-lookup"><span data-stu-id="139f8-177">Int32</span></span>|
|<span data-ttu-id="139f8-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="139f8-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="139f8-179">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-179">Int16</span></span>|
|<span data-ttu-id="139f8-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="139f8-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="139f8-181">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-181">Int16</span></span>|
|<span data-ttu-id="139f8-182">YAPILAMAZ</span><span class="sxs-lookup"><span data-stu-id="139f8-182">NULLABLE</span></span>|<span data-ttu-id="139f8-183">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-183">Int16</span></span>|
|<span data-ttu-id="139f8-184">AÇIKLAMALARININ</span><span class="sxs-lookup"><span data-stu-id="139f8-184">REMARKS</span></span>|<span data-ttu-id="139f8-185">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-185">String</span></span>|
|<span data-ttu-id="139f8-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="139f8-186">COLUMN_DEF</span></span>|<span data-ttu-id="139f8-187">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-187">String</span></span>|
|<span data-ttu-id="139f8-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="139f8-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="139f8-189">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-189">Int16</span></span>|
|<span data-ttu-id="139f8-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="139f8-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="139f8-191">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-191">Int16</span></span>|
|<span data-ttu-id="139f8-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="139f8-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="139f8-193">Int32</span><span class="sxs-lookup"><span data-stu-id="139f8-193">Int32</span></span>|
|<span data-ttu-id="139f8-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="139f8-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="139f8-195">Int32</span><span class="sxs-lookup"><span data-stu-id="139f8-195">Int32</span></span>|
|<span data-ttu-id="139f8-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="139f8-196">IS_NULLABLE</span></span>|<span data-ttu-id="139f8-197">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-197">String</span></span>|
|<span data-ttu-id="139f8-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="139f8-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="139f8-199">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-199">String</span></span>|
|<span data-ttu-id="139f8-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="139f8-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="139f8-201">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-201">String</span></span>|
|<span data-ttu-id="139f8-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="139f8-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="139f8-203">Bayt</span><span class="sxs-lookup"><span data-stu-id="139f8-203">Byte</span></span>|

### <a name="procedures"></a><span data-ttu-id="139f8-204">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="139f8-204">Procedures</span></span>

|<span data-ttu-id="139f8-205">Tation</span><span class="sxs-lookup"><span data-stu-id="139f8-205">ColumnName</span></span>|<span data-ttu-id="139f8-206">DataType</span><span class="sxs-lookup"><span data-stu-id="139f8-206">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="139f8-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="139f8-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="139f8-208">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-208">String</span></span>|
|<span data-ttu-id="139f8-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="139f8-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="139f8-210">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-210">String</span></span>|
|<span data-ttu-id="139f8-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="139f8-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="139f8-212">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-212">String</span></span>|
|<span data-ttu-id="139f8-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="139f8-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="139f8-214">Int32</span><span class="sxs-lookup"><span data-stu-id="139f8-214">Int32</span></span>|
|<span data-ttu-id="139f8-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="139f8-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="139f8-216">Int32</span><span class="sxs-lookup"><span data-stu-id="139f8-216">Int32</span></span>|
|<span data-ttu-id="139f8-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="139f8-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="139f8-218">Int32</span><span class="sxs-lookup"><span data-stu-id="139f8-218">Int32</span></span>|
|<span data-ttu-id="139f8-219">AÇIKLAMALARININ</span><span class="sxs-lookup"><span data-stu-id="139f8-219">REMARKS</span></span>|<span data-ttu-id="139f8-220">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-220">String</span></span>|
|<span data-ttu-id="139f8-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="139f8-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="139f8-222">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-222">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="139f8-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="139f8-223">ProcedureColumns</span></span>

|<span data-ttu-id="139f8-224">Tation</span><span class="sxs-lookup"><span data-stu-id="139f8-224">ColumnName</span></span>|<span data-ttu-id="139f8-225">DataType</span><span class="sxs-lookup"><span data-stu-id="139f8-225">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="139f8-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="139f8-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="139f8-227">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-227">String</span></span>|
|<span data-ttu-id="139f8-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="139f8-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="139f8-229">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-229">String</span></span>|
|<span data-ttu-id="139f8-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="139f8-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="139f8-231">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-231">String</span></span>|
|<span data-ttu-id="139f8-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="139f8-232">COLUMN_NAME</span></span>|<span data-ttu-id="139f8-233">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-233">String</span></span>|
|<span data-ttu-id="139f8-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="139f8-234">COLUMN_TYPE</span></span>|<span data-ttu-id="139f8-235">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-235">Int16</span></span>|
|<span data-ttu-id="139f8-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="139f8-236">DATA_TYPE</span></span>|<span data-ttu-id="139f8-237">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-237">Int16</span></span>|
|<span data-ttu-id="139f8-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="139f8-238">TYPE_NAME</span></span>|<span data-ttu-id="139f8-239">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-239">String</span></span>|
|<span data-ttu-id="139f8-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="139f8-240">COLUMN_SIZE</span></span>|<span data-ttu-id="139f8-241">Int32</span><span class="sxs-lookup"><span data-stu-id="139f8-241">Int32</span></span>|
|<span data-ttu-id="139f8-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="139f8-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="139f8-243">Int32</span><span class="sxs-lookup"><span data-stu-id="139f8-243">Int32</span></span>|
|<span data-ttu-id="139f8-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="139f8-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="139f8-245">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-245">Int16</span></span>|
|<span data-ttu-id="139f8-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="139f8-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="139f8-247">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-247">Int16</span></span>|
|<span data-ttu-id="139f8-248">YAPILAMAZ</span><span class="sxs-lookup"><span data-stu-id="139f8-248">NULLABLE</span></span>|<span data-ttu-id="139f8-249">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-249">Int16</span></span>|
|<span data-ttu-id="139f8-250">AÇIKLAMALARININ</span><span class="sxs-lookup"><span data-stu-id="139f8-250">REMARKS</span></span>|<span data-ttu-id="139f8-251">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-251">String</span></span>|
|<span data-ttu-id="139f8-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="139f8-252">COLUMN_DEF</span></span>|<span data-ttu-id="139f8-253">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-253">String</span></span>|
|<span data-ttu-id="139f8-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="139f8-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="139f8-255">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-255">Int16</span></span>|
|<span data-ttu-id="139f8-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="139f8-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="139f8-257">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-257">Int16</span></span>|
|<span data-ttu-id="139f8-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="139f8-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="139f8-259">Int32</span><span class="sxs-lookup"><span data-stu-id="139f8-259">Int32</span></span>|
|<span data-ttu-id="139f8-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="139f8-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="139f8-261">Int32</span><span class="sxs-lookup"><span data-stu-id="139f8-261">Int32</span></span>|
|<span data-ttu-id="139f8-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="139f8-262">IS_NULLABLE</span></span>|<span data-ttu-id="139f8-263">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-263">String</span></span>|
|<span data-ttu-id="139f8-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="139f8-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="139f8-265">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-265">String</span></span>|
|<span data-ttu-id="139f8-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="139f8-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="139f8-267">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-267">String</span></span>|
|<span data-ttu-id="139f8-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="139f8-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="139f8-269">Bayt</span><span class="sxs-lookup"><span data-stu-id="139f8-269">Byte</span></span>|

### <a name="procedureparameters"></a><span data-ttu-id="139f8-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="139f8-270">ProcedureParameters</span></span>

|<span data-ttu-id="139f8-271">Tation</span><span class="sxs-lookup"><span data-stu-id="139f8-271">ColumnName</span></span>|<span data-ttu-id="139f8-272">DataType</span><span class="sxs-lookup"><span data-stu-id="139f8-272">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="139f8-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="139f8-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="139f8-274">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-274">String</span></span>|
|<span data-ttu-id="139f8-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="139f8-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="139f8-276">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-276">String</span></span>|
|<span data-ttu-id="139f8-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="139f8-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="139f8-278">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-278">String</span></span>|
|<span data-ttu-id="139f8-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="139f8-279">COLUMN_NAME</span></span>|<span data-ttu-id="139f8-280">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-280">String</span></span>|
|<span data-ttu-id="139f8-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="139f8-281">COLUMN_TYPE</span></span>|<span data-ttu-id="139f8-282">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-282">Int16</span></span>|
|<span data-ttu-id="139f8-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="139f8-283">DATA_TYPE</span></span>|<span data-ttu-id="139f8-284">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-284">Int16</span></span>|
|<span data-ttu-id="139f8-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="139f8-285">TYPE_NAME</span></span>|<span data-ttu-id="139f8-286">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-286">String</span></span>|
|<span data-ttu-id="139f8-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="139f8-287">COLUMN_SIZE</span></span>|<span data-ttu-id="139f8-288">Int32</span><span class="sxs-lookup"><span data-stu-id="139f8-288">Int32</span></span>|
|<span data-ttu-id="139f8-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="139f8-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="139f8-290">Int32</span><span class="sxs-lookup"><span data-stu-id="139f8-290">Int32</span></span>|
|<span data-ttu-id="139f8-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="139f8-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="139f8-292">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-292">Int16</span></span>|
|<span data-ttu-id="139f8-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="139f8-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="139f8-294">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-294">Int16</span></span>|
|<span data-ttu-id="139f8-295">YAPILAMAZ</span><span class="sxs-lookup"><span data-stu-id="139f8-295">NULLABLE</span></span>|<span data-ttu-id="139f8-296">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-296">Int16</span></span>|
|<span data-ttu-id="139f8-297">AÇIKLAMALARININ</span><span class="sxs-lookup"><span data-stu-id="139f8-297">REMARKS</span></span>|<span data-ttu-id="139f8-298">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-298">String</span></span>|
|<span data-ttu-id="139f8-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="139f8-299">COLUMN_DEF</span></span>|<span data-ttu-id="139f8-300">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-300">String</span></span>|
|<span data-ttu-id="139f8-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="139f8-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="139f8-302">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-302">Int16</span></span>|
|<span data-ttu-id="139f8-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="139f8-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="139f8-304">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-304">Int16</span></span>|
|<span data-ttu-id="139f8-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="139f8-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="139f8-306">Int32</span><span class="sxs-lookup"><span data-stu-id="139f8-306">Int32</span></span>|
|<span data-ttu-id="139f8-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="139f8-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="139f8-308">Int32</span><span class="sxs-lookup"><span data-stu-id="139f8-308">Int32</span></span>|
|<span data-ttu-id="139f8-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="139f8-309">IS_NULLABLE</span></span>|<span data-ttu-id="139f8-310">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-310">String</span></span>|
|<span data-ttu-id="139f8-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="139f8-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="139f8-312">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-312">String</span></span>|
|<span data-ttu-id="139f8-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="139f8-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="139f8-314">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-314">String</span></span>|
|<span data-ttu-id="139f8-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="139f8-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="139f8-316">Bayt</span><span class="sxs-lookup"><span data-stu-id="139f8-316">Byte</span></span>|

## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="139f8-317">Microsoft Oracle ODBC sürücüsü</span><span class="sxs-lookup"><span data-stu-id="139f8-317">Microsoft Oracle ODBC Driver</span></span>

<span data-ttu-id="139f8-318">Microsoft SQL Server Oracle ODBC sürücüsü, ortak şema koleksiyonlarına ek olarak aşağıdaki belirli şema koleksiyonlarını destekler:</span><span class="sxs-lookup"><span data-stu-id="139f8-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="139f8-319">Takvimleri</span><span class="sxs-lookup"><span data-stu-id="139f8-319">Tables</span></span>

- <span data-ttu-id="139f8-320">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="139f8-320">Columns</span></span>

- <span data-ttu-id="139f8-321">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="139f8-321">Procedures</span></span>

- <span data-ttu-id="139f8-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="139f8-322">ProcedureColumns</span></span>

- <span data-ttu-id="139f8-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="139f8-323">ProcedureParameters</span></span>

- <span data-ttu-id="139f8-324">Görünümler</span><span class="sxs-lookup"><span data-stu-id="139f8-324">Views</span></span>

- <span data-ttu-id="139f8-325">Dizinlerde</span><span class="sxs-lookup"><span data-stu-id="139f8-325">Indexes</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="139f8-326">Tablolar ve görünümler</span><span class="sxs-lookup"><span data-stu-id="139f8-326">Tables and Views</span></span>

|<span data-ttu-id="139f8-327">Tation</span><span class="sxs-lookup"><span data-stu-id="139f8-327">ColumnName</span></span>|<span data-ttu-id="139f8-328">DataType</span><span class="sxs-lookup"><span data-stu-id="139f8-328">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="139f8-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="139f8-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="139f8-330">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-330">String</span></span>|
|<span data-ttu-id="139f8-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="139f8-331">TABLE_OWNER</span></span>|<span data-ttu-id="139f8-332">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-332">String</span></span>|
|<span data-ttu-id="139f8-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="139f8-333">TABLE_NAME</span></span>|<span data-ttu-id="139f8-334">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-334">String</span></span>|
|<span data-ttu-id="139f8-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="139f8-335">TABLE_TYPE</span></span>|<span data-ttu-id="139f8-336">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-336">String</span></span>|
|<span data-ttu-id="139f8-337">AÇIKLAMALARININ</span><span class="sxs-lookup"><span data-stu-id="139f8-337">REMARKS</span></span>|<span data-ttu-id="139f8-338">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-338">String</span></span>|

### <a name="columns"></a><span data-ttu-id="139f8-339">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="139f8-339">Columns</span></span>

|<span data-ttu-id="139f8-340">Tation</span><span class="sxs-lookup"><span data-stu-id="139f8-340">ColumnName</span></span>|<span data-ttu-id="139f8-341">DataType</span><span class="sxs-lookup"><span data-stu-id="139f8-341">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="139f8-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="139f8-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="139f8-343">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-343">String</span></span>|
|<span data-ttu-id="139f8-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="139f8-344">TABLE_OWNER</span></span>|<span data-ttu-id="139f8-345">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-345">String</span></span>|
|<span data-ttu-id="139f8-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="139f8-346">TABLE_NAME</span></span>|<span data-ttu-id="139f8-347">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-347">String</span></span>|
|<span data-ttu-id="139f8-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="139f8-348">COLUMN_NAME</span></span>|<span data-ttu-id="139f8-349">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-349">String</span></span>|
|<span data-ttu-id="139f8-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="139f8-350">DATA_TYPE</span></span>|<span data-ttu-id="139f8-351">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-351">Int16</span></span>|
|<span data-ttu-id="139f8-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="139f8-352">TYPE_NAME</span></span>|<span data-ttu-id="139f8-353">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-353">String</span></span>|
|<span data-ttu-id="139f8-354">DUYARLILIK</span><span class="sxs-lookup"><span data-stu-id="139f8-354">PRECISION</span></span>|<span data-ttu-id="139f8-355">Int32</span><span class="sxs-lookup"><span data-stu-id="139f8-355">Int32</span></span>|
|<span data-ttu-id="139f8-356">UZUNLUKLU</span><span class="sxs-lookup"><span data-stu-id="139f8-356">LENGTH</span></span>|<span data-ttu-id="139f8-357">Int32</span><span class="sxs-lookup"><span data-stu-id="139f8-357">Int32</span></span>|
|<span data-ttu-id="139f8-358">ÖLÇEK</span><span class="sxs-lookup"><span data-stu-id="139f8-358">SCALE</span></span>|<span data-ttu-id="139f8-359">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-359">Int16</span></span>|
|<span data-ttu-id="139f8-360">TABAN</span><span class="sxs-lookup"><span data-stu-id="139f8-360">RADIX</span></span>|<span data-ttu-id="139f8-361">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-361">Int16</span></span>|
|<span data-ttu-id="139f8-362">YAPILAMAZ</span><span class="sxs-lookup"><span data-stu-id="139f8-362">NULLABLE</span></span>|<span data-ttu-id="139f8-363">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-363">Int16</span></span>|
|<span data-ttu-id="139f8-364">AÇIKLAMALARININ</span><span class="sxs-lookup"><span data-stu-id="139f8-364">REMARKS</span></span>|<span data-ttu-id="139f8-365">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-365">String</span></span>|
|<span data-ttu-id="139f8-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="139f8-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="139f8-367">Int32</span><span class="sxs-lookup"><span data-stu-id="139f8-367">Int32</span></span>|

### <a name="procedures"></a><span data-ttu-id="139f8-368">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="139f8-368">Procedures</span></span>

|<span data-ttu-id="139f8-369">Tation</span><span class="sxs-lookup"><span data-stu-id="139f8-369">ColumnName</span></span>|<span data-ttu-id="139f8-370">DataType</span><span class="sxs-lookup"><span data-stu-id="139f8-370">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="139f8-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="139f8-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="139f8-372">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-372">String</span></span>|
|<span data-ttu-id="139f8-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="139f8-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="139f8-374">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-374">String</span></span>|
|<span data-ttu-id="139f8-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="139f8-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="139f8-376">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-376">String</span></span>|
|<span data-ttu-id="139f8-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="139f8-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="139f8-378">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-378">Int16</span></span>|
|<span data-ttu-id="139f8-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="139f8-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="139f8-380">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-380">Int16</span></span>|
|<span data-ttu-id="139f8-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="139f8-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="139f8-382">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-382">Int16</span></span>|
|<span data-ttu-id="139f8-383">AÇIKLAMALARININ</span><span class="sxs-lookup"><span data-stu-id="139f8-383">REMARKS</span></span>|<span data-ttu-id="139f8-384">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-384">String</span></span>|
|<span data-ttu-id="139f8-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="139f8-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="139f8-386">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-386">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="139f8-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="139f8-387">ProcedureColumns</span></span>

|<span data-ttu-id="139f8-388">Tation</span><span class="sxs-lookup"><span data-stu-id="139f8-388">ColumnName</span></span>|<span data-ttu-id="139f8-389">DataType</span><span class="sxs-lookup"><span data-stu-id="139f8-389">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="139f8-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="139f8-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="139f8-391">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-391">String</span></span>|
|<span data-ttu-id="139f8-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="139f8-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="139f8-393">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-393">String</span></span>|
|<span data-ttu-id="139f8-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="139f8-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="139f8-395">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-395">String</span></span>|
|<span data-ttu-id="139f8-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="139f8-396">COLUMN_NAME</span></span>|<span data-ttu-id="139f8-397">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-397">String</span></span>|
|<span data-ttu-id="139f8-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="139f8-398">COLUMN_TYPE</span></span>|<span data-ttu-id="139f8-399">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-399">Int16</span></span>|
|<span data-ttu-id="139f8-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="139f8-400">DATA_TYPE</span></span>|<span data-ttu-id="139f8-401">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-401">Int16</span></span>|
|<span data-ttu-id="139f8-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="139f8-402">TYPE_NAME</span></span>|<span data-ttu-id="139f8-403">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-403">String</span></span>|
|<span data-ttu-id="139f8-404">DUYARLILIK</span><span class="sxs-lookup"><span data-stu-id="139f8-404">PRECISION</span></span>|<span data-ttu-id="139f8-405">Int32</span><span class="sxs-lookup"><span data-stu-id="139f8-405">Int32</span></span>|
|<span data-ttu-id="139f8-406">UZUNLUKLU</span><span class="sxs-lookup"><span data-stu-id="139f8-406">LENGTH</span></span>|<span data-ttu-id="139f8-407">Int32</span><span class="sxs-lookup"><span data-stu-id="139f8-407">Int32</span></span>|
|<span data-ttu-id="139f8-408">ÖLÇEK</span><span class="sxs-lookup"><span data-stu-id="139f8-408">SCALE</span></span>|<span data-ttu-id="139f8-409">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-409">Int16</span></span>|
|<span data-ttu-id="139f8-410">TABAN</span><span class="sxs-lookup"><span data-stu-id="139f8-410">RADIX</span></span>|<span data-ttu-id="139f8-411">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-411">Int16</span></span>|
|<span data-ttu-id="139f8-412">YAPILAMAZ</span><span class="sxs-lookup"><span data-stu-id="139f8-412">NULLABLE</span></span>|<span data-ttu-id="139f8-413">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-413">Int16</span></span>|
|<span data-ttu-id="139f8-414">AÇIKLAMALARININ</span><span class="sxs-lookup"><span data-stu-id="139f8-414">REMARKS</span></span>|<span data-ttu-id="139f8-415">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-415">String</span></span>|
|<span data-ttu-id="139f8-416">YÜKLEMEK</span><span class="sxs-lookup"><span data-stu-id="139f8-416">OVERLOAD</span></span>|<span data-ttu-id="139f8-417">Int32</span><span class="sxs-lookup"><span data-stu-id="139f8-417">Int32</span></span>|
|<span data-ttu-id="139f8-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="139f8-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="139f8-419">Int32</span><span class="sxs-lookup"><span data-stu-id="139f8-419">Int32</span></span>|

## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="139f8-420">Microsoft Jet ODBC sürücüsü</span><span class="sxs-lookup"><span data-stu-id="139f8-420">Microsoft Jet ODBC Driver</span></span>

<span data-ttu-id="139f8-421">Microsoft Jet ODBC sürücüsü, ortak şema koleksiyonlarına ek olarak aşağıdaki belirli şema koleksiyonlarını destekler:</span><span class="sxs-lookup"><span data-stu-id="139f8-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="139f8-422">Takvimleri</span><span class="sxs-lookup"><span data-stu-id="139f8-422">Tables</span></span>

- <span data-ttu-id="139f8-423">Dizinlerde</span><span class="sxs-lookup"><span data-stu-id="139f8-423">Indexes</span></span>

- <span data-ttu-id="139f8-424">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="139f8-424">Columns</span></span>

- <span data-ttu-id="139f8-425">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="139f8-425">Procedures</span></span>

- <span data-ttu-id="139f8-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="139f8-426">ProcedureColumns</span></span>

- <span data-ttu-id="139f8-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="139f8-427">ProcedureParameters</span></span>

- <span data-ttu-id="139f8-428">Görünümler</span><span class="sxs-lookup"><span data-stu-id="139f8-428">Views</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="139f8-429">Tablolar ve görünümler</span><span class="sxs-lookup"><span data-stu-id="139f8-429">Tables and Views</span></span>

|<span data-ttu-id="139f8-430">Tation</span><span class="sxs-lookup"><span data-stu-id="139f8-430">ColumnName</span></span>|<span data-ttu-id="139f8-431">DataType</span><span class="sxs-lookup"><span data-stu-id="139f8-431">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="139f8-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="139f8-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="139f8-433">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-433">String</span></span>|
|<span data-ttu-id="139f8-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="139f8-434">TABLE_OWNER</span></span>|<span data-ttu-id="139f8-435">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-435">String</span></span>|
|<span data-ttu-id="139f8-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="139f8-436">TABLE_NAME</span></span>|<span data-ttu-id="139f8-437">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-437">String</span></span>|
|<span data-ttu-id="139f8-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="139f8-438">TABLE_TYPE</span></span>|<span data-ttu-id="139f8-439">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-439">String</span></span>|
|<span data-ttu-id="139f8-440">AÇIKLAMALARININ</span><span class="sxs-lookup"><span data-stu-id="139f8-440">REMARKS</span></span>|<span data-ttu-id="139f8-441">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-441">String</span></span>|

### <a name="columns"></a><span data-ttu-id="139f8-442">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="139f8-442">Columns</span></span>

|<span data-ttu-id="139f8-443">Tation</span><span class="sxs-lookup"><span data-stu-id="139f8-443">ColumnName</span></span>|<span data-ttu-id="139f8-444">DataType</span><span class="sxs-lookup"><span data-stu-id="139f8-444">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="139f8-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="139f8-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="139f8-446">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-446">String</span></span>|
|<span data-ttu-id="139f8-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="139f8-447">TABLE_OWNER</span></span>|<span data-ttu-id="139f8-448">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-448">String</span></span>|
|<span data-ttu-id="139f8-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="139f8-449">TABLE_NAME</span></span>|<span data-ttu-id="139f8-450">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-450">String</span></span>|
|<span data-ttu-id="139f8-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="139f8-451">COLUMN_NAME</span></span>|<span data-ttu-id="139f8-452">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-452">String</span></span>|
|<span data-ttu-id="139f8-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="139f8-453">DATA_TYPE</span></span>|<span data-ttu-id="139f8-454">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-454">Int16</span></span>|
|<span data-ttu-id="139f8-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="139f8-455">TYPE_NAME</span></span>|<span data-ttu-id="139f8-456">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-456">String</span></span>|
|<span data-ttu-id="139f8-457">DUYARLILIK</span><span class="sxs-lookup"><span data-stu-id="139f8-457">PRECISION</span></span>|<span data-ttu-id="139f8-458">Int32</span><span class="sxs-lookup"><span data-stu-id="139f8-458">Int32</span></span>|
|<span data-ttu-id="139f8-459">UZUNLUKLU</span><span class="sxs-lookup"><span data-stu-id="139f8-459">LENGTH</span></span>|<span data-ttu-id="139f8-460">Int32</span><span class="sxs-lookup"><span data-stu-id="139f8-460">Int32</span></span>|
|<span data-ttu-id="139f8-461">ÖLÇEK</span><span class="sxs-lookup"><span data-stu-id="139f8-461">SCALE</span></span>|<span data-ttu-id="139f8-462">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-462">Int16</span></span>|
|<span data-ttu-id="139f8-463">TABAN</span><span class="sxs-lookup"><span data-stu-id="139f8-463">RADIX</span></span>|<span data-ttu-id="139f8-464">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-464">Int16</span></span>|
|<span data-ttu-id="139f8-465">YAPILAMAZ</span><span class="sxs-lookup"><span data-stu-id="139f8-465">NULLABLE</span></span>|<span data-ttu-id="139f8-466">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-466">Int16</span></span>|
|<span data-ttu-id="139f8-467">AÇIKLAMALARININ</span><span class="sxs-lookup"><span data-stu-id="139f8-467">REMARKS</span></span>|<span data-ttu-id="139f8-468">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-468">String</span></span>|
|<span data-ttu-id="139f8-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="139f8-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="139f8-470">Int32</span><span class="sxs-lookup"><span data-stu-id="139f8-470">Int32</span></span>|

### <a name="procedures"></a><span data-ttu-id="139f8-471">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="139f8-471">Procedures</span></span>

|<span data-ttu-id="139f8-472">Tation</span><span class="sxs-lookup"><span data-stu-id="139f8-472">ColumnName</span></span>|<span data-ttu-id="139f8-473">DataType</span><span class="sxs-lookup"><span data-stu-id="139f8-473">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="139f8-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="139f8-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="139f8-475">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-475">String</span></span>|
|<span data-ttu-id="139f8-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="139f8-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="139f8-477">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-477">String</span></span>|
|<span data-ttu-id="139f8-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="139f8-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="139f8-479">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-479">String</span></span>|
|<span data-ttu-id="139f8-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="139f8-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="139f8-481">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-481">Int16</span></span>|
|<span data-ttu-id="139f8-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="139f8-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="139f8-483">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-483">Int16</span></span>|
|<span data-ttu-id="139f8-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="139f8-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="139f8-485">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-485">Int16</span></span>|
|<span data-ttu-id="139f8-486">AÇIKLAMALARININ</span><span class="sxs-lookup"><span data-stu-id="139f8-486">REMARKS</span></span>|<span data-ttu-id="139f8-487">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-487">String</span></span>|
|<span data-ttu-id="139f8-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="139f8-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="139f8-489">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-489">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="139f8-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="139f8-490">ProcedureColumns</span></span>

|<span data-ttu-id="139f8-491">Tation</span><span class="sxs-lookup"><span data-stu-id="139f8-491">ColumnName</span></span>|<span data-ttu-id="139f8-492">DataType</span><span class="sxs-lookup"><span data-stu-id="139f8-492">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="139f8-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="139f8-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="139f8-494">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-494">String</span></span>|
|<span data-ttu-id="139f8-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="139f8-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="139f8-496">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-496">String</span></span>|
|<span data-ttu-id="139f8-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="139f8-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="139f8-498">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-498">String</span></span>|
|<span data-ttu-id="139f8-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="139f8-499">COLUMN_NAME</span></span>|<span data-ttu-id="139f8-500">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-500">String</span></span>|
|<span data-ttu-id="139f8-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="139f8-501">COLUMN_TYPE</span></span>|<span data-ttu-id="139f8-502">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-502">Int16</span></span>|
|<span data-ttu-id="139f8-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="139f8-503">DATA_TYPE</span></span>|<span data-ttu-id="139f8-504">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-504">Int16</span></span>|
|<span data-ttu-id="139f8-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="139f8-505">TYPE_NAME</span></span>|<span data-ttu-id="139f8-506">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-506">String</span></span>|
|<span data-ttu-id="139f8-507">DUYARLILIK</span><span class="sxs-lookup"><span data-stu-id="139f8-507">PRECISION</span></span>|<span data-ttu-id="139f8-508">Int32</span><span class="sxs-lookup"><span data-stu-id="139f8-508">Int32</span></span>|
|<span data-ttu-id="139f8-509">UZUNLUKLU</span><span class="sxs-lookup"><span data-stu-id="139f8-509">LENGTH</span></span>|<span data-ttu-id="139f8-510">Int32</span><span class="sxs-lookup"><span data-stu-id="139f8-510">Int32</span></span>|
|<span data-ttu-id="139f8-511">ÖLÇEK</span><span class="sxs-lookup"><span data-stu-id="139f8-511">SCALE</span></span>|<span data-ttu-id="139f8-512">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-512">Int16</span></span>|
|<span data-ttu-id="139f8-513">TABAN</span><span class="sxs-lookup"><span data-stu-id="139f8-513">RADIX</span></span>|<span data-ttu-id="139f8-514">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-514">Int16</span></span>|
|<span data-ttu-id="139f8-515">YAPILAMAZ</span><span class="sxs-lookup"><span data-stu-id="139f8-515">NULLABLE</span></span>|<span data-ttu-id="139f8-516">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-516">Int16</span></span>|
|<span data-ttu-id="139f8-517">AÇIKLAMALARININ</span><span class="sxs-lookup"><span data-stu-id="139f8-517">REMARKS</span></span>|<span data-ttu-id="139f8-518">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-518">String</span></span>|
|<span data-ttu-id="139f8-519">YÜKLEMEK</span><span class="sxs-lookup"><span data-stu-id="139f8-519">OVERLOAD</span></span>|<span data-ttu-id="139f8-520">Int32</span><span class="sxs-lookup"><span data-stu-id="139f8-520">Int32</span></span>|
|<span data-ttu-id="139f8-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="139f8-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="139f8-522">Int32</span><span class="sxs-lookup"><span data-stu-id="139f8-522">Int32</span></span>|

### <a name="procedureparameters"></a><span data-ttu-id="139f8-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="139f8-523">ProcedureParameters</span></span>

|<span data-ttu-id="139f8-524">Tation</span><span class="sxs-lookup"><span data-stu-id="139f8-524">ColumnName</span></span>|<span data-ttu-id="139f8-525">DataType</span><span class="sxs-lookup"><span data-stu-id="139f8-525">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="139f8-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="139f8-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="139f8-527">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-527">String</span></span>|
|<span data-ttu-id="139f8-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="139f8-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="139f8-529">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-529">String</span></span>|
|<span data-ttu-id="139f8-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="139f8-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="139f8-531">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-531">String</span></span>|
|<span data-ttu-id="139f8-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="139f8-532">COLUMN_NAME</span></span>|<span data-ttu-id="139f8-533">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-533">String</span></span>|
|<span data-ttu-id="139f8-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="139f8-534">COLUMN_TYPE</span></span>|<span data-ttu-id="139f8-535">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-535">Int16</span></span>|
|<span data-ttu-id="139f8-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="139f8-536">DATA_TYPE</span></span>|<span data-ttu-id="139f8-537">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-537">Int16</span></span>|
|<span data-ttu-id="139f8-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="139f8-538">TYPE_NAME</span></span>|<span data-ttu-id="139f8-539">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-539">String</span></span>|
|<span data-ttu-id="139f8-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="139f8-540">COLUMN_SIZE</span></span>|<span data-ttu-id="139f8-541">Int32</span><span class="sxs-lookup"><span data-stu-id="139f8-541">Int32</span></span>|
|<span data-ttu-id="139f8-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="139f8-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="139f8-543">Int32</span><span class="sxs-lookup"><span data-stu-id="139f8-543">Int32</span></span>|
|<span data-ttu-id="139f8-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="139f8-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="139f8-545">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-545">Int16</span></span>|
|<span data-ttu-id="139f8-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="139f8-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="139f8-547">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-547">Int16</span></span>|
|<span data-ttu-id="139f8-548">YAPILAMAZ</span><span class="sxs-lookup"><span data-stu-id="139f8-548">NULLABLE</span></span>|<span data-ttu-id="139f8-549">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-549">Int16</span></span>|
|<span data-ttu-id="139f8-550">AÇIKLAMALARININ</span><span class="sxs-lookup"><span data-stu-id="139f8-550">REMARKS</span></span>|<span data-ttu-id="139f8-551">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-551">String</span></span>|
|<span data-ttu-id="139f8-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="139f8-552">COLUMN_DEF</span></span>|<span data-ttu-id="139f8-553">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-553">String</span></span>|
|<span data-ttu-id="139f8-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="139f8-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="139f8-555">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-555">Int16</span></span>|
|<span data-ttu-id="139f8-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="139f8-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="139f8-557">Int16</span><span class="sxs-lookup"><span data-stu-id="139f8-557">Int16</span></span>|
|<span data-ttu-id="139f8-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="139f8-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="139f8-559">Int32</span><span class="sxs-lookup"><span data-stu-id="139f8-559">Int32</span></span>|
|<span data-ttu-id="139f8-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="139f8-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="139f8-561">Int32</span><span class="sxs-lookup"><span data-stu-id="139f8-561">Int32</span></span>|
|<span data-ttu-id="139f8-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="139f8-562">IS_NULLABLE</span></span>|<span data-ttu-id="139f8-563">Dize</span><span class="sxs-lookup"><span data-stu-id="139f8-563">String</span></span>|

## <a name="see-also"></a><span data-ttu-id="139f8-564">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="139f8-564">See also</span></span>

- [<span data-ttu-id="139f8-565">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="139f8-565">ADO.NET Overview</span></span>](ado-net-overview.md)
