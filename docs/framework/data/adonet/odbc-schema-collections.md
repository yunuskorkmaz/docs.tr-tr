---
title: ODBC şema koleksiyonları
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: ffe80120ceffbe29c0a117cf1194860c5782be8c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365912"
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="f6115-102">ODBC şema koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="f6115-102">ODBC Schema Collections</span></span>

<span data-ttu-id="f6115-103">Bu bölümde, Microsoft SQL Server, Oracle ve Microsoft Jet ODBC sürücüleri için şema koleksiyonu desteği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f6115-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>

## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="f6115-104">Microsoft SQL Server ODBC sürücüsü</span><span class="sxs-lookup"><span data-stu-id="f6115-104">Microsoft SQL Server ODBC Driver</span></span>

<span data-ttu-id="f6115-105">Microsoft SQL Server ODBC sürücüsü, ortak şema koleksiyonları ek olarak aşağıdaki belirli şema koleksiyonları destekler:</span><span class="sxs-lookup"><span data-stu-id="f6115-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="f6115-106">Tabloları</span><span class="sxs-lookup"><span data-stu-id="f6115-106">Tables</span></span>

- <span data-ttu-id="f6115-107">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="f6115-107">Indexes</span></span>

- <span data-ttu-id="f6115-108">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="f6115-108">Columns</span></span>

- <span data-ttu-id="f6115-109">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="f6115-109">Procedures</span></span>

- <span data-ttu-id="f6115-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="f6115-110">ProcedureColumns</span></span>

- <span data-ttu-id="f6115-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="f6115-111">ProcedureParameters</span></span>

- <span data-ttu-id="f6115-112">Görünümler</span><span class="sxs-lookup"><span data-stu-id="f6115-112">Views</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="f6115-113">Tabloları ve görünümleri</span><span class="sxs-lookup"><span data-stu-id="f6115-113">Tables and Views</span></span>

|<span data-ttu-id="f6115-114">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f6115-114">ColumnName</span></span>|<span data-ttu-id="f6115-115">DataType</span><span class="sxs-lookup"><span data-stu-id="f6115-115">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="f6115-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="f6115-116">TABLE_CAT</span></span>|<span data-ttu-id="f6115-117">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-117">String</span></span>|
|<span data-ttu-id="f6115-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="f6115-118">TABLE_SCHEM</span></span>|<span data-ttu-id="f6115-119">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-119">String</span></span>|
|<span data-ttu-id="f6115-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f6115-120">TABLE_NAME</span></span>|<span data-ttu-id="f6115-121">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-121">String</span></span>|
|<span data-ttu-id="f6115-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f6115-122">TABLE_TYPE</span></span>|<span data-ttu-id="f6115-123">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-123">String</span></span>|
|<span data-ttu-id="f6115-124">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="f6115-124">REMARKS</span></span>|<span data-ttu-id="f6115-125">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-125">String</span></span>|

### <a name="indexes"></a><span data-ttu-id="f6115-126">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="f6115-126">Indexes</span></span>

|<span data-ttu-id="f6115-127">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f6115-127">ColumnName</span></span>|<span data-ttu-id="f6115-128">DataType</span><span class="sxs-lookup"><span data-stu-id="f6115-128">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="f6115-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="f6115-129">TABLE_CAT</span></span>|<span data-ttu-id="f6115-130">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-130">String</span></span>|
|<span data-ttu-id="f6115-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="f6115-131">TABLE_SCHEM</span></span>|<span data-ttu-id="f6115-132">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-132">String</span></span>|
|<span data-ttu-id="f6115-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f6115-133">TABLE_NAME</span></span>|<span data-ttu-id="f6115-134">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-134">String</span></span>|
|<span data-ttu-id="f6115-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="f6115-135">NON_UNIQUE</span></span>|<span data-ttu-id="f6115-136">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-136">Int16</span></span>|
|<span data-ttu-id="f6115-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="f6115-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="f6115-138">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-138">String</span></span>|
|<span data-ttu-id="f6115-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="f6115-139">INDEX_NAME</span></span>|<span data-ttu-id="f6115-140">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-140">String</span></span>|
|<span data-ttu-id="f6115-141">TÜRÜ</span><span class="sxs-lookup"><span data-stu-id="f6115-141">TYPE</span></span>|<span data-ttu-id="f6115-142">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-142">Int16</span></span>|
|<span data-ttu-id="f6115-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f6115-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="f6115-144">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-144">Int16</span></span>|
|<span data-ttu-id="f6115-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f6115-145">COLUMN_NAME</span></span>|<span data-ttu-id="f6115-146">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-146">String</span></span>|
|<span data-ttu-id="f6115-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="f6115-147">ASC_OR_DESC</span></span>|<span data-ttu-id="f6115-148">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-148">String</span></span>|
|<span data-ttu-id="f6115-149">ÖNEM DÜZEYİ</span><span class="sxs-lookup"><span data-stu-id="f6115-149">CARDINALITY</span></span>|<span data-ttu-id="f6115-150">Int32</span><span class="sxs-lookup"><span data-stu-id="f6115-150">Int32</span></span>|
|<span data-ttu-id="f6115-151">SAYFALARI</span><span class="sxs-lookup"><span data-stu-id="f6115-151">PAGES</span></span>|<span data-ttu-id="f6115-152">Int32</span><span class="sxs-lookup"><span data-stu-id="f6115-152">Int32</span></span>|
|<span data-ttu-id="f6115-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="f6115-153">FILTER_CONDITION</span></span>|<span data-ttu-id="f6115-154">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-154">String</span></span>|
|<span data-ttu-id="f6115-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f6115-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="f6115-156">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-156">String</span></span>|
|<span data-ttu-id="f6115-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f6115-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="f6115-158">Bayt</span><span class="sxs-lookup"><span data-stu-id="f6115-158">Byte</span></span>|

