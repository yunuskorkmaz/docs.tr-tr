---
description: 'Daha fazla bilgi edinin: ODBC şema koleksiyonları'
title: ODBC Şema Koleksiyonları
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: ceac67e49914db7010e315a2dfcdb630bea1e29f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786205"
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="4e438-103">ODBC Şema Koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="4e438-103">ODBC Schema Collections</span></span>

<span data-ttu-id="4e438-104">Bu bölümde Microsoft SQL Server, Oracle ve Microsoft Jet için ODBC sürücüleri için şema koleksiyonu desteği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4e438-104">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>

## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="4e438-105">Microsoft SQL Server ODBC sürücüsü</span><span class="sxs-lookup"><span data-stu-id="4e438-105">Microsoft SQL Server ODBC Driver</span></span>

<span data-ttu-id="4e438-106">Microsoft SQL Server ODBC sürücüsü, ortak şema koleksiyonlarına ek olarak aşağıdaki belirli şema koleksiyonlarını destekler:</span><span class="sxs-lookup"><span data-stu-id="4e438-106">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="4e438-107">Tablolar</span><span class="sxs-lookup"><span data-stu-id="4e438-107">Tables</span></span>

- <span data-ttu-id="4e438-108">Dizinler</span><span class="sxs-lookup"><span data-stu-id="4e438-108">Indexes</span></span>

- <span data-ttu-id="4e438-109">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="4e438-109">Columns</span></span>

- <span data-ttu-id="4e438-110">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="4e438-110">Procedures</span></span>

- <span data-ttu-id="4e438-111">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="4e438-111">ProcedureColumns</span></span>

- <span data-ttu-id="4e438-112">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="4e438-112">ProcedureParameters</span></span>

- <span data-ttu-id="4e438-113">Görünümler</span><span class="sxs-lookup"><span data-stu-id="4e438-113">Views</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="4e438-114">Tablolar ve görünümler</span><span class="sxs-lookup"><span data-stu-id="4e438-114">Tables and Views</span></span>

|<span data-ttu-id="4e438-115">ColumnName</span><span class="sxs-lookup"><span data-stu-id="4e438-115">ColumnName</span></span>|<span data-ttu-id="4e438-116">DataType</span><span class="sxs-lookup"><span data-stu-id="4e438-116">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="4e438-117">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="4e438-117">TABLE_CAT</span></span>|<span data-ttu-id="4e438-118">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-118">String</span></span>|
|<span data-ttu-id="4e438-119">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="4e438-119">TABLE_SCHEM</span></span>|<span data-ttu-id="4e438-120">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-120">String</span></span>|
|<span data-ttu-id="4e438-121">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="4e438-121">TABLE_NAME</span></span>|<span data-ttu-id="4e438-122">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-122">String</span></span>|
|<span data-ttu-id="4e438-123">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="4e438-123">TABLE_TYPE</span></span>|<span data-ttu-id="4e438-124">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-124">String</span></span>|
|<span data-ttu-id="4e438-125">AÇıKLAMALARıNıN</span><span class="sxs-lookup"><span data-stu-id="4e438-125">REMARKS</span></span>|<span data-ttu-id="4e438-126">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-126">String</span></span>|

### <a name="indexes"></a><span data-ttu-id="4e438-127">Dizinler</span><span class="sxs-lookup"><span data-stu-id="4e438-127">Indexes</span></span>

|<span data-ttu-id="4e438-128">ColumnName</span><span class="sxs-lookup"><span data-stu-id="4e438-128">ColumnName</span></span>|<span data-ttu-id="4e438-129">DataType</span><span class="sxs-lookup"><span data-stu-id="4e438-129">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="4e438-130">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="4e438-130">TABLE_CAT</span></span>|<span data-ttu-id="4e438-131">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-131">String</span></span>|
|<span data-ttu-id="4e438-132">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="4e438-132">TABLE_SCHEM</span></span>|<span data-ttu-id="4e438-133">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-133">String</span></span>|
|<span data-ttu-id="4e438-134">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="4e438-134">TABLE_NAME</span></span>|<span data-ttu-id="4e438-135">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-135">String</span></span>|
|<span data-ttu-id="4e438-136">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="4e438-136">NON_UNIQUE</span></span>|<span data-ttu-id="4e438-137">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-137">Int16</span></span>|
|<span data-ttu-id="4e438-138">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="4e438-138">INDEX_QUALIFIER</span></span>|<span data-ttu-id="4e438-139">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-139">String</span></span>|
|<span data-ttu-id="4e438-140">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="4e438-140">INDEX_NAME</span></span>|<span data-ttu-id="4e438-141">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-141">String</span></span>|
|<span data-ttu-id="4e438-142">TÜR</span><span class="sxs-lookup"><span data-stu-id="4e438-142">TYPE</span></span>|<span data-ttu-id="4e438-143">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-143">Int16</span></span>|
|<span data-ttu-id="4e438-144">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="4e438-144">ORDINAL_POSITION</span></span>|<span data-ttu-id="4e438-145">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-145">Int16</span></span>|
|<span data-ttu-id="4e438-146">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="4e438-146">COLUMN_NAME</span></span>|<span data-ttu-id="4e438-147">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-147">String</span></span>|
|<span data-ttu-id="4e438-148">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="4e438-148">ASC_OR_DESC</span></span>|<span data-ttu-id="4e438-149">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-149">String</span></span>|
|<span data-ttu-id="4e438-150">ITE</span><span class="sxs-lookup"><span data-stu-id="4e438-150">CARDINALITY</span></span>|<span data-ttu-id="4e438-151">Int32</span><span class="sxs-lookup"><span data-stu-id="4e438-151">Int32</span></span>|
|<span data-ttu-id="4e438-152">SAYFALARı</span><span class="sxs-lookup"><span data-stu-id="4e438-152">PAGES</span></span>|<span data-ttu-id="4e438-153">Int32</span><span class="sxs-lookup"><span data-stu-id="4e438-153">Int32</span></span>|
|<span data-ttu-id="4e438-154">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="4e438-154">FILTER_CONDITION</span></span>|<span data-ttu-id="4e438-155">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-155">String</span></span>|
|<span data-ttu-id="4e438-156">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4e438-156">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="4e438-157">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-157">String</span></span>|
|<span data-ttu-id="4e438-158">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4e438-158">SS_DATA_TYPE</span></span>|<span data-ttu-id="4e438-159">Bayt</span><span class="sxs-lookup"><span data-stu-id="4e438-159">Byte</span></span>|

