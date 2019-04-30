---
title: ODBC Şema Koleksiyonları
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: ffe80120ceffbe29c0a117cf1194860c5782be8c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772053"
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="523b1-102">ODBC Şema Koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="523b1-102">ODBC Schema Collections</span></span>

<span data-ttu-id="523b1-103">Bu bölümde, Microsoft SQL Server, Oracle ve Microsoft Jet ODBC sürücüleri için şema koleksiyonu desteği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="523b1-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>

## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="523b1-104">Microsoft SQL Server ODBC sürücüsü</span><span class="sxs-lookup"><span data-stu-id="523b1-104">Microsoft SQL Server ODBC Driver</span></span>

<span data-ttu-id="523b1-105">Microsoft SQL Server ODBC sürücüsü, ortak şema koleksiyonları ek olarak aşağıdaki belirli şema koleksiyonları destekler:</span><span class="sxs-lookup"><span data-stu-id="523b1-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="523b1-106">Tabloları</span><span class="sxs-lookup"><span data-stu-id="523b1-106">Tables</span></span>

- <span data-ttu-id="523b1-107">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="523b1-107">Indexes</span></span>

- <span data-ttu-id="523b1-108">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="523b1-108">Columns</span></span>

- <span data-ttu-id="523b1-109">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="523b1-109">Procedures</span></span>

- <span data-ttu-id="523b1-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="523b1-110">ProcedureColumns</span></span>

- <span data-ttu-id="523b1-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="523b1-111">ProcedureParameters</span></span>

- <span data-ttu-id="523b1-112">Görünümler</span><span class="sxs-lookup"><span data-stu-id="523b1-112">Views</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="523b1-113">Tabloları ve görünümleri</span><span class="sxs-lookup"><span data-stu-id="523b1-113">Tables and Views</span></span>

|<span data-ttu-id="523b1-114">ColumnName</span><span class="sxs-lookup"><span data-stu-id="523b1-114">ColumnName</span></span>|<span data-ttu-id="523b1-115">DataType</span><span class="sxs-lookup"><span data-stu-id="523b1-115">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="523b1-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="523b1-116">TABLE_CAT</span></span>|<span data-ttu-id="523b1-117">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-117">String</span></span>|
|<span data-ttu-id="523b1-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="523b1-118">TABLE_SCHEM</span></span>|<span data-ttu-id="523b1-119">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-119">String</span></span>|
|<span data-ttu-id="523b1-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="523b1-120">TABLE_NAME</span></span>|<span data-ttu-id="523b1-121">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-121">String</span></span>|
|<span data-ttu-id="523b1-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="523b1-122">TABLE_TYPE</span></span>|<span data-ttu-id="523b1-123">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-123">String</span></span>|
|<span data-ttu-id="523b1-124">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="523b1-124">REMARKS</span></span>|<span data-ttu-id="523b1-125">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-125">String</span></span>|

### <a name="indexes"></a><span data-ttu-id="523b1-126">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="523b1-126">Indexes</span></span>

|<span data-ttu-id="523b1-127">ColumnName</span><span class="sxs-lookup"><span data-stu-id="523b1-127">ColumnName</span></span>|<span data-ttu-id="523b1-128">DataType</span><span class="sxs-lookup"><span data-stu-id="523b1-128">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="523b1-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="523b1-129">TABLE_CAT</span></span>|<span data-ttu-id="523b1-130">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-130">String</span></span>|
|<span data-ttu-id="523b1-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="523b1-131">TABLE_SCHEM</span></span>|<span data-ttu-id="523b1-132">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-132">String</span></span>|
|<span data-ttu-id="523b1-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="523b1-133">TABLE_NAME</span></span>|<span data-ttu-id="523b1-134">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-134">String</span></span>|
|<span data-ttu-id="523b1-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="523b1-135">NON_UNIQUE</span></span>|<span data-ttu-id="523b1-136">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-136">Int16</span></span>|
|<span data-ttu-id="523b1-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="523b1-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="523b1-138">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-138">String</span></span>|
|<span data-ttu-id="523b1-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="523b1-139">INDEX_NAME</span></span>|<span data-ttu-id="523b1-140">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-140">String</span></span>|
|<span data-ttu-id="523b1-141">TÜRÜ</span><span class="sxs-lookup"><span data-stu-id="523b1-141">TYPE</span></span>|<span data-ttu-id="523b1-142">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-142">Int16</span></span>|
|<span data-ttu-id="523b1-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="523b1-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="523b1-144">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-144">Int16</span></span>|
|<span data-ttu-id="523b1-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="523b1-145">COLUMN_NAME</span></span>|<span data-ttu-id="523b1-146">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-146">String</span></span>|
|<span data-ttu-id="523b1-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="523b1-147">ASC_OR_DESC</span></span>|<span data-ttu-id="523b1-148">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-148">String</span></span>|
|<span data-ttu-id="523b1-149">ÖNEM DÜZEYİ</span><span class="sxs-lookup"><span data-stu-id="523b1-149">CARDINALITY</span></span>|<span data-ttu-id="523b1-150">Int32</span><span class="sxs-lookup"><span data-stu-id="523b1-150">Int32</span></span>|
|<span data-ttu-id="523b1-151">SAYFALARI</span><span class="sxs-lookup"><span data-stu-id="523b1-151">PAGES</span></span>|<span data-ttu-id="523b1-152">Int32</span><span class="sxs-lookup"><span data-stu-id="523b1-152">Int32</span></span>|
|<span data-ttu-id="523b1-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="523b1-153">FILTER_CONDITION</span></span>|<span data-ttu-id="523b1-154">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-154">String</span></span>|
|<span data-ttu-id="523b1-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="523b1-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="523b1-156">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-156">String</span></span>|
|<span data-ttu-id="523b1-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="523b1-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="523b1-158">Bayt</span><span class="sxs-lookup"><span data-stu-id="523b1-158">Byte</span></span>|