### <a name="columns"></a><span data-ttu-id="f6115-159">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="f6115-159">Columns</span></span>

|<span data-ttu-id="f6115-160">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f6115-160">ColumnName</span></span>|<span data-ttu-id="f6115-161">DataType</span><span class="sxs-lookup"><span data-stu-id="f6115-161">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="f6115-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="f6115-162">TABLE_CAT</span></span>|<span data-ttu-id="f6115-163">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-163">String</span></span>|
|<span data-ttu-id="f6115-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="f6115-164">TABLE_SCHEM</span></span>|<span data-ttu-id="f6115-165">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-165">String</span></span>|
|<span data-ttu-id="f6115-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f6115-166">TABLE_NAME</span></span>|<span data-ttu-id="f6115-167">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-167">String</span></span>|
|<span data-ttu-id="f6115-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f6115-168">COLUMN_NAME</span></span>|<span data-ttu-id="f6115-169">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-169">String</span></span>|
|<span data-ttu-id="f6115-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f6115-170">DATA_TYPE</span></span>|<span data-ttu-id="f6115-171">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-171">Int16</span></span>|
|<span data-ttu-id="f6115-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="f6115-172">TYPE_NAME</span></span>|<span data-ttu-id="f6115-173">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-173">String</span></span>|
|<span data-ttu-id="f6115-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="f6115-174">COLUMN_SIZE</span></span>|<span data-ttu-id="f6115-175">Int32</span><span class="sxs-lookup"><span data-stu-id="f6115-175">Int32</span></span>|
|<span data-ttu-id="f6115-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f6115-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="f6115-177">Int32</span><span class="sxs-lookup"><span data-stu-id="f6115-177">Int32</span></span>|
|<span data-ttu-id="f6115-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="f6115-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="f6115-179">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-179">Int16</span></span>|
|<span data-ttu-id="f6115-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="f6115-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="f6115-181">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-181">Int16</span></span>|
|<span data-ttu-id="f6115-182">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="f6115-182">NULLABLE</span></span>|<span data-ttu-id="f6115-183">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-183">Int16</span></span>|
|<span data-ttu-id="f6115-184">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="f6115-184">REMARKS</span></span>|<span data-ttu-id="f6115-185">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-185">String</span></span>|
|<span data-ttu-id="f6115-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="f6115-186">COLUMN_DEF</span></span>|<span data-ttu-id="f6115-187">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-187">String</span></span>|
|<span data-ttu-id="f6115-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f6115-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="f6115-189">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-189">Int16</span></span>|
|<span data-ttu-id="f6115-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="f6115-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="f6115-191">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-191">Int16</span></span>|
|<span data-ttu-id="f6115-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f6115-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="f6115-193">Int32</span><span class="sxs-lookup"><span data-stu-id="f6115-193">Int32</span></span>|
|<span data-ttu-id="f6115-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f6115-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="f6115-195">Int32</span><span class="sxs-lookup"><span data-stu-id="f6115-195">Int32</span></span>|
|<span data-ttu-id="f6115-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f6115-196">IS_NULLABLE</span></span>|<span data-ttu-id="f6115-197">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-197">String</span></span>|
|<span data-ttu-id="f6115-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f6115-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="f6115-199">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-199">String</span></span>|
|<span data-ttu-id="f6115-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f6115-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="f6115-201">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-201">String</span></span>|
|<span data-ttu-id="f6115-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f6115-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="f6115-203">Bayt</span><span class="sxs-lookup"><span data-stu-id="f6115-203">Byte</span></span>|

### <a name="procedures"></a><span data-ttu-id="f6115-204">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="f6115-204">Procedures</span></span>