### <a name="columns"></a><span data-ttu-id="4e438-160">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="4e438-160">Columns</span></span>

|<span data-ttu-id="4e438-161">ColumnName</span><span class="sxs-lookup"><span data-stu-id="4e438-161">ColumnName</span></span>|<span data-ttu-id="4e438-162">DataType</span><span class="sxs-lookup"><span data-stu-id="4e438-162">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="4e438-163">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="4e438-163">TABLE_CAT</span></span>|<span data-ttu-id="4e438-164">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-164">String</span></span>|
|<span data-ttu-id="4e438-165">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="4e438-165">TABLE_SCHEM</span></span>|<span data-ttu-id="4e438-166">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-166">String</span></span>|
|<span data-ttu-id="4e438-167">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="4e438-167">TABLE_NAME</span></span>|<span data-ttu-id="4e438-168">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-168">String</span></span>|
|<span data-ttu-id="4e438-169">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="4e438-169">COLUMN_NAME</span></span>|<span data-ttu-id="4e438-170">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-170">String</span></span>|
|<span data-ttu-id="4e438-171">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4e438-171">DATA_TYPE</span></span>|<span data-ttu-id="4e438-172">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-172">Int16</span></span>|
|<span data-ttu-id="4e438-173">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="4e438-173">TYPE_NAME</span></span>|<span data-ttu-id="4e438-174">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-174">String</span></span>|
|<span data-ttu-id="4e438-175">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="4e438-175">COLUMN_SIZE</span></span>|<span data-ttu-id="4e438-176">Int32</span><span class="sxs-lookup"><span data-stu-id="4e438-176">Int32</span></span>|
|<span data-ttu-id="4e438-177">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="4e438-177">BUFFER_LENGTH</span></span>|<span data-ttu-id="4e438-178">Int32</span><span class="sxs-lookup"><span data-stu-id="4e438-178">Int32</span></span>|
|<span data-ttu-id="4e438-179">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="4e438-179">DECIMAL_DIGITS</span></span>|<span data-ttu-id="4e438-180">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-180">Int16</span></span>|
|<span data-ttu-id="4e438-181">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="4e438-181">NUM_PREC_RADIX</span></span>|<span data-ttu-id="4e438-182">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-182">Int16</span></span>|
|<span data-ttu-id="4e438-183">YAPıLAMAZ</span><span class="sxs-lookup"><span data-stu-id="4e438-183">NULLABLE</span></span>|<span data-ttu-id="4e438-184">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-184">Int16</span></span>|
|<span data-ttu-id="4e438-185">AÇıKLAMALARıNıN</span><span class="sxs-lookup"><span data-stu-id="4e438-185">REMARKS</span></span>|<span data-ttu-id="4e438-186">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-186">String</span></span>|
|<span data-ttu-id="4e438-187">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="4e438-187">COLUMN_DEF</span></span>|<span data-ttu-id="4e438-188">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-188">String</span></span>|
|<span data-ttu-id="4e438-189">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4e438-189">SQL_DATA_TYPE</span></span>|<span data-ttu-id="4e438-190">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-190">Int16</span></span>|
|<span data-ttu-id="4e438-191">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="4e438-191">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="4e438-192">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-192">Int16</span></span>|
|<span data-ttu-id="4e438-193">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="4e438-193">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="4e438-194">Int32</span><span class="sxs-lookup"><span data-stu-id="4e438-194">Int32</span></span>|
|<span data-ttu-id="4e438-195">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="4e438-195">ORDINAL_POSITION</span></span>|<span data-ttu-id="4e438-196">Int32</span><span class="sxs-lookup"><span data-stu-id="4e438-196">Int32</span></span>|
|<span data-ttu-id="4e438-197">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="4e438-197">IS_NULLABLE</span></span>|<span data-ttu-id="4e438-198">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-198">String</span></span>|
|<span data-ttu-id="4e438-199">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4e438-199">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="4e438-200">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-200">String</span></span>|
|<span data-ttu-id="4e438-201">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4e438-201">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="4e438-202">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-202">String</span></span>|
|<span data-ttu-id="4e438-203">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4e438-203">SS_DATA_TYPE</span></span>|<span data-ttu-id="4e438-204">Bayt</span><span class="sxs-lookup"><span data-stu-id="4e438-204">Byte</span></span>|

### <a name="procedures"></a><span data-ttu-id="4e438-205">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="4e438-205">Procedures</span></span>

|<span data-ttu-id="4e438-206">ColumnName</span><span class="sxs-lookup"><span data-stu-id="4e438-206">ColumnName</span></span>|<span data-ttu-id="4e438-207">DataType</span><span class="sxs-lookup"><span data-stu-id="4e438-207">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="4e438-208">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="4e438-208">PROCEDURE_CAT</span></span>|<span data-ttu-id="4e438-209">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-209">String</span></span>|
|<span data-ttu-id="4e438-210">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="4e438-210">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="4e438-211">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-211">String</span></span>|
|<span data-ttu-id="4e438-212">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="4e438-212">PROCEDURE_NAME</span></span>|<span data-ttu-id="4e438-213">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-213">String</span></span>|
|<span data-ttu-id="4e438-214">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="4e438-214">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="4e438-215">Int32</span><span class="sxs-lookup"><span data-stu-id="4e438-215">Int32</span></span>|
|<span data-ttu-id="4e438-216">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="4e438-216">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="4e438-217">Int32</span><span class="sxs-lookup"><span data-stu-id="4e438-217">Int32</span></span>|
|<span data-ttu-id="4e438-218">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="4e438-218">NUM_RESULT_SETS</span></span>|<span data-ttu-id="4e438-219">Int32</span><span class="sxs-lookup"><span data-stu-id="4e438-219">Int32</span></span>|
|<span data-ttu-id="4e438-220">AÇıKLAMALARıNıN</span><span class="sxs-lookup"><span data-stu-id="4e438-220">REMARKS</span></span>|<span data-ttu-id="4e438-221">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-221">String</span></span>|
|<span data-ttu-id="4e438-222">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="4e438-222">PROCEDURE_TYPE</span></span>|<span data-ttu-id="4e438-223">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-223">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="4e438-224">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="4e438-224">ProcedureColumns</span></span>