### <a name="columns"></a><span data-ttu-id="523b1-159">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="523b1-159">Columns</span></span>

|<span data-ttu-id="523b1-160">ColumnName</span><span class="sxs-lookup"><span data-stu-id="523b1-160">ColumnName</span></span>|<span data-ttu-id="523b1-161">DataType</span><span class="sxs-lookup"><span data-stu-id="523b1-161">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="523b1-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="523b1-162">TABLE_CAT</span></span>|<span data-ttu-id="523b1-163">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-163">String</span></span>|
|<span data-ttu-id="523b1-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="523b1-164">TABLE_SCHEM</span></span>|<span data-ttu-id="523b1-165">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-165">String</span></span>|
|<span data-ttu-id="523b1-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="523b1-166">TABLE_NAME</span></span>|<span data-ttu-id="523b1-167">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-167">String</span></span>|
|<span data-ttu-id="523b1-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="523b1-168">COLUMN_NAME</span></span>|<span data-ttu-id="523b1-169">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-169">String</span></span>|
|<span data-ttu-id="523b1-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="523b1-170">DATA_TYPE</span></span>|<span data-ttu-id="523b1-171">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-171">Int16</span></span>|
|<span data-ttu-id="523b1-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="523b1-172">TYPE_NAME</span></span>|<span data-ttu-id="523b1-173">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-173">String</span></span>|
|<span data-ttu-id="523b1-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="523b1-174">COLUMN_SIZE</span></span>|<span data-ttu-id="523b1-175">Int32</span><span class="sxs-lookup"><span data-stu-id="523b1-175">Int32</span></span>|
|<span data-ttu-id="523b1-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="523b1-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="523b1-177">Int32</span><span class="sxs-lookup"><span data-stu-id="523b1-177">Int32</span></span>|
|<span data-ttu-id="523b1-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="523b1-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="523b1-179">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-179">Int16</span></span>|
|<span data-ttu-id="523b1-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="523b1-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="523b1-181">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-181">Int16</span></span>|
|<span data-ttu-id="523b1-182">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="523b1-182">NULLABLE</span></span>|<span data-ttu-id="523b1-183">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-183">Int16</span></span>|
|<span data-ttu-id="523b1-184">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="523b1-184">REMARKS</span></span>|<span data-ttu-id="523b1-185">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-185">String</span></span>|
|<span data-ttu-id="523b1-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="523b1-186">COLUMN_DEF</span></span>|<span data-ttu-id="523b1-187">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-187">String</span></span>|
|<span data-ttu-id="523b1-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="523b1-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="523b1-189">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-189">Int16</span></span>|
|<span data-ttu-id="523b1-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="523b1-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="523b1-191">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-191">Int16</span></span>|
|<span data-ttu-id="523b1-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="523b1-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="523b1-193">Int32</span><span class="sxs-lookup"><span data-stu-id="523b1-193">Int32</span></span>|
|<span data-ttu-id="523b1-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="523b1-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="523b1-195">Int32</span><span class="sxs-lookup"><span data-stu-id="523b1-195">Int32</span></span>|
|<span data-ttu-id="523b1-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="523b1-196">IS_NULLABLE</span></span>|<span data-ttu-id="523b1-197">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-197">String</span></span>|
|<span data-ttu-id="523b1-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="523b1-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="523b1-199">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-199">String</span></span>|
|<span data-ttu-id="523b1-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="523b1-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="523b1-201">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-201">String</span></span>|
|<span data-ttu-id="523b1-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="523b1-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="523b1-203">Bayt</span><span class="sxs-lookup"><span data-stu-id="523b1-203">Byte</span></span>|

### <a name="procedures"></a><span data-ttu-id="523b1-204">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="523b1-204">Procedures</span></span>