|<span data-ttu-id="f6115-205">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f6115-205">ColumnName</span></span>|<span data-ttu-id="f6115-206">DataType</span><span class="sxs-lookup"><span data-stu-id="f6115-206">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="f6115-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="f6115-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="f6115-208">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-208">String</span></span>|
|<span data-ttu-id="f6115-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="f6115-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="f6115-210">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-210">String</span></span>|
|<span data-ttu-id="f6115-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f6115-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="f6115-212">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-212">String</span></span>|
|<span data-ttu-id="f6115-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="f6115-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="f6115-214">Int32</span><span class="sxs-lookup"><span data-stu-id="f6115-214">Int32</span></span>|
|<span data-ttu-id="f6115-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="f6115-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="f6115-216">Int32</span><span class="sxs-lookup"><span data-stu-id="f6115-216">Int32</span></span>|
|<span data-ttu-id="f6115-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="f6115-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="f6115-218">Int32</span><span class="sxs-lookup"><span data-stu-id="f6115-218">Int32</span></span>|
|<span data-ttu-id="f6115-219">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="f6115-219">REMARKS</span></span>|<span data-ttu-id="f6115-220">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-220">String</span></span>|
|<span data-ttu-id="f6115-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f6115-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="f6115-222">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-222">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="f6115-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="f6115-223">ProcedureColumns</span></span>

|<span data-ttu-id="f6115-224">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f6115-224">ColumnName</span></span>|<span data-ttu-id="f6115-225">DataType</span><span class="sxs-lookup"><span data-stu-id="f6115-225">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="f6115-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="f6115-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="f6115-227">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-227">String</span></span>|
|<span data-ttu-id="f6115-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="f6115-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="f6115-229">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-229">String</span></span>|
|<span data-ttu-id="f6115-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f6115-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="f6115-231">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-231">String</span></span>|
|<span data-ttu-id="f6115-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f6115-232">COLUMN_NAME</span></span>|<span data-ttu-id="f6115-233">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-233">String</span></span>|
|<span data-ttu-id="f6115-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="f6115-234">COLUMN_TYPE</span></span>|<span data-ttu-id="f6115-235">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-235">Int16</span></span>|
|<span data-ttu-id="f6115-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f6115-236">DATA_TYPE</span></span>|<span data-ttu-id="f6115-237">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-237">Int16</span></span>|
|<span data-ttu-id="f6115-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="f6115-238">TYPE_NAME</span></span>|<span data-ttu-id="f6115-239">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-239">String</span></span>|
|<span data-ttu-id="f6115-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="f6115-240">COLUMN_SIZE</span></span>|<span data-ttu-id="f6115-241">Int32</span><span class="sxs-lookup"><span data-stu-id="f6115-241">Int32</span></span>|
|<span data-ttu-id="f6115-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f6115-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="f6115-243">Int32</span><span class="sxs-lookup"><span data-stu-id="f6115-243">Int32</span></span>|
|<span data-ttu-id="f6115-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="f6115-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="f6115-245">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-245">Int16</span></span>|
|<span data-ttu-id="f6115-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="f6115-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="f6115-247">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-247">Int16</span></span>|
|<span data-ttu-id="f6115-248">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="f6115-248">NULLABLE</span></span>|<span data-ttu-id="f6115-249">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-249">Int16</span></span>|
|<span data-ttu-id="f6115-250">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="f6115-250">REMARKS</span></span>|<span data-ttu-id="f6115-251">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-251">String</span></span>|
|<span data-ttu-id="f6115-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="f6115-252">COLUMN_DEF</span></span>|<span data-ttu-id="f6115-253">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-253">String</span></span>|
|<span data-ttu-id="f6115-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f6115-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="f6115-255">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-255">Int16</span></span>|
|<span data-ttu-id="f6115-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="f6115-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="f6115-257">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-257">Int16</span></span>|
|<span data-ttu-id="f6115-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f6115-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="f6115-259">Int32</span><span class="sxs-lookup"><span data-stu-id="f6115-259">Int32</span></span>|
|<span data-ttu-id="f6115-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f6115-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="f6115-261">Int32</span><span class="sxs-lookup"><span data-stu-id="f6115-261">Int32</span></span>|
|<span data-ttu-id="f6115-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f6115-262">IS_NULLABLE</span></span>|<span data-ttu-id="f6115-263">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-263">String</span></span>|
|<span data-ttu-id="f6115-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f6115-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="f6115-265">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-265">String</span></span>|
|<span data-ttu-id="f6115-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f6115-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="f6115-267">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-267">String</span></span>|
|<span data-ttu-id="f6115-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f6115-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="f6115-269">Bayt</span><span class="sxs-lookup"><span data-stu-id="f6115-269">Byte</span></span>|

### <a name="procedureparameters"></a><span data-ttu-id="f6115-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="f6115-270">ProcedureParameters</span></span>