|<span data-ttu-id="4e438-225">ColumnName</span><span class="sxs-lookup"><span data-stu-id="4e438-225">ColumnName</span></span>|<span data-ttu-id="4e438-226">DataType</span><span class="sxs-lookup"><span data-stu-id="4e438-226">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="4e438-227">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="4e438-227">PROCEDURE_CAT</span></span>|<span data-ttu-id="4e438-228">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-228">String</span></span>|
|<span data-ttu-id="4e438-229">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="4e438-229">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="4e438-230">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-230">String</span></span>|
|<span data-ttu-id="4e438-231">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="4e438-231">PROCEDURE_NAME</span></span>|<span data-ttu-id="4e438-232">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-232">String</span></span>|
|<span data-ttu-id="4e438-233">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="4e438-233">COLUMN_NAME</span></span>|<span data-ttu-id="4e438-234">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-234">String</span></span>|
|<span data-ttu-id="4e438-235">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="4e438-235">COLUMN_TYPE</span></span>|<span data-ttu-id="4e438-236">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-236">Int16</span></span>|
|<span data-ttu-id="4e438-237">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4e438-237">DATA_TYPE</span></span>|<span data-ttu-id="4e438-238">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-238">Int16</span></span>|
|<span data-ttu-id="4e438-239">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="4e438-239">TYPE_NAME</span></span>|<span data-ttu-id="4e438-240">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-240">String</span></span>|
|<span data-ttu-id="4e438-241">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="4e438-241">COLUMN_SIZE</span></span>|<span data-ttu-id="4e438-242">Int32</span><span class="sxs-lookup"><span data-stu-id="4e438-242">Int32</span></span>|
|<span data-ttu-id="4e438-243">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="4e438-243">BUFFER_LENGTH</span></span>|<span data-ttu-id="4e438-244">Int32</span><span class="sxs-lookup"><span data-stu-id="4e438-244">Int32</span></span>|
|<span data-ttu-id="4e438-245">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="4e438-245">DECIMAL_DIGITS</span></span>|<span data-ttu-id="4e438-246">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-246">Int16</span></span>|
|<span data-ttu-id="4e438-247">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="4e438-247">NUM_PREC_RADIX</span></span>|<span data-ttu-id="4e438-248">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-248">Int16</span></span>|
|<span data-ttu-id="4e438-249">YAPıLAMAZ</span><span class="sxs-lookup"><span data-stu-id="4e438-249">NULLABLE</span></span>|<span data-ttu-id="4e438-250">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-250">Int16</span></span>|
|<span data-ttu-id="4e438-251">AÇıKLAMALARıNıN</span><span class="sxs-lookup"><span data-stu-id="4e438-251">REMARKS</span></span>|<span data-ttu-id="4e438-252">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-252">String</span></span>|
|<span data-ttu-id="4e438-253">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="4e438-253">COLUMN_DEF</span></span>|<span data-ttu-id="4e438-254">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-254">String</span></span>|
|<span data-ttu-id="4e438-255">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4e438-255">SQL_DATA_TYPE</span></span>|<span data-ttu-id="4e438-256">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-256">Int16</span></span>|
|<span data-ttu-id="4e438-257">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="4e438-257">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="4e438-258">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-258">Int16</span></span>|
|<span data-ttu-id="4e438-259">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="4e438-259">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="4e438-260">Int32</span><span class="sxs-lookup"><span data-stu-id="4e438-260">Int32</span></span>|
|<span data-ttu-id="4e438-261">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="4e438-261">ORDINAL_POSITION</span></span>|<span data-ttu-id="4e438-262">Int32</span><span class="sxs-lookup"><span data-stu-id="4e438-262">Int32</span></span>|
|<span data-ttu-id="4e438-263">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="4e438-263">IS_NULLABLE</span></span>|<span data-ttu-id="4e438-264">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-264">String</span></span>|
|<span data-ttu-id="4e438-265">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4e438-265">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="4e438-266">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-266">String</span></span>|
|<span data-ttu-id="4e438-267">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4e438-267">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="4e438-268">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-268">String</span></span>|
|<span data-ttu-id="4e438-269">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4e438-269">SS_DATA_TYPE</span></span>|<span data-ttu-id="4e438-270">Bayt</span><span class="sxs-lookup"><span data-stu-id="4e438-270">Byte</span></span>|

### <a name="procedureparameters"></a><span data-ttu-id="4e438-271">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="4e438-271">ProcedureParameters</span></span>