|<span data-ttu-id="523b1-205">ColumnName</span><span class="sxs-lookup"><span data-stu-id="523b1-205">ColumnName</span></span>|<span data-ttu-id="523b1-206">DataType</span><span class="sxs-lookup"><span data-stu-id="523b1-206">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="523b1-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="523b1-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="523b1-208">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-208">String</span></span>|
|<span data-ttu-id="523b1-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="523b1-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="523b1-210">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-210">String</span></span>|
|<span data-ttu-id="523b1-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="523b1-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="523b1-212">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-212">String</span></span>|
|<span data-ttu-id="523b1-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="523b1-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="523b1-214">Int32</span><span class="sxs-lookup"><span data-stu-id="523b1-214">Int32</span></span>|
|<span data-ttu-id="523b1-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="523b1-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="523b1-216">Int32</span><span class="sxs-lookup"><span data-stu-id="523b1-216">Int32</span></span>|
|<span data-ttu-id="523b1-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="523b1-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="523b1-218">Int32</span><span class="sxs-lookup"><span data-stu-id="523b1-218">Int32</span></span>|
|<span data-ttu-id="523b1-219">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="523b1-219">REMARKS</span></span>|<span data-ttu-id="523b1-220">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-220">String</span></span>|
|<span data-ttu-id="523b1-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="523b1-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="523b1-222">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-222">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="523b1-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="523b1-223">ProcedureColumns</span></span>

|<span data-ttu-id="523b1-224">ColumnName</span><span class="sxs-lookup"><span data-stu-id="523b1-224">ColumnName</span></span>|<span data-ttu-id="523b1-225">DataType</span><span class="sxs-lookup"><span data-stu-id="523b1-225">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="523b1-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="523b1-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="523b1-227">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-227">String</span></span>|
|<span data-ttu-id="523b1-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="523b1-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="523b1-229">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-229">String</span></span>|
|<span data-ttu-id="523b1-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="523b1-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="523b1-231">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-231">String</span></span>|
|<span data-ttu-id="523b1-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="523b1-232">COLUMN_NAME</span></span>|<span data-ttu-id="523b1-233">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-233">String</span></span>|
|<span data-ttu-id="523b1-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="523b1-234">COLUMN_TYPE</span></span>|<span data-ttu-id="523b1-235">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-235">Int16</span></span>|
|<span data-ttu-id="523b1-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="523b1-236">DATA_TYPE</span></span>|<span data-ttu-id="523b1-237">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-237">Int16</span></span>|
|<span data-ttu-id="523b1-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="523b1-238">TYPE_NAME</span></span>|<span data-ttu-id="523b1-239">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-239">String</span></span>|
|<span data-ttu-id="523b1-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="523b1-240">COLUMN_SIZE</span></span>|<span data-ttu-id="523b1-241">Int32</span><span class="sxs-lookup"><span data-stu-id="523b1-241">Int32</span></span>|
|<span data-ttu-id="523b1-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="523b1-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="523b1-243">Int32</span><span class="sxs-lookup"><span data-stu-id="523b1-243">Int32</span></span>|
|<span data-ttu-id="523b1-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="523b1-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="523b1-245">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-245">Int16</span></span>|
|<span data-ttu-id="523b1-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="523b1-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="523b1-247">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-247">Int16</span></span>|
|<span data-ttu-id="523b1-248">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="523b1-248">NULLABLE</span></span>|<span data-ttu-id="523b1-249">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-249">Int16</span></span>|
|<span data-ttu-id="523b1-250">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="523b1-250">REMARKS</span></span>|<span data-ttu-id="523b1-251">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-251">String</span></span>|
|<span data-ttu-id="523b1-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="523b1-252">COLUMN_DEF</span></span>|<span data-ttu-id="523b1-253">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-253">String</span></span>|
|<span data-ttu-id="523b1-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="523b1-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="523b1-255">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-255">Int16</span></span>|
|<span data-ttu-id="523b1-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="523b1-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="523b1-257">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-257">Int16</span></span>|
|<span data-ttu-id="523b1-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="523b1-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="523b1-259">Int32</span><span class="sxs-lookup"><span data-stu-id="523b1-259">Int32</span></span>|
|<span data-ttu-id="523b1-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="523b1-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="523b1-261">Int32</span><span class="sxs-lookup"><span data-stu-id="523b1-261">Int32</span></span>|
|<span data-ttu-id="523b1-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="523b1-262">IS_NULLABLE</span></span>|<span data-ttu-id="523b1-263">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-263">String</span></span>|
|<span data-ttu-id="523b1-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="523b1-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="523b1-265">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-265">String</span></span>|
|<span data-ttu-id="523b1-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="523b1-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="523b1-267">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-267">String</span></span>|
|<span data-ttu-id="523b1-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="523b1-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="523b1-269">Bayt</span><span class="sxs-lookup"><span data-stu-id="523b1-269">Byte</span></span>|

### <a name="procedureparameters"></a><span data-ttu-id="523b1-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="523b1-270">ProcedureParameters</span></span>