|<span data-ttu-id="f6115-271">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f6115-271">ColumnName</span></span>|<span data-ttu-id="f6115-272">DataType</span><span class="sxs-lookup"><span data-stu-id="f6115-272">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="f6115-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="f6115-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="f6115-274">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-274">String</span></span>|
|<span data-ttu-id="f6115-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="f6115-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="f6115-276">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-276">String</span></span>|
|<span data-ttu-id="f6115-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f6115-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="f6115-278">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-278">String</span></span>|
|<span data-ttu-id="f6115-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f6115-279">COLUMN_NAME</span></span>|<span data-ttu-id="f6115-280">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-280">String</span></span>|
|<span data-ttu-id="f6115-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="f6115-281">COLUMN_TYPE</span></span>|<span data-ttu-id="f6115-282">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-282">Int16</span></span>|
|<span data-ttu-id="f6115-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f6115-283">DATA_TYPE</span></span>|<span data-ttu-id="f6115-284">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-284">Int16</span></span>|
|<span data-ttu-id="f6115-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="f6115-285">TYPE_NAME</span></span>|<span data-ttu-id="f6115-286">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-286">String</span></span>|
|<span data-ttu-id="f6115-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="f6115-287">COLUMN_SIZE</span></span>|<span data-ttu-id="f6115-288">Int32</span><span class="sxs-lookup"><span data-stu-id="f6115-288">Int32</span></span>|
|<span data-ttu-id="f6115-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f6115-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="f6115-290">Int32</span><span class="sxs-lookup"><span data-stu-id="f6115-290">Int32</span></span>|
|<span data-ttu-id="f6115-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="f6115-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="f6115-292">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-292">Int16</span></span>|
|<span data-ttu-id="f6115-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="f6115-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="f6115-294">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-294">Int16</span></span>|
|<span data-ttu-id="f6115-295">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="f6115-295">NULLABLE</span></span>|<span data-ttu-id="f6115-296">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-296">Int16</span></span>|
|<span data-ttu-id="f6115-297">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="f6115-297">REMARKS</span></span>|<span data-ttu-id="f6115-298">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-298">String</span></span>|
|<span data-ttu-id="f6115-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="f6115-299">COLUMN_DEF</span></span>|<span data-ttu-id="f6115-300">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-300">String</span></span>|
|<span data-ttu-id="f6115-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f6115-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="f6115-302">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-302">Int16</span></span>|
|<span data-ttu-id="f6115-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="f6115-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="f6115-304">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-304">Int16</span></span>|
|<span data-ttu-id="f6115-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f6115-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="f6115-306">Int32</span><span class="sxs-lookup"><span data-stu-id="f6115-306">Int32</span></span>|
|<span data-ttu-id="f6115-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f6115-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="f6115-308">Int32</span><span class="sxs-lookup"><span data-stu-id="f6115-308">Int32</span></span>|
|<span data-ttu-id="f6115-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f6115-309">IS_NULLABLE</span></span>|<span data-ttu-id="f6115-310">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-310">String</span></span>|
|<span data-ttu-id="f6115-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f6115-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="f6115-312">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-312">String</span></span>|
|<span data-ttu-id="f6115-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f6115-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="f6115-314">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-314">String</span></span>|
|<span data-ttu-id="f6115-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f6115-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="f6115-316">Bayt</span><span class="sxs-lookup"><span data-stu-id="f6115-316">Byte</span></span>|

## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="f6115-317">Microsoft Oracle ODBC sürücüsü</span><span class="sxs-lookup"><span data-stu-id="f6115-317">Microsoft Oracle ODBC Driver</span></span>

<span data-ttu-id="f6115-318">Microsoft SQL Server ve Oracle ODBC sürücüsü, ortak şema koleksiyonları ek olarak aşağıdaki belirli şema koleksiyonları destekler:</span><span class="sxs-lookup"><span data-stu-id="f6115-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="f6115-319">Tabloları</span><span class="sxs-lookup"><span data-stu-id="f6115-319">Tables</span></span>

- <span data-ttu-id="f6115-320">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="f6115-320">Columns</span></span>

- <span data-ttu-id="f6115-321">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="f6115-321">Procedures</span></span>

- <span data-ttu-id="f6115-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="f6115-322">ProcedureColumns</span></span>

- <span data-ttu-id="f6115-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="f6115-323">ProcedureParameters</span></span>

- <span data-ttu-id="f6115-324">Görünümler</span><span class="sxs-lookup"><span data-stu-id="f6115-324">Views</span></span>

- <span data-ttu-id="f6115-325">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="f6115-325">Indexes</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="f6115-326">Tabloları ve görünümleri</span><span class="sxs-lookup"><span data-stu-id="f6115-326">Tables and Views</span></span>

|<span data-ttu-id="f6115-327">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f6115-327">ColumnName</span></span>|<span data-ttu-id="f6115-328">DataType</span><span class="sxs-lookup"><span data-stu-id="f6115-328">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="f6115-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="f6115-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="f6115-330">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-330">String</span></span>|
|<span data-ttu-id="f6115-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="f6115-331">TABLE_OWNER</span></span>|<span data-ttu-id="f6115-332">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-332">String</span></span>|
|<span data-ttu-id="f6115-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f6115-333">TABLE_NAME</span></span>|<span data-ttu-id="f6115-334">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-334">String</span></span>|
|<span data-ttu-id="f6115-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f6115-335">TABLE_TYPE</span></span>|<span data-ttu-id="f6115-336">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-336">String</span></span>|
|<span data-ttu-id="f6115-337">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="f6115-337">REMARKS</span></span>|<span data-ttu-id="f6115-338">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-338">String</span></span>|