|<span data-ttu-id="4e438-272">ColumnName</span><span class="sxs-lookup"><span data-stu-id="4e438-272">ColumnName</span></span>|<span data-ttu-id="4e438-273">DataType</span><span class="sxs-lookup"><span data-stu-id="4e438-273">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="4e438-274">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="4e438-274">PROCEDURE_CAT</span></span>|<span data-ttu-id="4e438-275">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-275">String</span></span>|
|<span data-ttu-id="4e438-276">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="4e438-276">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="4e438-277">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-277">String</span></span>|
|<span data-ttu-id="4e438-278">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="4e438-278">PROCEDURE_NAME</span></span>|<span data-ttu-id="4e438-279">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-279">String</span></span>|
|<span data-ttu-id="4e438-280">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="4e438-280">COLUMN_NAME</span></span>|<span data-ttu-id="4e438-281">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-281">String</span></span>|
|<span data-ttu-id="4e438-282">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="4e438-282">COLUMN_TYPE</span></span>|<span data-ttu-id="4e438-283">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-283">Int16</span></span>|
|<span data-ttu-id="4e438-284">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4e438-284">DATA_TYPE</span></span>|<span data-ttu-id="4e438-285">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-285">Int16</span></span>|
|<span data-ttu-id="4e438-286">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="4e438-286">TYPE_NAME</span></span>|<span data-ttu-id="4e438-287">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-287">String</span></span>|
|<span data-ttu-id="4e438-288">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="4e438-288">COLUMN_SIZE</span></span>|<span data-ttu-id="4e438-289">Int32</span><span class="sxs-lookup"><span data-stu-id="4e438-289">Int32</span></span>|
|<span data-ttu-id="4e438-290">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="4e438-290">BUFFER_LENGTH</span></span>|<span data-ttu-id="4e438-291">Int32</span><span class="sxs-lookup"><span data-stu-id="4e438-291">Int32</span></span>|
|<span data-ttu-id="4e438-292">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="4e438-292">DECIMAL_DIGITS</span></span>|<span data-ttu-id="4e438-293">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-293">Int16</span></span>|
|<span data-ttu-id="4e438-294">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="4e438-294">NUM_PREC_RADIX</span></span>|<span data-ttu-id="4e438-295">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-295">Int16</span></span>|
|<span data-ttu-id="4e438-296">YAPıLAMAZ</span><span class="sxs-lookup"><span data-stu-id="4e438-296">NULLABLE</span></span>|<span data-ttu-id="4e438-297">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-297">Int16</span></span>|
|<span data-ttu-id="4e438-298">AÇıKLAMALARıNıN</span><span class="sxs-lookup"><span data-stu-id="4e438-298">REMARKS</span></span>|<span data-ttu-id="4e438-299">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-299">String</span></span>|
|<span data-ttu-id="4e438-300">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="4e438-300">COLUMN_DEF</span></span>|<span data-ttu-id="4e438-301">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-301">String</span></span>|
|<span data-ttu-id="4e438-302">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4e438-302">SQL_DATA_TYPE</span></span>|<span data-ttu-id="4e438-303">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-303">Int16</span></span>|
|<span data-ttu-id="4e438-304">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="4e438-304">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="4e438-305">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-305">Int16</span></span>|
|<span data-ttu-id="4e438-306">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="4e438-306">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="4e438-307">Int32</span><span class="sxs-lookup"><span data-stu-id="4e438-307">Int32</span></span>|
|<span data-ttu-id="4e438-308">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="4e438-308">ORDINAL_POSITION</span></span>|<span data-ttu-id="4e438-309">Int32</span><span class="sxs-lookup"><span data-stu-id="4e438-309">Int32</span></span>|
|<span data-ttu-id="4e438-310">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="4e438-310">IS_NULLABLE</span></span>|<span data-ttu-id="4e438-311">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-311">String</span></span>|
|<span data-ttu-id="4e438-312">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4e438-312">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="4e438-313">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-313">String</span></span>|
|<span data-ttu-id="4e438-314">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4e438-314">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="4e438-315">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-315">String</span></span>|
|<span data-ttu-id="4e438-316">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4e438-316">SS_DATA_TYPE</span></span>|<span data-ttu-id="4e438-317">Bayt</span><span class="sxs-lookup"><span data-stu-id="4e438-317">Byte</span></span>|

## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="4e438-318">Microsoft Oracle ODBC sürücüsü</span><span class="sxs-lookup"><span data-stu-id="4e438-318">Microsoft Oracle ODBC Driver</span></span>

<span data-ttu-id="4e438-319">Microsoft SQL Server Oracle ODBC sürücüsü, ortak şema koleksiyonlarına ek olarak aşağıdaki belirli şema koleksiyonlarını destekler:</span><span class="sxs-lookup"><span data-stu-id="4e438-319">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="4e438-320">Tablolar</span><span class="sxs-lookup"><span data-stu-id="4e438-320">Tables</span></span>

- <span data-ttu-id="4e438-321">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="4e438-321">Columns</span></span>

- <span data-ttu-id="4e438-322">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="4e438-322">Procedures</span></span>

- <span data-ttu-id="4e438-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="4e438-323">ProcedureColumns</span></span>

- <span data-ttu-id="4e438-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="4e438-324">ProcedureParameters</span></span>

- <span data-ttu-id="4e438-325">Görünümler</span><span class="sxs-lookup"><span data-stu-id="4e438-325">Views</span></span>

- <span data-ttu-id="4e438-326">Dizinler</span><span class="sxs-lookup"><span data-stu-id="4e438-326">Indexes</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="4e438-327">Tablolar ve görünümler</span><span class="sxs-lookup"><span data-stu-id="4e438-327">Tables and Views</span></span>

|<span data-ttu-id="4e438-328">ColumnName</span><span class="sxs-lookup"><span data-stu-id="4e438-328">ColumnName</span></span>|<span data-ttu-id="4e438-329">DataType</span><span class="sxs-lookup"><span data-stu-id="4e438-329">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="4e438-330">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="4e438-330">TABLE_QUALIFIER</span></span>|<span data-ttu-id="4e438-331">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-331">String</span></span>|
|<span data-ttu-id="4e438-332">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="4e438-332">TABLE_OWNER</span></span>|<span data-ttu-id="4e438-333">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-333">String</span></span>|
|<span data-ttu-id="4e438-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="4e438-334">TABLE_NAME</span></span>|<span data-ttu-id="4e438-335">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-335">String</span></span>|
|<span data-ttu-id="4e438-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="4e438-336">TABLE_TYPE</span></span>|<span data-ttu-id="4e438-337">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-337">String</span></span>|
|<span data-ttu-id="4e438-338">AÇıKLAMALARıNıN</span><span class="sxs-lookup"><span data-stu-id="4e438-338">REMARKS</span></span>|<span data-ttu-id="4e438-339">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-339">String</span></span>|