|<span data-ttu-id="523b1-271">ColumnName</span><span class="sxs-lookup"><span data-stu-id="523b1-271">ColumnName</span></span>|<span data-ttu-id="523b1-272">DataType</span><span class="sxs-lookup"><span data-stu-id="523b1-272">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="523b1-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="523b1-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="523b1-274">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-274">String</span></span>|
|<span data-ttu-id="523b1-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="523b1-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="523b1-276">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-276">String</span></span>|
|<span data-ttu-id="523b1-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="523b1-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="523b1-278">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-278">String</span></span>|
|<span data-ttu-id="523b1-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="523b1-279">COLUMN_NAME</span></span>|<span data-ttu-id="523b1-280">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-280">String</span></span>|
|<span data-ttu-id="523b1-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="523b1-281">COLUMN_TYPE</span></span>|<span data-ttu-id="523b1-282">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-282">Int16</span></span>|
|<span data-ttu-id="523b1-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="523b1-283">DATA_TYPE</span></span>|<span data-ttu-id="523b1-284">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-284">Int16</span></span>|
|<span data-ttu-id="523b1-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="523b1-285">TYPE_NAME</span></span>|<span data-ttu-id="523b1-286">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-286">String</span></span>|
|<span data-ttu-id="523b1-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="523b1-287">COLUMN_SIZE</span></span>|<span data-ttu-id="523b1-288">Int32</span><span class="sxs-lookup"><span data-stu-id="523b1-288">Int32</span></span>|
|<span data-ttu-id="523b1-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="523b1-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="523b1-290">Int32</span><span class="sxs-lookup"><span data-stu-id="523b1-290">Int32</span></span>|
|<span data-ttu-id="523b1-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="523b1-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="523b1-292">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-292">Int16</span></span>|
|<span data-ttu-id="523b1-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="523b1-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="523b1-294">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-294">Int16</span></span>|
|<span data-ttu-id="523b1-295">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="523b1-295">NULLABLE</span></span>|<span data-ttu-id="523b1-296">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-296">Int16</span></span>|
|<span data-ttu-id="523b1-297">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="523b1-297">REMARKS</span></span>|<span data-ttu-id="523b1-298">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-298">String</span></span>|
|<span data-ttu-id="523b1-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="523b1-299">COLUMN_DEF</span></span>|<span data-ttu-id="523b1-300">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-300">String</span></span>|
|<span data-ttu-id="523b1-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="523b1-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="523b1-302">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-302">Int16</span></span>|
|<span data-ttu-id="523b1-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="523b1-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="523b1-304">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-304">Int16</span></span>|
|<span data-ttu-id="523b1-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="523b1-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="523b1-306">Int32</span><span class="sxs-lookup"><span data-stu-id="523b1-306">Int32</span></span>|
|<span data-ttu-id="523b1-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="523b1-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="523b1-308">Int32</span><span class="sxs-lookup"><span data-stu-id="523b1-308">Int32</span></span>|
|<span data-ttu-id="523b1-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="523b1-309">IS_NULLABLE</span></span>|<span data-ttu-id="523b1-310">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-310">String</span></span>|
|<span data-ttu-id="523b1-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="523b1-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="523b1-312">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-312">String</span></span>|
|<span data-ttu-id="523b1-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="523b1-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="523b1-314">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-314">String</span></span>|
|<span data-ttu-id="523b1-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="523b1-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="523b1-316">Bayt</span><span class="sxs-lookup"><span data-stu-id="523b1-316">Byte</span></span>|

## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="523b1-317">Microsoft Oracle ODBC sürücüsü</span><span class="sxs-lookup"><span data-stu-id="523b1-317">Microsoft Oracle ODBC Driver</span></span>

<span data-ttu-id="523b1-318">Microsoft SQL Server ve Oracle ODBC sürücüsü, ortak şema koleksiyonları ek olarak aşağıdaki belirli şema koleksiyonları destekler:</span><span class="sxs-lookup"><span data-stu-id="523b1-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="523b1-319">Tabloları</span><span class="sxs-lookup"><span data-stu-id="523b1-319">Tables</span></span>

- <span data-ttu-id="523b1-320">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="523b1-320">Columns</span></span>

- <span data-ttu-id="523b1-321">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="523b1-321">Procedures</span></span>

- <span data-ttu-id="523b1-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="523b1-322">ProcedureColumns</span></span>

- <span data-ttu-id="523b1-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="523b1-323">ProcedureParameters</span></span>

- <span data-ttu-id="523b1-324">Görünümler</span><span class="sxs-lookup"><span data-stu-id="523b1-324">Views</span></span>

- <span data-ttu-id="523b1-325">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="523b1-325">Indexes</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="523b1-326">Tabloları ve görünümleri</span><span class="sxs-lookup"><span data-stu-id="523b1-326">Tables and Views</span></span>

|<span data-ttu-id="523b1-327">ColumnName</span><span class="sxs-lookup"><span data-stu-id="523b1-327">ColumnName</span></span>|<span data-ttu-id="523b1-328">DataType</span><span class="sxs-lookup"><span data-stu-id="523b1-328">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="523b1-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="523b1-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="523b1-330">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-330">String</span></span>|
|<span data-ttu-id="523b1-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="523b1-331">TABLE_OWNER</span></span>|<span data-ttu-id="523b1-332">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-332">String</span></span>|
|<span data-ttu-id="523b1-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="523b1-333">TABLE_NAME</span></span>|<span data-ttu-id="523b1-334">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-334">String</span></span>|
|<span data-ttu-id="523b1-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="523b1-335">TABLE_TYPE</span></span>|<span data-ttu-id="523b1-336">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-336">String</span></span>|
|<span data-ttu-id="523b1-337">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="523b1-337">REMARKS</span></span>|<span data-ttu-id="523b1-338">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-338">String</span></span>|