### <a name="columns"></a><span data-ttu-id="f6115-339">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="f6115-339">Columns</span></span>

|<span data-ttu-id="f6115-340">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f6115-340">ColumnName</span></span>|<span data-ttu-id="f6115-341">DataType</span><span class="sxs-lookup"><span data-stu-id="f6115-341">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="f6115-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="f6115-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="f6115-343">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-343">String</span></span>|
|<span data-ttu-id="f6115-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="f6115-344">TABLE_OWNER</span></span>|<span data-ttu-id="f6115-345">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-345">String</span></span>|
|<span data-ttu-id="f6115-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f6115-346">TABLE_NAME</span></span>|<span data-ttu-id="f6115-347">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-347">String</span></span>|
|<span data-ttu-id="f6115-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f6115-348">COLUMN_NAME</span></span>|<span data-ttu-id="f6115-349">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-349">String</span></span>|
|<span data-ttu-id="f6115-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f6115-350">DATA_TYPE</span></span>|<span data-ttu-id="f6115-351">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-351">Int16</span></span>|
|<span data-ttu-id="f6115-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="f6115-352">TYPE_NAME</span></span>|<span data-ttu-id="f6115-353">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-353">String</span></span>|
|<span data-ttu-id="f6115-354">DUYARLIK</span><span class="sxs-lookup"><span data-stu-id="f6115-354">PRECISION</span></span>|<span data-ttu-id="f6115-355">Int32</span><span class="sxs-lookup"><span data-stu-id="f6115-355">Int32</span></span>|
|<span data-ttu-id="f6115-356">UZUNLUĞU</span><span class="sxs-lookup"><span data-stu-id="f6115-356">LENGTH</span></span>|<span data-ttu-id="f6115-357">Int32</span><span class="sxs-lookup"><span data-stu-id="f6115-357">Int32</span></span>|
|<span data-ttu-id="f6115-358">ÖLÇEK</span><span class="sxs-lookup"><span data-stu-id="f6115-358">SCALE</span></span>|<span data-ttu-id="f6115-359">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-359">Int16</span></span>|
|<span data-ttu-id="f6115-360">RADIX</span><span class="sxs-lookup"><span data-stu-id="f6115-360">RADIX</span></span>|<span data-ttu-id="f6115-361">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-361">Int16</span></span>|
|<span data-ttu-id="f6115-362">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="f6115-362">NULLABLE</span></span>|<span data-ttu-id="f6115-363">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-363">Int16</span></span>|
|<span data-ttu-id="f6115-364">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="f6115-364">REMARKS</span></span>|<span data-ttu-id="f6115-365">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-365">String</span></span>|
|<span data-ttu-id="f6115-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f6115-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="f6115-367">Int32</span><span class="sxs-lookup"><span data-stu-id="f6115-367">Int32</span></span>|

### <a name="procedures"></a><span data-ttu-id="f6115-368">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="f6115-368">Procedures</span></span>

|<span data-ttu-id="f6115-369">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f6115-369">ColumnName</span></span>|<span data-ttu-id="f6115-370">DataType</span><span class="sxs-lookup"><span data-stu-id="f6115-370">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="f6115-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="f6115-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="f6115-372">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-372">String</span></span>|
|<span data-ttu-id="f6115-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="f6115-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="f6115-374">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-374">String</span></span>|
|<span data-ttu-id="f6115-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f6115-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="f6115-376">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-376">String</span></span>|
|<span data-ttu-id="f6115-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="f6115-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="f6115-378">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-378">Int16</span></span>|
|<span data-ttu-id="f6115-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="f6115-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="f6115-380">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-380">Int16</span></span>|
|<span data-ttu-id="f6115-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="f6115-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="f6115-382">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-382">Int16</span></span>|
|<span data-ttu-id="f6115-383">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="f6115-383">REMARKS</span></span>|<span data-ttu-id="f6115-384">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-384">String</span></span>|
|<span data-ttu-id="f6115-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f6115-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="f6115-386">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-386">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="f6115-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="f6115-387">ProcedureColumns</span></span>