### <a name="columns"></a><span data-ttu-id="4e438-340">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="4e438-340">Columns</span></span>

|<span data-ttu-id="4e438-341">ColumnName</span><span class="sxs-lookup"><span data-stu-id="4e438-341">ColumnName</span></span>|<span data-ttu-id="4e438-342">DataType</span><span class="sxs-lookup"><span data-stu-id="4e438-342">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="4e438-343">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="4e438-343">TABLE_QUALIFIER</span></span>|<span data-ttu-id="4e438-344">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-344">String</span></span>|
|<span data-ttu-id="4e438-345">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="4e438-345">TABLE_OWNER</span></span>|<span data-ttu-id="4e438-346">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-346">String</span></span>|
|<span data-ttu-id="4e438-347">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="4e438-347">TABLE_NAME</span></span>|<span data-ttu-id="4e438-348">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-348">String</span></span>|
|<span data-ttu-id="4e438-349">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="4e438-349">COLUMN_NAME</span></span>|<span data-ttu-id="4e438-350">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-350">String</span></span>|
|<span data-ttu-id="4e438-351">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4e438-351">DATA_TYPE</span></span>|<span data-ttu-id="4e438-352">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-352">Int16</span></span>|
|<span data-ttu-id="4e438-353">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="4e438-353">TYPE_NAME</span></span>|<span data-ttu-id="4e438-354">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-354">String</span></span>|
|<span data-ttu-id="4e438-355">DUYARLıLıK</span><span class="sxs-lookup"><span data-stu-id="4e438-355">PRECISION</span></span>|<span data-ttu-id="4e438-356">Int32</span><span class="sxs-lookup"><span data-stu-id="4e438-356">Int32</span></span>|
|<span data-ttu-id="4e438-357">LENGTH</span><span class="sxs-lookup"><span data-stu-id="4e438-357">LENGTH</span></span>|<span data-ttu-id="4e438-358">Int32</span><span class="sxs-lookup"><span data-stu-id="4e438-358">Int32</span></span>|
|<span data-ttu-id="4e438-359">ÖLÇEK</span><span class="sxs-lookup"><span data-stu-id="4e438-359">SCALE</span></span>|<span data-ttu-id="4e438-360">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-360">Int16</span></span>|
|<span data-ttu-id="4e438-361">TABAN</span><span class="sxs-lookup"><span data-stu-id="4e438-361">RADIX</span></span>|<span data-ttu-id="4e438-362">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-362">Int16</span></span>|
|<span data-ttu-id="4e438-363">YAPıLAMAZ</span><span class="sxs-lookup"><span data-stu-id="4e438-363">NULLABLE</span></span>|<span data-ttu-id="4e438-364">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-364">Int16</span></span>|
|<span data-ttu-id="4e438-365">AÇıKLAMALARıNıN</span><span class="sxs-lookup"><span data-stu-id="4e438-365">REMARKS</span></span>|<span data-ttu-id="4e438-366">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-366">String</span></span>|
|<span data-ttu-id="4e438-367">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="4e438-367">ORDINAL_POSITION</span></span>|<span data-ttu-id="4e438-368">Int32</span><span class="sxs-lookup"><span data-stu-id="4e438-368">Int32</span></span>|

### <a name="procedures"></a><span data-ttu-id="4e438-369">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="4e438-369">Procedures</span></span>

|<span data-ttu-id="4e438-370">ColumnName</span><span class="sxs-lookup"><span data-stu-id="4e438-370">ColumnName</span></span>|<span data-ttu-id="4e438-371">DataType</span><span class="sxs-lookup"><span data-stu-id="4e438-371">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="4e438-372">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="4e438-372">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="4e438-373">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-373">String</span></span>|
|<span data-ttu-id="4e438-374">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="4e438-374">PROCEDURE_OWNER</span></span>|<span data-ttu-id="4e438-375">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-375">String</span></span>|
|<span data-ttu-id="4e438-376">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="4e438-376">PROCEDURE_NAME</span></span>|<span data-ttu-id="4e438-377">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-377">String</span></span>|
|<span data-ttu-id="4e438-378">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="4e438-378">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="4e438-379">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-379">Int16</span></span>|
|<span data-ttu-id="4e438-380">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="4e438-380">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="4e438-381">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-381">Int16</span></span>|
|<span data-ttu-id="4e438-382">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="4e438-382">NUM_RESULT_SETS</span></span>|<span data-ttu-id="4e438-383">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-383">Int16</span></span>|
|<span data-ttu-id="4e438-384">AÇıKLAMALARıNıN</span><span class="sxs-lookup"><span data-stu-id="4e438-384">REMARKS</span></span>|<span data-ttu-id="4e438-385">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-385">String</span></span>|
|<span data-ttu-id="4e438-386">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="4e438-386">PROCEDURE_TYPE</span></span>|<span data-ttu-id="4e438-387">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-387">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="4e438-388">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="4e438-388">ProcedureColumns</span></span>