### <a name="columns"></a><span data-ttu-id="523b1-339">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="523b1-339">Columns</span></span>

|<span data-ttu-id="523b1-340">ColumnName</span><span class="sxs-lookup"><span data-stu-id="523b1-340">ColumnName</span></span>|<span data-ttu-id="523b1-341">DataType</span><span class="sxs-lookup"><span data-stu-id="523b1-341">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="523b1-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="523b1-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="523b1-343">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-343">String</span></span>|
|<span data-ttu-id="523b1-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="523b1-344">TABLE_OWNER</span></span>|<span data-ttu-id="523b1-345">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-345">String</span></span>|
|<span data-ttu-id="523b1-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="523b1-346">TABLE_NAME</span></span>|<span data-ttu-id="523b1-347">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-347">String</span></span>|
|<span data-ttu-id="523b1-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="523b1-348">COLUMN_NAME</span></span>|<span data-ttu-id="523b1-349">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-349">String</span></span>|
|<span data-ttu-id="523b1-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="523b1-350">DATA_TYPE</span></span>|<span data-ttu-id="523b1-351">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-351">Int16</span></span>|
|<span data-ttu-id="523b1-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="523b1-352">TYPE_NAME</span></span>|<span data-ttu-id="523b1-353">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-353">String</span></span>|
|<span data-ttu-id="523b1-354">DUYARLIK</span><span class="sxs-lookup"><span data-stu-id="523b1-354">PRECISION</span></span>|<span data-ttu-id="523b1-355">Int32</span><span class="sxs-lookup"><span data-stu-id="523b1-355">Int32</span></span>|
|<span data-ttu-id="523b1-356">UZUNLUĞU</span><span class="sxs-lookup"><span data-stu-id="523b1-356">LENGTH</span></span>|<span data-ttu-id="523b1-357">Int32</span><span class="sxs-lookup"><span data-stu-id="523b1-357">Int32</span></span>|
|<span data-ttu-id="523b1-358">ÖLÇEK</span><span class="sxs-lookup"><span data-stu-id="523b1-358">SCALE</span></span>|<span data-ttu-id="523b1-359">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-359">Int16</span></span>|
|<span data-ttu-id="523b1-360">RADIX</span><span class="sxs-lookup"><span data-stu-id="523b1-360">RADIX</span></span>|<span data-ttu-id="523b1-361">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-361">Int16</span></span>|
|<span data-ttu-id="523b1-362">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="523b1-362">NULLABLE</span></span>|<span data-ttu-id="523b1-363">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-363">Int16</span></span>|
|<span data-ttu-id="523b1-364">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="523b1-364">REMARKS</span></span>|<span data-ttu-id="523b1-365">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-365">String</span></span>|
|<span data-ttu-id="523b1-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="523b1-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="523b1-367">Int32</span><span class="sxs-lookup"><span data-stu-id="523b1-367">Int32</span></span>|

### <a name="procedures"></a><span data-ttu-id="523b1-368">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="523b1-368">Procedures</span></span>

|<span data-ttu-id="523b1-369">ColumnName</span><span class="sxs-lookup"><span data-stu-id="523b1-369">ColumnName</span></span>|<span data-ttu-id="523b1-370">DataType</span><span class="sxs-lookup"><span data-stu-id="523b1-370">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="523b1-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="523b1-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="523b1-372">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-372">String</span></span>|
|<span data-ttu-id="523b1-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="523b1-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="523b1-374">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-374">String</span></span>|
|<span data-ttu-id="523b1-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="523b1-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="523b1-376">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-376">String</span></span>|
|<span data-ttu-id="523b1-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="523b1-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="523b1-378">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-378">Int16</span></span>|
|<span data-ttu-id="523b1-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="523b1-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="523b1-380">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-380">Int16</span></span>|
|<span data-ttu-id="523b1-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="523b1-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="523b1-382">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-382">Int16</span></span>|
|<span data-ttu-id="523b1-383">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="523b1-383">REMARKS</span></span>|<span data-ttu-id="523b1-384">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-384">String</span></span>|
|<span data-ttu-id="523b1-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="523b1-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="523b1-386">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-386">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="523b1-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="523b1-387">ProcedureColumns</span></span>