|<span data-ttu-id="f6115-388">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f6115-388">ColumnName</span></span>|<span data-ttu-id="f6115-389">DataType</span><span class="sxs-lookup"><span data-stu-id="f6115-389">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="f6115-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="f6115-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="f6115-391">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-391">String</span></span>|
|<span data-ttu-id="f6115-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="f6115-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="f6115-393">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-393">String</span></span>|
|<span data-ttu-id="f6115-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f6115-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="f6115-395">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-395">String</span></span>|
|<span data-ttu-id="f6115-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f6115-396">COLUMN_NAME</span></span>|<span data-ttu-id="f6115-397">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-397">String</span></span>|
|<span data-ttu-id="f6115-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="f6115-398">COLUMN_TYPE</span></span>|<span data-ttu-id="f6115-399">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-399">Int16</span></span>|
|<span data-ttu-id="f6115-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f6115-400">DATA_TYPE</span></span>|<span data-ttu-id="f6115-401">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-401">Int16</span></span>|
|<span data-ttu-id="f6115-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="f6115-402">TYPE_NAME</span></span>|<span data-ttu-id="f6115-403">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-403">String</span></span>|
|<span data-ttu-id="f6115-404">DUYARLIK</span><span class="sxs-lookup"><span data-stu-id="f6115-404">PRECISION</span></span>|<span data-ttu-id="f6115-405">Int32</span><span class="sxs-lookup"><span data-stu-id="f6115-405">Int32</span></span>|
|<span data-ttu-id="f6115-406">UZUNLUĞU</span><span class="sxs-lookup"><span data-stu-id="f6115-406">LENGTH</span></span>|<span data-ttu-id="f6115-407">Int32</span><span class="sxs-lookup"><span data-stu-id="f6115-407">Int32</span></span>|
|<span data-ttu-id="f6115-408">ÖLÇEK</span><span class="sxs-lookup"><span data-stu-id="f6115-408">SCALE</span></span>|<span data-ttu-id="f6115-409">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-409">Int16</span></span>|
|<span data-ttu-id="f6115-410">RADIX</span><span class="sxs-lookup"><span data-stu-id="f6115-410">RADIX</span></span>|<span data-ttu-id="f6115-411">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-411">Int16</span></span>|
|<span data-ttu-id="f6115-412">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="f6115-412">NULLABLE</span></span>|<span data-ttu-id="f6115-413">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-413">Int16</span></span>|
|<span data-ttu-id="f6115-414">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="f6115-414">REMARKS</span></span>|<span data-ttu-id="f6115-415">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-415">String</span></span>|
|<span data-ttu-id="f6115-416">AŞIRI YÜKLEME</span><span class="sxs-lookup"><span data-stu-id="f6115-416">OVERLOAD</span></span>|<span data-ttu-id="f6115-417">Int32</span><span class="sxs-lookup"><span data-stu-id="f6115-417">Int32</span></span>|
|<span data-ttu-id="f6115-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f6115-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="f6115-419">Int32</span><span class="sxs-lookup"><span data-stu-id="f6115-419">Int32</span></span>|

## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="f6115-420">Microsoft Jet ODBC sürücüsü</span><span class="sxs-lookup"><span data-stu-id="f6115-420">Microsoft Jet ODBC Driver</span></span>

<span data-ttu-id="f6115-421">Microsoft Jet ODBC sürücüsü, ortak şema koleksiyonları ek olarak aşağıdaki belirli şema koleksiyonları destekler:</span><span class="sxs-lookup"><span data-stu-id="f6115-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="f6115-422">Tabloları</span><span class="sxs-lookup"><span data-stu-id="f6115-422">Tables</span></span>

- <span data-ttu-id="f6115-423">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="f6115-423">Indexes</span></span>

- <span data-ttu-id="f6115-424">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="f6115-424">Columns</span></span>

- <span data-ttu-id="f6115-425">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="f6115-425">Procedures</span></span>

- <span data-ttu-id="f6115-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="f6115-426">ProcedureColumns</span></span>

- <span data-ttu-id="f6115-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="f6115-427">ProcedureParameters</span></span>

- <span data-ttu-id="f6115-428">Görünümler</span><span class="sxs-lookup"><span data-stu-id="f6115-428">Views</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="f6115-429">Tabloları ve görünümleri</span><span class="sxs-lookup"><span data-stu-id="f6115-429">Tables and Views</span></span>

|<span data-ttu-id="f6115-430">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f6115-430">ColumnName</span></span>|<span data-ttu-id="f6115-431">DataType</span><span class="sxs-lookup"><span data-stu-id="f6115-431">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="f6115-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="f6115-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="f6115-433">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-433">String</span></span>|
|<span data-ttu-id="f6115-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="f6115-434">TABLE_OWNER</span></span>|<span data-ttu-id="f6115-435">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-435">String</span></span>|
|<span data-ttu-id="f6115-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f6115-436">TABLE_NAME</span></span>|<span data-ttu-id="f6115-437">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-437">String</span></span>|
|<span data-ttu-id="f6115-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f6115-438">TABLE_TYPE</span></span>|<span data-ttu-id="f6115-439">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-439">String</span></span>|
|<span data-ttu-id="f6115-440">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="f6115-440">REMARKS</span></span>|<span data-ttu-id="f6115-441">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-441">String</span></span>|

### <a name="columns"></a><span data-ttu-id="f6115-442">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="f6115-442">Columns</span></span>