|<span data-ttu-id="4e438-389">ColumnName</span><span class="sxs-lookup"><span data-stu-id="4e438-389">ColumnName</span></span>|<span data-ttu-id="4e438-390">DataType</span><span class="sxs-lookup"><span data-stu-id="4e438-390">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="4e438-391">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="4e438-391">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="4e438-392">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-392">String</span></span>|
|<span data-ttu-id="4e438-393">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="4e438-393">PROCEDURE_OWNER</span></span>|<span data-ttu-id="4e438-394">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-394">String</span></span>|
|<span data-ttu-id="4e438-395">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="4e438-395">PROCEDURE_NAME</span></span>|<span data-ttu-id="4e438-396">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-396">String</span></span>|
|<span data-ttu-id="4e438-397">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="4e438-397">COLUMN_NAME</span></span>|<span data-ttu-id="4e438-398">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-398">String</span></span>|
|<span data-ttu-id="4e438-399">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="4e438-399">COLUMN_TYPE</span></span>|<span data-ttu-id="4e438-400">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-400">Int16</span></span>|
|<span data-ttu-id="4e438-401">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4e438-401">DATA_TYPE</span></span>|<span data-ttu-id="4e438-402">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-402">Int16</span></span>|
|<span data-ttu-id="4e438-403">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="4e438-403">TYPE_NAME</span></span>|<span data-ttu-id="4e438-404">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-404">String</span></span>|
|<span data-ttu-id="4e438-405">DUYARLıLıK</span><span class="sxs-lookup"><span data-stu-id="4e438-405">PRECISION</span></span>|<span data-ttu-id="4e438-406">Int32</span><span class="sxs-lookup"><span data-stu-id="4e438-406">Int32</span></span>|
|<span data-ttu-id="4e438-407">LENGTH</span><span class="sxs-lookup"><span data-stu-id="4e438-407">LENGTH</span></span>|<span data-ttu-id="4e438-408">Int32</span><span class="sxs-lookup"><span data-stu-id="4e438-408">Int32</span></span>|
|<span data-ttu-id="4e438-409">ÖLÇEK</span><span class="sxs-lookup"><span data-stu-id="4e438-409">SCALE</span></span>|<span data-ttu-id="4e438-410">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-410">Int16</span></span>|
|<span data-ttu-id="4e438-411">TABAN</span><span class="sxs-lookup"><span data-stu-id="4e438-411">RADIX</span></span>|<span data-ttu-id="4e438-412">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-412">Int16</span></span>|
|<span data-ttu-id="4e438-413">YAPıLAMAZ</span><span class="sxs-lookup"><span data-stu-id="4e438-413">NULLABLE</span></span>|<span data-ttu-id="4e438-414">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-414">Int16</span></span>|
|<span data-ttu-id="4e438-415">AÇıKLAMALARıNıN</span><span class="sxs-lookup"><span data-stu-id="4e438-415">REMARKS</span></span>|<span data-ttu-id="4e438-416">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-416">String</span></span>|
|<span data-ttu-id="4e438-417">YÜKLEMEK</span><span class="sxs-lookup"><span data-stu-id="4e438-417">OVERLOAD</span></span>|<span data-ttu-id="4e438-418">Int32</span><span class="sxs-lookup"><span data-stu-id="4e438-418">Int32</span></span>|
|<span data-ttu-id="4e438-419">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="4e438-419">ORDINAL_POSITION</span></span>|<span data-ttu-id="4e438-420">Int32</span><span class="sxs-lookup"><span data-stu-id="4e438-420">Int32</span></span>|

## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="4e438-421">Microsoft Jet ODBC sürücüsü</span><span class="sxs-lookup"><span data-stu-id="4e438-421">Microsoft Jet ODBC Driver</span></span>

<span data-ttu-id="4e438-422">Microsoft Jet ODBC sürücüsü, ortak şema koleksiyonlarına ek olarak aşağıdaki belirli şema koleksiyonlarını destekler:</span><span class="sxs-lookup"><span data-stu-id="4e438-422">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="4e438-423">Tablolar</span><span class="sxs-lookup"><span data-stu-id="4e438-423">Tables</span></span>

- <span data-ttu-id="4e438-424">Dizinler</span><span class="sxs-lookup"><span data-stu-id="4e438-424">Indexes</span></span>

- <span data-ttu-id="4e438-425">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="4e438-425">Columns</span></span>

- <span data-ttu-id="4e438-426">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="4e438-426">Procedures</span></span>

- <span data-ttu-id="4e438-427">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="4e438-427">ProcedureColumns</span></span>

- <span data-ttu-id="4e438-428">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="4e438-428">ProcedureParameters</span></span>

- <span data-ttu-id="4e438-429">Görünümler</span><span class="sxs-lookup"><span data-stu-id="4e438-429">Views</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="4e438-430">Tablolar ve görünümler</span><span class="sxs-lookup"><span data-stu-id="4e438-430">Tables and Views</span></span>

|<span data-ttu-id="4e438-431">ColumnName</span><span class="sxs-lookup"><span data-stu-id="4e438-431">ColumnName</span></span>|<span data-ttu-id="4e438-432">DataType</span><span class="sxs-lookup"><span data-stu-id="4e438-432">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="4e438-433">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="4e438-433">TABLE_QUALIFIER</span></span>|<span data-ttu-id="4e438-434">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-434">String</span></span>|
|<span data-ttu-id="4e438-435">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="4e438-435">TABLE_OWNER</span></span>|<span data-ttu-id="4e438-436">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-436">String</span></span>|
|<span data-ttu-id="4e438-437">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="4e438-437">TABLE_NAME</span></span>|<span data-ttu-id="4e438-438">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-438">String</span></span>|
|<span data-ttu-id="4e438-439">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="4e438-439">TABLE_TYPE</span></span>|<span data-ttu-id="4e438-440">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-440">String</span></span>|
|<span data-ttu-id="4e438-441">AÇıKLAMALARıNıN</span><span class="sxs-lookup"><span data-stu-id="4e438-441">REMARKS</span></span>|<span data-ttu-id="4e438-442">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-442">String</span></span>|

### <a name="columns"></a><span data-ttu-id="4e438-443">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="4e438-443">Columns</span></span>