|<span data-ttu-id="523b1-388">ColumnName</span><span class="sxs-lookup"><span data-stu-id="523b1-388">ColumnName</span></span>|<span data-ttu-id="523b1-389">DataType</span><span class="sxs-lookup"><span data-stu-id="523b1-389">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="523b1-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="523b1-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="523b1-391">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-391">String</span></span>|
|<span data-ttu-id="523b1-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="523b1-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="523b1-393">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-393">String</span></span>|
|<span data-ttu-id="523b1-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="523b1-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="523b1-395">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-395">String</span></span>|
|<span data-ttu-id="523b1-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="523b1-396">COLUMN_NAME</span></span>|<span data-ttu-id="523b1-397">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-397">String</span></span>|
|<span data-ttu-id="523b1-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="523b1-398">COLUMN_TYPE</span></span>|<span data-ttu-id="523b1-399">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-399">Int16</span></span>|
|<span data-ttu-id="523b1-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="523b1-400">DATA_TYPE</span></span>|<span data-ttu-id="523b1-401">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-401">Int16</span></span>|
|<span data-ttu-id="523b1-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="523b1-402">TYPE_NAME</span></span>|<span data-ttu-id="523b1-403">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-403">String</span></span>|
|<span data-ttu-id="523b1-404">DUYARLIK</span><span class="sxs-lookup"><span data-stu-id="523b1-404">PRECISION</span></span>|<span data-ttu-id="523b1-405">Int32</span><span class="sxs-lookup"><span data-stu-id="523b1-405">Int32</span></span>|
|<span data-ttu-id="523b1-406">UZUNLUĞU</span><span class="sxs-lookup"><span data-stu-id="523b1-406">LENGTH</span></span>|<span data-ttu-id="523b1-407">Int32</span><span class="sxs-lookup"><span data-stu-id="523b1-407">Int32</span></span>|
|<span data-ttu-id="523b1-408">ÖLÇEK</span><span class="sxs-lookup"><span data-stu-id="523b1-408">SCALE</span></span>|<span data-ttu-id="523b1-409">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-409">Int16</span></span>|
|<span data-ttu-id="523b1-410">RADIX</span><span class="sxs-lookup"><span data-stu-id="523b1-410">RADIX</span></span>|<span data-ttu-id="523b1-411">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-411">Int16</span></span>|
|<span data-ttu-id="523b1-412">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="523b1-412">NULLABLE</span></span>|<span data-ttu-id="523b1-413">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-413">Int16</span></span>|
|<span data-ttu-id="523b1-414">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="523b1-414">REMARKS</span></span>|<span data-ttu-id="523b1-415">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-415">String</span></span>|
|<span data-ttu-id="523b1-416">AŞIRI YÜKLEME</span><span class="sxs-lookup"><span data-stu-id="523b1-416">OVERLOAD</span></span>|<span data-ttu-id="523b1-417">Int32</span><span class="sxs-lookup"><span data-stu-id="523b1-417">Int32</span></span>|
|<span data-ttu-id="523b1-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="523b1-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="523b1-419">Int32</span><span class="sxs-lookup"><span data-stu-id="523b1-419">Int32</span></span>|

## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="523b1-420">Microsoft Jet ODBC sürücüsü</span><span class="sxs-lookup"><span data-stu-id="523b1-420">Microsoft Jet ODBC Driver</span></span>

<span data-ttu-id="523b1-421">Microsoft Jet ODBC sürücüsü, ortak şema koleksiyonları ek olarak aşağıdaki belirli şema koleksiyonları destekler:</span><span class="sxs-lookup"><span data-stu-id="523b1-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="523b1-422">Tabloları</span><span class="sxs-lookup"><span data-stu-id="523b1-422">Tables</span></span>

- <span data-ttu-id="523b1-423">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="523b1-423">Indexes</span></span>

- <span data-ttu-id="523b1-424">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="523b1-424">Columns</span></span>

- <span data-ttu-id="523b1-425">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="523b1-425">Procedures</span></span>

- <span data-ttu-id="523b1-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="523b1-426">ProcedureColumns</span></span>

- <span data-ttu-id="523b1-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="523b1-427">ProcedureParameters</span></span>

- <span data-ttu-id="523b1-428">Görünümler</span><span class="sxs-lookup"><span data-stu-id="523b1-428">Views</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="523b1-429">Tabloları ve görünümleri</span><span class="sxs-lookup"><span data-stu-id="523b1-429">Tables and Views</span></span>

|<span data-ttu-id="523b1-430">ColumnName</span><span class="sxs-lookup"><span data-stu-id="523b1-430">ColumnName</span></span>|<span data-ttu-id="523b1-431">DataType</span><span class="sxs-lookup"><span data-stu-id="523b1-431">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="523b1-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="523b1-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="523b1-433">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-433">String</span></span>|
|<span data-ttu-id="523b1-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="523b1-434">TABLE_OWNER</span></span>|<span data-ttu-id="523b1-435">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-435">String</span></span>|
|<span data-ttu-id="523b1-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="523b1-436">TABLE_NAME</span></span>|<span data-ttu-id="523b1-437">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-437">String</span></span>|
|<span data-ttu-id="523b1-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="523b1-438">TABLE_TYPE</span></span>|<span data-ttu-id="523b1-439">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-439">String</span></span>|
|<span data-ttu-id="523b1-440">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="523b1-440">REMARKS</span></span>|<span data-ttu-id="523b1-441">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-441">String</span></span>|

### <a name="columns"></a><span data-ttu-id="523b1-442">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="523b1-442">Columns</span></span>