|<span data-ttu-id="f6115-443">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f6115-443">ColumnName</span></span>|<span data-ttu-id="f6115-444">DataType</span><span class="sxs-lookup"><span data-stu-id="f6115-444">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="f6115-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="f6115-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="f6115-446">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-446">String</span></span>|
|<span data-ttu-id="f6115-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="f6115-447">TABLE_OWNER</span></span>|<span data-ttu-id="f6115-448">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-448">String</span></span>|
|<span data-ttu-id="f6115-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f6115-449">TABLE_NAME</span></span>|<span data-ttu-id="f6115-450">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-450">String</span></span>|
|<span data-ttu-id="f6115-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f6115-451">COLUMN_NAME</span></span>|<span data-ttu-id="f6115-452">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-452">String</span></span>|
|<span data-ttu-id="f6115-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f6115-453">DATA_TYPE</span></span>|<span data-ttu-id="f6115-454">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-454">Int16</span></span>|
|<span data-ttu-id="f6115-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="f6115-455">TYPE_NAME</span></span>|<span data-ttu-id="f6115-456">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-456">String</span></span>|
|<span data-ttu-id="f6115-457">DUYARLIK</span><span class="sxs-lookup"><span data-stu-id="f6115-457">PRECISION</span></span>|<span data-ttu-id="f6115-458">Int32</span><span class="sxs-lookup"><span data-stu-id="f6115-458">Int32</span></span>|
|<span data-ttu-id="f6115-459">UZUNLUĞU</span><span class="sxs-lookup"><span data-stu-id="f6115-459">LENGTH</span></span>|<span data-ttu-id="f6115-460">Int32</span><span class="sxs-lookup"><span data-stu-id="f6115-460">Int32</span></span>|
|<span data-ttu-id="f6115-461">ÖLÇEK</span><span class="sxs-lookup"><span data-stu-id="f6115-461">SCALE</span></span>|<span data-ttu-id="f6115-462">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-462">Int16</span></span>|
|<span data-ttu-id="f6115-463">RADIX</span><span class="sxs-lookup"><span data-stu-id="f6115-463">RADIX</span></span>|<span data-ttu-id="f6115-464">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-464">Int16</span></span>|
|<span data-ttu-id="f6115-465">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="f6115-465">NULLABLE</span></span>|<span data-ttu-id="f6115-466">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-466">Int16</span></span>|
|<span data-ttu-id="f6115-467">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="f6115-467">REMARKS</span></span>|<span data-ttu-id="f6115-468">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-468">String</span></span>|
|<span data-ttu-id="f6115-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f6115-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="f6115-470">Int32</span><span class="sxs-lookup"><span data-stu-id="f6115-470">Int32</span></span>|

### <a name="procedures"></a><span data-ttu-id="f6115-471">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="f6115-471">Procedures</span></span>

|<span data-ttu-id="f6115-472">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f6115-472">ColumnName</span></span>|<span data-ttu-id="f6115-473">DataType</span><span class="sxs-lookup"><span data-stu-id="f6115-473">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="f6115-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="f6115-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="f6115-475">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-475">String</span></span>|
|<span data-ttu-id="f6115-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="f6115-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="f6115-477">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-477">String</span></span>|
|<span data-ttu-id="f6115-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f6115-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="f6115-479">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-479">String</span></span>|
|<span data-ttu-id="f6115-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="f6115-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="f6115-481">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-481">Int16</span></span>|
|<span data-ttu-id="f6115-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="f6115-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="f6115-483">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-483">Int16</span></span>|
|<span data-ttu-id="f6115-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="f6115-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="f6115-485">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-485">Int16</span></span>|
|<span data-ttu-id="f6115-486">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="f6115-486">REMARKS</span></span>|<span data-ttu-id="f6115-487">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-487">String</span></span>|
|<span data-ttu-id="f6115-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f6115-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="f6115-489">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-489">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="f6115-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="f6115-490">ProcedureColumns</span></span>