|<span data-ttu-id="4e438-444">ColumnName</span><span class="sxs-lookup"><span data-stu-id="4e438-444">ColumnName</span></span>|<span data-ttu-id="4e438-445">DataType</span><span class="sxs-lookup"><span data-stu-id="4e438-445">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="4e438-446">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="4e438-446">TABLE_QUALIFIER</span></span>|<span data-ttu-id="4e438-447">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-447">String</span></span>|
|<span data-ttu-id="4e438-448">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="4e438-448">TABLE_OWNER</span></span>|<span data-ttu-id="4e438-449">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-449">String</span></span>|
|<span data-ttu-id="4e438-450">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="4e438-450">TABLE_NAME</span></span>|<span data-ttu-id="4e438-451">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-451">String</span></span>|
|<span data-ttu-id="4e438-452">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="4e438-452">COLUMN_NAME</span></span>|<span data-ttu-id="4e438-453">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-453">String</span></span>|
|<span data-ttu-id="4e438-454">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4e438-454">DATA_TYPE</span></span>|<span data-ttu-id="4e438-455">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-455">Int16</span></span>|
|<span data-ttu-id="4e438-456">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="4e438-456">TYPE_NAME</span></span>|<span data-ttu-id="4e438-457">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-457">String</span></span>|
|<span data-ttu-id="4e438-458">DUYARLıLıK</span><span class="sxs-lookup"><span data-stu-id="4e438-458">PRECISION</span></span>|<span data-ttu-id="4e438-459">Int32</span><span class="sxs-lookup"><span data-stu-id="4e438-459">Int32</span></span>|
|<span data-ttu-id="4e438-460">LENGTH</span><span class="sxs-lookup"><span data-stu-id="4e438-460">LENGTH</span></span>|<span data-ttu-id="4e438-461">Int32</span><span class="sxs-lookup"><span data-stu-id="4e438-461">Int32</span></span>|
|<span data-ttu-id="4e438-462">ÖLÇEK</span><span class="sxs-lookup"><span data-stu-id="4e438-462">SCALE</span></span>|<span data-ttu-id="4e438-463">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-463">Int16</span></span>|
|<span data-ttu-id="4e438-464">TABAN</span><span class="sxs-lookup"><span data-stu-id="4e438-464">RADIX</span></span>|<span data-ttu-id="4e438-465">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-465">Int16</span></span>|
|<span data-ttu-id="4e438-466">YAPıLAMAZ</span><span class="sxs-lookup"><span data-stu-id="4e438-466">NULLABLE</span></span>|<span data-ttu-id="4e438-467">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-467">Int16</span></span>|
|<span data-ttu-id="4e438-468">AÇıKLAMALARıNıN</span><span class="sxs-lookup"><span data-stu-id="4e438-468">REMARKS</span></span>|<span data-ttu-id="4e438-469">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-469">String</span></span>|
|<span data-ttu-id="4e438-470">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="4e438-470">ORDINAL_POSITION</span></span>|<span data-ttu-id="4e438-471">Int32</span><span class="sxs-lookup"><span data-stu-id="4e438-471">Int32</span></span>|

### <a name="procedures"></a><span data-ttu-id="4e438-472">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="4e438-472">Procedures</span></span>

|<span data-ttu-id="4e438-473">ColumnName</span><span class="sxs-lookup"><span data-stu-id="4e438-473">ColumnName</span></span>|<span data-ttu-id="4e438-474">DataType</span><span class="sxs-lookup"><span data-stu-id="4e438-474">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="4e438-475">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="4e438-475">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="4e438-476">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-476">String</span></span>|
|<span data-ttu-id="4e438-477">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="4e438-477">PROCEDURE_OWNER</span></span>|<span data-ttu-id="4e438-478">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-478">String</span></span>|
|<span data-ttu-id="4e438-479">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="4e438-479">PROCEDURE_NAME</span></span>|<span data-ttu-id="4e438-480">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-480">String</span></span>|
|<span data-ttu-id="4e438-481">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="4e438-481">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="4e438-482">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-482">Int16</span></span>|
|<span data-ttu-id="4e438-483">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="4e438-483">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="4e438-484">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-484">Int16</span></span>|
|<span data-ttu-id="4e438-485">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="4e438-485">NUM_RESULT_SETS</span></span>|<span data-ttu-id="4e438-486">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-486">Int16</span></span>|
|<span data-ttu-id="4e438-487">AÇıKLAMALARıNıN</span><span class="sxs-lookup"><span data-stu-id="4e438-487">REMARKS</span></span>|<span data-ttu-id="4e438-488">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-488">String</span></span>|
|<span data-ttu-id="4e438-489">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="4e438-489">PROCEDURE_TYPE</span></span>|<span data-ttu-id="4e438-490">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-490">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="4e438-491">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="4e438-491">ProcedureColumns</span></span>

|<span data-ttu-id="4e438-492">ColumnName</span><span class="sxs-lookup"><span data-stu-id="4e438-492">ColumnName</span></span>|<span data-ttu-id="4e438-493">DataType</span><span class="sxs-lookup"><span data-stu-id="4e438-493">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="4e438-494">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="4e438-494">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="4e438-495">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-495">String</span></span>|
|<span data-ttu-id="4e438-496">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="4e438-496">PROCEDURE_OWNER</span></span>|<span data-ttu-id="4e438-497">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-497">String</span></span>|
|<span data-ttu-id="4e438-498">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="4e438-498">PROCEDURE_NAME</span></span>|<span data-ttu-id="4e438-499">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-499">String</span></span>|
|<span data-ttu-id="4e438-500">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="4e438-500">COLUMN_NAME</span></span>|<span data-ttu-id="4e438-501">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-501">String</span></span>|
|<span data-ttu-id="4e438-502">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="4e438-502">COLUMN_TYPE</span></span>|<span data-ttu-id="4e438-503">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-503">Int16</span></span>|
|<span data-ttu-id="4e438-504">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4e438-504">DATA_TYPE</span></span>|<span data-ttu-id="4e438-505">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-505">Int16</span></span>|
|<span data-ttu-id="4e438-506">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="4e438-506">TYPE_NAME</span></span>|<span data-ttu-id="4e438-507">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-507">String</span></span>|
|<span data-ttu-id="4e438-508">DUYARLıLıK</span><span class="sxs-lookup"><span data-stu-id="4e438-508">PRECISION</span></span>|<span data-ttu-id="4e438-509">Int32</span><span class="sxs-lookup"><span data-stu-id="4e438-509">Int32</span></span>|
|<span data-ttu-id="4e438-510">LENGTH</span><span class="sxs-lookup"><span data-stu-id="4e438-510">LENGTH</span></span>|<span data-ttu-id="4e438-511">Int32</span><span class="sxs-lookup"><span data-stu-id="4e438-511">Int32</span></span>|
|<span data-ttu-id="4e438-512">ÖLÇEK</span><span class="sxs-lookup"><span data-stu-id="4e438-512">SCALE</span></span>|<span data-ttu-id="4e438-513">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-513">Int16</span></span>|
|<span data-ttu-id="4e438-514">TABAN</span><span class="sxs-lookup"><span data-stu-id="4e438-514">RADIX</span></span>|<span data-ttu-id="4e438-515">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-515">Int16</span></span>|
|<span data-ttu-id="4e438-516">YAPıLAMAZ</span><span class="sxs-lookup"><span data-stu-id="4e438-516">NULLABLE</span></span>|<span data-ttu-id="4e438-517">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-517">Int16</span></span>|
|<span data-ttu-id="4e438-518">AÇıKLAMALARıNıN</span><span class="sxs-lookup"><span data-stu-id="4e438-518">REMARKS</span></span>|<span data-ttu-id="4e438-519">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-519">String</span></span>|
|<span data-ttu-id="4e438-520">YÜKLEMEK</span><span class="sxs-lookup"><span data-stu-id="4e438-520">OVERLOAD</span></span>|<span data-ttu-id="4e438-521">Int32</span><span class="sxs-lookup"><span data-stu-id="4e438-521">Int32</span></span>|
|<span data-ttu-id="4e438-522">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="4e438-522">ORDINAL_POSITION</span></span>|<span data-ttu-id="4e438-523">Int32</span><span class="sxs-lookup"><span data-stu-id="4e438-523">Int32</span></span>|