|<span data-ttu-id="523b1-443">ColumnName</span><span class="sxs-lookup"><span data-stu-id="523b1-443">ColumnName</span></span>|<span data-ttu-id="523b1-444">DataType</span><span class="sxs-lookup"><span data-stu-id="523b1-444">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="523b1-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="523b1-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="523b1-446">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-446">String</span></span>|
|<span data-ttu-id="523b1-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="523b1-447">TABLE_OWNER</span></span>|<span data-ttu-id="523b1-448">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-448">String</span></span>|
|<span data-ttu-id="523b1-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="523b1-449">TABLE_NAME</span></span>|<span data-ttu-id="523b1-450">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-450">String</span></span>|
|<span data-ttu-id="523b1-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="523b1-451">COLUMN_NAME</span></span>|<span data-ttu-id="523b1-452">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-452">String</span></span>|
|<span data-ttu-id="523b1-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="523b1-453">DATA_TYPE</span></span>|<span data-ttu-id="523b1-454">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-454">Int16</span></span>|
|<span data-ttu-id="523b1-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="523b1-455">TYPE_NAME</span></span>|<span data-ttu-id="523b1-456">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-456">String</span></span>|
|<span data-ttu-id="523b1-457">DUYARLIK</span><span class="sxs-lookup"><span data-stu-id="523b1-457">PRECISION</span></span>|<span data-ttu-id="523b1-458">Int32</span><span class="sxs-lookup"><span data-stu-id="523b1-458">Int32</span></span>|
|<span data-ttu-id="523b1-459">UZUNLUĞU</span><span class="sxs-lookup"><span data-stu-id="523b1-459">LENGTH</span></span>|<span data-ttu-id="523b1-460">Int32</span><span class="sxs-lookup"><span data-stu-id="523b1-460">Int32</span></span>|
|<span data-ttu-id="523b1-461">ÖLÇEK</span><span class="sxs-lookup"><span data-stu-id="523b1-461">SCALE</span></span>|<span data-ttu-id="523b1-462">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-462">Int16</span></span>|
|<span data-ttu-id="523b1-463">RADIX</span><span class="sxs-lookup"><span data-stu-id="523b1-463">RADIX</span></span>|<span data-ttu-id="523b1-464">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-464">Int16</span></span>|
|<span data-ttu-id="523b1-465">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="523b1-465">NULLABLE</span></span>|<span data-ttu-id="523b1-466">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-466">Int16</span></span>|
|<span data-ttu-id="523b1-467">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="523b1-467">REMARKS</span></span>|<span data-ttu-id="523b1-468">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-468">String</span></span>|
|<span data-ttu-id="523b1-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="523b1-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="523b1-470">Int32</span><span class="sxs-lookup"><span data-stu-id="523b1-470">Int32</span></span>|

### <a name="procedures"></a><span data-ttu-id="523b1-471">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="523b1-471">Procedures</span></span>

|<span data-ttu-id="523b1-472">ColumnName</span><span class="sxs-lookup"><span data-stu-id="523b1-472">ColumnName</span></span>|<span data-ttu-id="523b1-473">DataType</span><span class="sxs-lookup"><span data-stu-id="523b1-473">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="523b1-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="523b1-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="523b1-475">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-475">String</span></span>|
|<span data-ttu-id="523b1-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="523b1-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="523b1-477">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-477">String</span></span>|
|<span data-ttu-id="523b1-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="523b1-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="523b1-479">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-479">String</span></span>|
|<span data-ttu-id="523b1-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="523b1-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="523b1-481">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-481">Int16</span></span>|
|<span data-ttu-id="523b1-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="523b1-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="523b1-483">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-483">Int16</span></span>|
|<span data-ttu-id="523b1-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="523b1-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="523b1-485">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-485">Int16</span></span>|
|<span data-ttu-id="523b1-486">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="523b1-486">REMARKS</span></span>|<span data-ttu-id="523b1-487">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-487">String</span></span>|
|<span data-ttu-id="523b1-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="523b1-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="523b1-489">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-489">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="523b1-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="523b1-490">ProcedureColumns</span></span>