|<span data-ttu-id="f6115-491">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f6115-491">ColumnName</span></span>|<span data-ttu-id="f6115-492">DataType</span><span class="sxs-lookup"><span data-stu-id="f6115-492">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="f6115-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="f6115-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="f6115-494">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-494">String</span></span>|
|<span data-ttu-id="f6115-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="f6115-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="f6115-496">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-496">String</span></span>|
|<span data-ttu-id="f6115-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f6115-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="f6115-498">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-498">String</span></span>|
|<span data-ttu-id="f6115-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f6115-499">COLUMN_NAME</span></span>|<span data-ttu-id="f6115-500">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-500">String</span></span>|
|<span data-ttu-id="f6115-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="f6115-501">COLUMN_TYPE</span></span>|<span data-ttu-id="f6115-502">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-502">Int16</span></span>|
|<span data-ttu-id="f6115-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f6115-503">DATA_TYPE</span></span>|<span data-ttu-id="f6115-504">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-504">Int16</span></span>|
|<span data-ttu-id="f6115-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="f6115-505">TYPE_NAME</span></span>|<span data-ttu-id="f6115-506">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-506">String</span></span>|
|<span data-ttu-id="f6115-507">DUYARLIK</span><span class="sxs-lookup"><span data-stu-id="f6115-507">PRECISION</span></span>|<span data-ttu-id="f6115-508">Int32</span><span class="sxs-lookup"><span data-stu-id="f6115-508">Int32</span></span>|
|<span data-ttu-id="f6115-509">UZUNLUĞU</span><span class="sxs-lookup"><span data-stu-id="f6115-509">LENGTH</span></span>|<span data-ttu-id="f6115-510">Int32</span><span class="sxs-lookup"><span data-stu-id="f6115-510">Int32</span></span>|
|<span data-ttu-id="f6115-511">ÖLÇEK</span><span class="sxs-lookup"><span data-stu-id="f6115-511">SCALE</span></span>|<span data-ttu-id="f6115-512">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-512">Int16</span></span>|
|<span data-ttu-id="f6115-513">RADIX</span><span class="sxs-lookup"><span data-stu-id="f6115-513">RADIX</span></span>|<span data-ttu-id="f6115-514">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-514">Int16</span></span>|
|<span data-ttu-id="f6115-515">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="f6115-515">NULLABLE</span></span>|<span data-ttu-id="f6115-516">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-516">Int16</span></span>|
|<span data-ttu-id="f6115-517">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="f6115-517">REMARKS</span></span>|<span data-ttu-id="f6115-518">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-518">String</span></span>|
|<span data-ttu-id="f6115-519">AŞIRI YÜKLEME</span><span class="sxs-lookup"><span data-stu-id="f6115-519">OVERLOAD</span></span>|<span data-ttu-id="f6115-520">Int32</span><span class="sxs-lookup"><span data-stu-id="f6115-520">Int32</span></span>|
|<span data-ttu-id="f6115-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f6115-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="f6115-522">Int32</span><span class="sxs-lookup"><span data-stu-id="f6115-522">Int32</span></span>|

### <a name="procedureparameters"></a><span data-ttu-id="f6115-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="f6115-523">ProcedureParameters</span></span>

|<span data-ttu-id="f6115-524">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f6115-524">ColumnName</span></span>|<span data-ttu-id="f6115-525">DataType</span><span class="sxs-lookup"><span data-stu-id="f6115-525">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="f6115-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="f6115-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="f6115-527">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-527">String</span></span>|
|<span data-ttu-id="f6115-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="f6115-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="f6115-529">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-529">String</span></span>|
|<span data-ttu-id="f6115-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f6115-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="f6115-531">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-531">String</span></span>|
|<span data-ttu-id="f6115-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f6115-532">COLUMN_NAME</span></span>|<span data-ttu-id="f6115-533">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-533">String</span></span>|
|<span data-ttu-id="f6115-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="f6115-534">COLUMN_TYPE</span></span>|<span data-ttu-id="f6115-535">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-535">Int16</span></span>|
|<span data-ttu-id="f6115-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f6115-536">DATA_TYPE</span></span>|<span data-ttu-id="f6115-537">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-537">Int16</span></span>|
|<span data-ttu-id="f6115-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="f6115-538">TYPE_NAME</span></span>|<span data-ttu-id="f6115-539">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-539">String</span></span>|
|<span data-ttu-id="f6115-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="f6115-540">COLUMN_SIZE</span></span>|<span data-ttu-id="f6115-541">Int32</span><span class="sxs-lookup"><span data-stu-id="f6115-541">Int32</span></span>|
|<span data-ttu-id="f6115-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f6115-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="f6115-543">Int32</span><span class="sxs-lookup"><span data-stu-id="f6115-543">Int32</span></span>|
|<span data-ttu-id="f6115-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="f6115-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="f6115-545">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-545">Int16</span></span>|
|<span data-ttu-id="f6115-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="f6115-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="f6115-547">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-547">Int16</span></span>|
|<span data-ttu-id="f6115-548">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="f6115-548">NULLABLE</span></span>|<span data-ttu-id="f6115-549">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-549">Int16</span></span>|
|<span data-ttu-id="f6115-550">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="f6115-550">REMARKS</span></span>|<span data-ttu-id="f6115-551">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-551">String</span></span>|
|<span data-ttu-id="f6115-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="f6115-552">COLUMN_DEF</span></span>|<span data-ttu-id="f6115-553">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-553">String</span></span>|
|<span data-ttu-id="f6115-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f6115-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="f6115-555">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-555">Int16</span></span>|
|<span data-ttu-id="f6115-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="f6115-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="f6115-557">Int16</span><span class="sxs-lookup"><span data-stu-id="f6115-557">Int16</span></span>|
|<span data-ttu-id="f6115-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f6115-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="f6115-559">Int32</span><span class="sxs-lookup"><span data-stu-id="f6115-559">Int32</span></span>|
|<span data-ttu-id="f6115-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f6115-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="f6115-561">Int32</span><span class="sxs-lookup"><span data-stu-id="f6115-561">Int32</span></span>|
|<span data-ttu-id="f6115-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f6115-562">IS_NULLABLE</span></span>|<span data-ttu-id="f6115-563">Dize</span><span class="sxs-lookup"><span data-stu-id="f6115-563">String</span></span>|

## <a name="see-also"></a><span data-ttu-id="f6115-564">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f6115-564">See also</span></span>

- [<span data-ttu-id="f6115-565">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="f6115-565">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