### <a name="procedureparameters"></a><span data-ttu-id="4e438-524">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="4e438-524">ProcedureParameters</span></span>

|<span data-ttu-id="4e438-525">ColumnName</span><span class="sxs-lookup"><span data-stu-id="4e438-525">ColumnName</span></span>|<span data-ttu-id="4e438-526">DataType</span><span class="sxs-lookup"><span data-stu-id="4e438-526">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="4e438-527">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="4e438-527">PROCEDURE_CAT</span></span>|<span data-ttu-id="4e438-528">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-528">String</span></span>|
|<span data-ttu-id="4e438-529">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="4e438-529">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="4e438-530">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-530">String</span></span>|
|<span data-ttu-id="4e438-531">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="4e438-531">PROCEDURE_NAME</span></span>|<span data-ttu-id="4e438-532">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-532">String</span></span>|
|<span data-ttu-id="4e438-533">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="4e438-533">COLUMN_NAME</span></span>|<span data-ttu-id="4e438-534">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-534">String</span></span>|
|<span data-ttu-id="4e438-535">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="4e438-535">COLUMN_TYPE</span></span>|<span data-ttu-id="4e438-536">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-536">Int16</span></span>|
|<span data-ttu-id="4e438-537">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4e438-537">DATA_TYPE</span></span>|<span data-ttu-id="4e438-538">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-538">Int16</span></span>|
|<span data-ttu-id="4e438-539">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="4e438-539">TYPE_NAME</span></span>|<span data-ttu-id="4e438-540">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-540">String</span></span>|
|<span data-ttu-id="4e438-541">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="4e438-541">COLUMN_SIZE</span></span>|<span data-ttu-id="4e438-542">Int32</span><span class="sxs-lookup"><span data-stu-id="4e438-542">Int32</span></span>|
|<span data-ttu-id="4e438-543">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="4e438-543">BUFFER_LENGTH</span></span>|<span data-ttu-id="4e438-544">Int32</span><span class="sxs-lookup"><span data-stu-id="4e438-544">Int32</span></span>|
|<span data-ttu-id="4e438-545">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="4e438-545">DECIMAL_DIGITS</span></span>|<span data-ttu-id="4e438-546">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-546">Int16</span></span>|
|<span data-ttu-id="4e438-547">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="4e438-547">NUM_PREC_RADIX</span></span>|<span data-ttu-id="4e438-548">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-548">Int16</span></span>|
|<span data-ttu-id="4e438-549">YAPıLAMAZ</span><span class="sxs-lookup"><span data-stu-id="4e438-549">NULLABLE</span></span>|<span data-ttu-id="4e438-550">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-550">Int16</span></span>|
|<span data-ttu-id="4e438-551">AÇıKLAMALARıNıN</span><span class="sxs-lookup"><span data-stu-id="4e438-551">REMARKS</span></span>|<span data-ttu-id="4e438-552">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-552">String</span></span>|
|<span data-ttu-id="4e438-553">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="4e438-553">COLUMN_DEF</span></span>|<span data-ttu-id="4e438-554">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-554">String</span></span>|
|<span data-ttu-id="4e438-555">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4e438-555">SQL_DATA_TYPE</span></span>|<span data-ttu-id="4e438-556">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-556">Int16</span></span>|
|<span data-ttu-id="4e438-557">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="4e438-557">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="4e438-558">Int16</span><span class="sxs-lookup"><span data-stu-id="4e438-558">Int16</span></span>|
|<span data-ttu-id="4e438-559">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="4e438-559">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="4e438-560">Int32</span><span class="sxs-lookup"><span data-stu-id="4e438-560">Int32</span></span>|
|<span data-ttu-id="4e438-561">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="4e438-561">ORDINAL_POSITION</span></span>|<span data-ttu-id="4e438-562">Int32</span><span class="sxs-lookup"><span data-stu-id="4e438-562">Int32</span></span>|
|<span data-ttu-id="4e438-563">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="4e438-563">IS_NULLABLE</span></span>|<span data-ttu-id="4e438-564">Dize</span><span class="sxs-lookup"><span data-stu-id="4e438-564">String</span></span>|

## <a name="see-also"></a><span data-ttu-id="4e438-565">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e438-565">See also</span></span>

- [<span data-ttu-id="4e438-566">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4e438-566">ADO.NET Overview</span></span>](ado-net-overview.md)