|<span data-ttu-id="523b1-491">ColumnName</span><span class="sxs-lookup"><span data-stu-id="523b1-491">ColumnName</span></span>|<span data-ttu-id="523b1-492">DataType</span><span class="sxs-lookup"><span data-stu-id="523b1-492">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="523b1-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="523b1-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="523b1-494">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-494">String</span></span>|
|<span data-ttu-id="523b1-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="523b1-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="523b1-496">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-496">String</span></span>|
|<span data-ttu-id="523b1-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="523b1-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="523b1-498">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-498">String</span></span>|
|<span data-ttu-id="523b1-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="523b1-499">COLUMN_NAME</span></span>|<span data-ttu-id="523b1-500">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-500">String</span></span>|
|<span data-ttu-id="523b1-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="523b1-501">COLUMN_TYPE</span></span>|<span data-ttu-id="523b1-502">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-502">Int16</span></span>|
|<span data-ttu-id="523b1-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="523b1-503">DATA_TYPE</span></span>|<span data-ttu-id="523b1-504">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-504">Int16</span></span>|
|<span data-ttu-id="523b1-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="523b1-505">TYPE_NAME</span></span>|<span data-ttu-id="523b1-506">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-506">String</span></span>|
|<span data-ttu-id="523b1-507">DUYARLIK</span><span class="sxs-lookup"><span data-stu-id="523b1-507">PRECISION</span></span>|<span data-ttu-id="523b1-508">Int32</span><span class="sxs-lookup"><span data-stu-id="523b1-508">Int32</span></span>|
|<span data-ttu-id="523b1-509">UZUNLUĞU</span><span class="sxs-lookup"><span data-stu-id="523b1-509">LENGTH</span></span>|<span data-ttu-id="523b1-510">Int32</span><span class="sxs-lookup"><span data-stu-id="523b1-510">Int32</span></span>|
|<span data-ttu-id="523b1-511">ÖLÇEK</span><span class="sxs-lookup"><span data-stu-id="523b1-511">SCALE</span></span>|<span data-ttu-id="523b1-512">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-512">Int16</span></span>|
|<span data-ttu-id="523b1-513">RADIX</span><span class="sxs-lookup"><span data-stu-id="523b1-513">RADIX</span></span>|<span data-ttu-id="523b1-514">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-514">Int16</span></span>|
|<span data-ttu-id="523b1-515">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="523b1-515">NULLABLE</span></span>|<span data-ttu-id="523b1-516">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-516">Int16</span></span>|
|<span data-ttu-id="523b1-517">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="523b1-517">REMARKS</span></span>|<span data-ttu-id="523b1-518">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-518">String</span></span>|
|<span data-ttu-id="523b1-519">AŞIRI YÜKLEME</span><span class="sxs-lookup"><span data-stu-id="523b1-519">OVERLOAD</span></span>|<span data-ttu-id="523b1-520">Int32</span><span class="sxs-lookup"><span data-stu-id="523b1-520">Int32</span></span>|
|<span data-ttu-id="523b1-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="523b1-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="523b1-522">Int32</span><span class="sxs-lookup"><span data-stu-id="523b1-522">Int32</span></span>|

### <a name="procedureparameters"></a><span data-ttu-id="523b1-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="523b1-523">ProcedureParameters</span></span>

|<span data-ttu-id="523b1-524">ColumnName</span><span class="sxs-lookup"><span data-stu-id="523b1-524">ColumnName</span></span>|<span data-ttu-id="523b1-525">DataType</span><span class="sxs-lookup"><span data-stu-id="523b1-525">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="523b1-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="523b1-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="523b1-527">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-527">String</span></span>|
|<span data-ttu-id="523b1-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="523b1-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="523b1-529">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-529">String</span></span>|
|<span data-ttu-id="523b1-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="523b1-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="523b1-531">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-531">String</span></span>|
|<span data-ttu-id="523b1-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="523b1-532">COLUMN_NAME</span></span>|<span data-ttu-id="523b1-533">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-533">String</span></span>|
|<span data-ttu-id="523b1-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="523b1-534">COLUMN_TYPE</span></span>|<span data-ttu-id="523b1-535">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-535">Int16</span></span>|
|<span data-ttu-id="523b1-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="523b1-536">DATA_TYPE</span></span>|<span data-ttu-id="523b1-537">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-537">Int16</span></span>|
|<span data-ttu-id="523b1-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="523b1-538">TYPE_NAME</span></span>|<span data-ttu-id="523b1-539">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-539">String</span></span>|
|<span data-ttu-id="523b1-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="523b1-540">COLUMN_SIZE</span></span>|<span data-ttu-id="523b1-541">Int32</span><span class="sxs-lookup"><span data-stu-id="523b1-541">Int32</span></span>|
|<span data-ttu-id="523b1-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="523b1-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="523b1-543">Int32</span><span class="sxs-lookup"><span data-stu-id="523b1-543">Int32</span></span>|
|<span data-ttu-id="523b1-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="523b1-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="523b1-545">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-545">Int16</span></span>|
|<span data-ttu-id="523b1-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="523b1-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="523b1-547">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-547">Int16</span></span>|
|<span data-ttu-id="523b1-548">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="523b1-548">NULLABLE</span></span>|<span data-ttu-id="523b1-549">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-549">Int16</span></span>|
|<span data-ttu-id="523b1-550">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="523b1-550">REMARKS</span></span>|<span data-ttu-id="523b1-551">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-551">String</span></span>|
|<span data-ttu-id="523b1-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="523b1-552">COLUMN_DEF</span></span>|<span data-ttu-id="523b1-553">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-553">String</span></span>|
|<span data-ttu-id="523b1-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="523b1-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="523b1-555">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-555">Int16</span></span>|
|<span data-ttu-id="523b1-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="523b1-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="523b1-557">Int16</span><span class="sxs-lookup"><span data-stu-id="523b1-557">Int16</span></span>|
|<span data-ttu-id="523b1-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="523b1-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="523b1-559">Int32</span><span class="sxs-lookup"><span data-stu-id="523b1-559">Int32</span></span>|
|<span data-ttu-id="523b1-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="523b1-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="523b1-561">Int32</span><span class="sxs-lookup"><span data-stu-id="523b1-561">Int32</span></span>|
|<span data-ttu-id="523b1-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="523b1-562">IS_NULLABLE</span></span>|<span data-ttu-id="523b1-563">Dize</span><span class="sxs-lookup"><span data-stu-id="523b1-563">String</span></span>|

## <a name="see-also"></a><span data-ttu-id="523b1-564">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="523b1-564">See also</span></span>

- [<span data-ttu-id="523b1-565">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="523b1-565">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
