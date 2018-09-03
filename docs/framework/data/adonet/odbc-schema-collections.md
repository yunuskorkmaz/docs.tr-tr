---
title: ODBC şema koleksiyonları
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: bdedbb11960f02b99dcca6388abf663635238f74
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43479986"
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="cac14-102">ODBC şema koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="cac14-102">ODBC Schema Collections</span></span>
<span data-ttu-id="cac14-103">Bu bölümde, Microsoft SQL Server, Oracle ve Microsoft Jet ODBC sürücüleri için şema koleksiyonu desteği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cac14-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="cac14-104">Microsoft SQL Server ODBC sürücüsü</span><span class="sxs-lookup"><span data-stu-id="cac14-104">Microsoft SQL Server ODBC Driver</span></span>  
 <span data-ttu-id="cac14-105">Microsoft SQL Server ODBC sürücüsü, ortak şema koleksiyonları ek olarak aşağıdaki belirli şema koleksiyonları destekler:</span><span class="sxs-lookup"><span data-stu-id="cac14-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="cac14-106">Tabloları</span><span class="sxs-lookup"><span data-stu-id="cac14-106">Tables</span></span>  
  
-   <span data-ttu-id="cac14-107">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="cac14-107">Indexes</span></span>  
  
-   <span data-ttu-id="cac14-108">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="cac14-108">Columns</span></span>  
  
-   <span data-ttu-id="cac14-109">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="cac14-109">Procedures</span></span>  
  
-   <span data-ttu-id="cac14-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="cac14-110">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="cac14-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="cac14-111">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="cac14-112">Görünümler</span><span class="sxs-lookup"><span data-stu-id="cac14-112">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="cac14-113">Tabloları ve görünümleri</span><span class="sxs-lookup"><span data-stu-id="cac14-113">Tables and Views</span></span>  
  
|<span data-ttu-id="cac14-114">ColumnName</span><span class="sxs-lookup"><span data-stu-id="cac14-114">ColumnName</span></span>|<span data-ttu-id="cac14-115">Veri türü</span><span class="sxs-lookup"><span data-stu-id="cac14-115">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cac14-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="cac14-116">TABLE_CAT</span></span>|<span data-ttu-id="cac14-117">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-117">String</span></span>|  
|<span data-ttu-id="cac14-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="cac14-118">TABLE_SCHEM</span></span>|<span data-ttu-id="cac14-119">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-119">String</span></span>|  
|<span data-ttu-id="cac14-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="cac14-120">TABLE_NAME</span></span>|<span data-ttu-id="cac14-121">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-121">String</span></span>|  
|<span data-ttu-id="cac14-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="cac14-122">TABLE_TYPE</span></span>|<span data-ttu-id="cac14-123">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-123">String</span></span>|  
|<span data-ttu-id="cac14-124">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="cac14-124">REMARKS</span></span>|<span data-ttu-id="cac14-125">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-125">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="cac14-126">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="cac14-126">Indexes</span></span>  
  
|<span data-ttu-id="cac14-127">ColumnName</span><span class="sxs-lookup"><span data-stu-id="cac14-127">ColumnName</span></span>|<span data-ttu-id="cac14-128">Veri türü</span><span class="sxs-lookup"><span data-stu-id="cac14-128">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cac14-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="cac14-129">TABLE_CAT</span></span>|<span data-ttu-id="cac14-130">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-130">String</span></span>|  
|<span data-ttu-id="cac14-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="cac14-131">TABLE_SCHEM</span></span>|<span data-ttu-id="cac14-132">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-132">String</span></span>|  
|<span data-ttu-id="cac14-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="cac14-133">TABLE_NAME</span></span>|<span data-ttu-id="cac14-134">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-134">String</span></span>|  
|<span data-ttu-id="cac14-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="cac14-135">NON_UNIQUE</span></span>|<span data-ttu-id="cac14-136">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-136">Int16</span></span>|  
|<span data-ttu-id="cac14-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="cac14-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="cac14-138">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-138">String</span></span>|  
|<span data-ttu-id="cac14-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="cac14-139">INDEX_NAME</span></span>|<span data-ttu-id="cac14-140">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-140">String</span></span>|  
|<span data-ttu-id="cac14-141">TÜRÜ</span><span class="sxs-lookup"><span data-stu-id="cac14-141">TYPE</span></span>|<span data-ttu-id="cac14-142">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-142">Int16</span></span>|  
|<span data-ttu-id="cac14-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="cac14-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="cac14-144">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-144">Int16</span></span>|  
|<span data-ttu-id="cac14-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="cac14-145">COLUMN_NAME</span></span>|<span data-ttu-id="cac14-146">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-146">String</span></span>|  
|<span data-ttu-id="cac14-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="cac14-147">ASC_OR_DESC</span></span>|<span data-ttu-id="cac14-148">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-148">String</span></span>|  
|<span data-ttu-id="cac14-149">CARDINATLITY</span><span class="sxs-lookup"><span data-stu-id="cac14-149">CARDINATLITY</span></span>|<span data-ttu-id="cac14-150">Int32</span><span class="sxs-lookup"><span data-stu-id="cac14-150">Int32</span></span>|  
|<span data-ttu-id="cac14-151">SAYFALARI</span><span class="sxs-lookup"><span data-stu-id="cac14-151">PAGES</span></span>|<span data-ttu-id="cac14-152">Int32</span><span class="sxs-lookup"><span data-stu-id="cac14-152">Int32</span></span>|  
|<span data-ttu-id="cac14-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="cac14-153">FILTER_CONDITION</span></span>|<span data-ttu-id="cac14-154">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-154">String</span></span>|  
|<span data-ttu-id="cac14-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cac14-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="cac14-156">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-156">String</span></span>|  
|<span data-ttu-id="cac14-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cac14-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="cac14-158">Bayt</span><span class="sxs-lookup"><span data-stu-id="cac14-158">Byte</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="cac14-159">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="cac14-159">Columns</span></span>  
  
|<span data-ttu-id="cac14-160">ColumnName</span><span class="sxs-lookup"><span data-stu-id="cac14-160">ColumnName</span></span>|<span data-ttu-id="cac14-161">Veri türü</span><span class="sxs-lookup"><span data-stu-id="cac14-161">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cac14-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="cac14-162">TABLE_CAT</span></span>|<span data-ttu-id="cac14-163">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-163">String</span></span>|  
|<span data-ttu-id="cac14-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="cac14-164">TABLE_SCHEM</span></span>|<span data-ttu-id="cac14-165">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-165">String</span></span>|  
|<span data-ttu-id="cac14-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="cac14-166">TABLE_NAME</span></span>|<span data-ttu-id="cac14-167">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-167">String</span></span>|  
|<span data-ttu-id="cac14-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="cac14-168">COLUMN_NAME</span></span>|<span data-ttu-id="cac14-169">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-169">String</span></span>|  
|<span data-ttu-id="cac14-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cac14-170">DATA_TYPE</span></span>|<span data-ttu-id="cac14-171">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-171">Int16</span></span>|  
|<span data-ttu-id="cac14-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="cac14-172">TYPE_NAME</span></span>|<span data-ttu-id="cac14-173">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-173">String</span></span>|  
|<span data-ttu-id="cac14-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="cac14-174">COLUMN_SIZE</span></span>|<span data-ttu-id="cac14-175">Int32</span><span class="sxs-lookup"><span data-stu-id="cac14-175">Int32</span></span>|  
|<span data-ttu-id="cac14-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="cac14-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="cac14-177">Int32</span><span class="sxs-lookup"><span data-stu-id="cac14-177">Int32</span></span>|  
|<span data-ttu-id="cac14-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="cac14-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="cac14-179">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-179">Int16</span></span>|  
|<span data-ttu-id="cac14-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="cac14-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="cac14-181">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-181">Int16</span></span>|  
|<span data-ttu-id="cac14-182">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="cac14-182">NULLABLE</span></span>|<span data-ttu-id="cac14-183">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-183">Int16</span></span>|  
|<span data-ttu-id="cac14-184">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="cac14-184">REMARKS</span></span>|<span data-ttu-id="cac14-185">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-185">String</span></span>|  
|<span data-ttu-id="cac14-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="cac14-186">COLUMN_DEF</span></span>|<span data-ttu-id="cac14-187">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-187">String</span></span>|  
|<span data-ttu-id="cac14-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cac14-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="cac14-189">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-189">Int16</span></span>|  
|<span data-ttu-id="cac14-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="cac14-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="cac14-191">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-191">Int16</span></span>|  
|<span data-ttu-id="cac14-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="cac14-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="cac14-193">Int32</span><span class="sxs-lookup"><span data-stu-id="cac14-193">Int32</span></span>|  
|<span data-ttu-id="cac14-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="cac14-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="cac14-195">Int32</span><span class="sxs-lookup"><span data-stu-id="cac14-195">Int32</span></span>|  
|<span data-ttu-id="cac14-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="cac14-196">IS_NULLABLE</span></span>|<span data-ttu-id="cac14-197">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-197">String</span></span>|  
|<span data-ttu-id="cac14-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="cac14-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="cac14-199">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-199">String</span></span>|  
|<span data-ttu-id="cac14-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cac14-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="cac14-201">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-201">String</span></span>|  
|<span data-ttu-id="cac14-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cac14-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="cac14-203">Bayt</span><span class="sxs-lookup"><span data-stu-id="cac14-203">Byte</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="cac14-204">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="cac14-204">Procedures</span></span>  
  
|<span data-ttu-id="cac14-205">ColumnName</span><span class="sxs-lookup"><span data-stu-id="cac14-205">ColumnName</span></span>|<span data-ttu-id="cac14-206">Veri türü</span><span class="sxs-lookup"><span data-stu-id="cac14-206">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cac14-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="cac14-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="cac14-208">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-208">String</span></span>|  
|<span data-ttu-id="cac14-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="cac14-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="cac14-210">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-210">String</span></span>|  
|<span data-ttu-id="cac14-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="cac14-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="cac14-212">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-212">String</span></span>|  
|<span data-ttu-id="cac14-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="cac14-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="cac14-214">Int32</span><span class="sxs-lookup"><span data-stu-id="cac14-214">Int32</span></span>|  
|<span data-ttu-id="cac14-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="cac14-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="cac14-216">Int32</span><span class="sxs-lookup"><span data-stu-id="cac14-216">Int32</span></span>|  
|<span data-ttu-id="cac14-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="cac14-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="cac14-218">Int32</span><span class="sxs-lookup"><span data-stu-id="cac14-218">Int32</span></span>|  
|<span data-ttu-id="cac14-219">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="cac14-219">REMARKS</span></span>|<span data-ttu-id="cac14-220">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-220">String</span></span>|  
|<span data-ttu-id="cac14-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="cac14-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="cac14-222">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-222">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="cac14-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="cac14-223">ProcedureColumns</span></span>  
  
|<span data-ttu-id="cac14-224">ColumnName</span><span class="sxs-lookup"><span data-stu-id="cac14-224">ColumnName</span></span>|<span data-ttu-id="cac14-225">Veri türü</span><span class="sxs-lookup"><span data-stu-id="cac14-225">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cac14-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="cac14-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="cac14-227">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-227">String</span></span>|  
|<span data-ttu-id="cac14-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="cac14-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="cac14-229">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-229">String</span></span>|  
|<span data-ttu-id="cac14-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="cac14-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="cac14-231">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-231">String</span></span>|  
|<span data-ttu-id="cac14-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="cac14-232">COLUMN_NAME</span></span>|<span data-ttu-id="cac14-233">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-233">String</span></span>|  
|<span data-ttu-id="cac14-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="cac14-234">COLUMN_TYPE</span></span>|<span data-ttu-id="cac14-235">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-235">Int16</span></span>|  
|<span data-ttu-id="cac14-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cac14-236">DATA_TYPE</span></span>|<span data-ttu-id="cac14-237">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-237">Int16</span></span>|  
|<span data-ttu-id="cac14-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="cac14-238">TYPE_NAME</span></span>|<span data-ttu-id="cac14-239">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-239">String</span></span>|  
|<span data-ttu-id="cac14-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="cac14-240">COLUMN_SIZE</span></span>|<span data-ttu-id="cac14-241">Int32</span><span class="sxs-lookup"><span data-stu-id="cac14-241">Int32</span></span>|  
|<span data-ttu-id="cac14-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="cac14-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="cac14-243">Int32</span><span class="sxs-lookup"><span data-stu-id="cac14-243">Int32</span></span>|  
|<span data-ttu-id="cac14-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="cac14-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="cac14-245">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-245">Int16</span></span>|  
|<span data-ttu-id="cac14-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="cac14-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="cac14-247">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-247">Int16</span></span>|  
|<span data-ttu-id="cac14-248">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="cac14-248">NULLABLE</span></span>|<span data-ttu-id="cac14-249">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-249">Int16</span></span>|  
|<span data-ttu-id="cac14-250">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="cac14-250">REMARKS</span></span>|<span data-ttu-id="cac14-251">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-251">String</span></span>|  
|<span data-ttu-id="cac14-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="cac14-252">COLUMN_DEF</span></span>|<span data-ttu-id="cac14-253">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-253">String</span></span>|  
|<span data-ttu-id="cac14-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cac14-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="cac14-255">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-255">Int16</span></span>|  
|<span data-ttu-id="cac14-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="cac14-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="cac14-257">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-257">Int16</span></span>|  
|<span data-ttu-id="cac14-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="cac14-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="cac14-259">Int32</span><span class="sxs-lookup"><span data-stu-id="cac14-259">Int32</span></span>|  
|<span data-ttu-id="cac14-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="cac14-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="cac14-261">Int32</span><span class="sxs-lookup"><span data-stu-id="cac14-261">Int32</span></span>|  
|<span data-ttu-id="cac14-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="cac14-262">IS_NULLABLE</span></span>|<span data-ttu-id="cac14-263">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-263">String</span></span>|  
|<span data-ttu-id="cac14-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="cac14-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="cac14-265">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-265">String</span></span>|  
|<span data-ttu-id="cac14-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cac14-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="cac14-267">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-267">String</span></span>|  
|<span data-ttu-id="cac14-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cac14-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="cac14-269">Bayt</span><span class="sxs-lookup"><span data-stu-id="cac14-269">Byte</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="cac14-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="cac14-270">ProcedureParameters</span></span>  
  
|<span data-ttu-id="cac14-271">ColumnName</span><span class="sxs-lookup"><span data-stu-id="cac14-271">ColumnName</span></span>|<span data-ttu-id="cac14-272">Veri türü</span><span class="sxs-lookup"><span data-stu-id="cac14-272">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cac14-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="cac14-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="cac14-274">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-274">String</span></span>|  
|<span data-ttu-id="cac14-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="cac14-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="cac14-276">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-276">String</span></span>|  
|<span data-ttu-id="cac14-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="cac14-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="cac14-278">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-278">String</span></span>|  
|<span data-ttu-id="cac14-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="cac14-279">COLUMN_NAME</span></span>|<span data-ttu-id="cac14-280">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-280">String</span></span>|  
|<span data-ttu-id="cac14-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="cac14-281">COLUMN_TYPE</span></span>|<span data-ttu-id="cac14-282">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-282">Int16</span></span>|  
|<span data-ttu-id="cac14-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cac14-283">DATA_TYPE</span></span>|<span data-ttu-id="cac14-284">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-284">Int16</span></span>|  
|<span data-ttu-id="cac14-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="cac14-285">TYPE_NAME</span></span>|<span data-ttu-id="cac14-286">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-286">String</span></span>|  
|<span data-ttu-id="cac14-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="cac14-287">COLUMN_SIZE</span></span>|<span data-ttu-id="cac14-288">Int32</span><span class="sxs-lookup"><span data-stu-id="cac14-288">Int32</span></span>|  
|<span data-ttu-id="cac14-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="cac14-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="cac14-290">Int32</span><span class="sxs-lookup"><span data-stu-id="cac14-290">Int32</span></span>|  
|<span data-ttu-id="cac14-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="cac14-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="cac14-292">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-292">Int16</span></span>|  
|<span data-ttu-id="cac14-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="cac14-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="cac14-294">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-294">Int16</span></span>|  
|<span data-ttu-id="cac14-295">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="cac14-295">NULLABLE</span></span>|<span data-ttu-id="cac14-296">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-296">Int16</span></span>|  
|<span data-ttu-id="cac14-297">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="cac14-297">REMARKS</span></span>|<span data-ttu-id="cac14-298">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-298">String</span></span>|  
|<span data-ttu-id="cac14-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="cac14-299">COLUMN_DEF</span></span>|<span data-ttu-id="cac14-300">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-300">String</span></span>|  
|<span data-ttu-id="cac14-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cac14-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="cac14-302">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-302">Int16</span></span>|  
|<span data-ttu-id="cac14-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="cac14-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="cac14-304">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-304">Int16</span></span>|  
|<span data-ttu-id="cac14-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="cac14-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="cac14-306">Int32</span><span class="sxs-lookup"><span data-stu-id="cac14-306">Int32</span></span>|  
|<span data-ttu-id="cac14-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="cac14-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="cac14-308">Int32</span><span class="sxs-lookup"><span data-stu-id="cac14-308">Int32</span></span>|  
|<span data-ttu-id="cac14-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="cac14-309">IS_NULLABLE</span></span>|<span data-ttu-id="cac14-310">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-310">String</span></span>|  
|<span data-ttu-id="cac14-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="cac14-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="cac14-312">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-312">String</span></span>|  
|<span data-ttu-id="cac14-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cac14-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="cac14-314">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-314">String</span></span>|  
|<span data-ttu-id="cac14-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cac14-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="cac14-316">Bayt</span><span class="sxs-lookup"><span data-stu-id="cac14-316">Byte</span></span>|  
  
## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="cac14-317">Microsoft Oracle ODBC sürücüsü</span><span class="sxs-lookup"><span data-stu-id="cac14-317">Microsoft Oracle ODBC Driver</span></span>  
 <span data-ttu-id="cac14-318">Microsoft SQL Server ve Oracle ODBC sürücüsü, ortak şema koleksiyonları ek olarak aşağıdaki belirli şema koleksiyonları destekler:</span><span class="sxs-lookup"><span data-stu-id="cac14-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="cac14-319">Tabloları</span><span class="sxs-lookup"><span data-stu-id="cac14-319">Tables</span></span>  
  
-   <span data-ttu-id="cac14-320">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="cac14-320">Columns</span></span>  
  
-   <span data-ttu-id="cac14-321">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="cac14-321">Procedures</span></span>  
  
-   <span data-ttu-id="cac14-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="cac14-322">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="cac14-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="cac14-323">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="cac14-324">Görünümler</span><span class="sxs-lookup"><span data-stu-id="cac14-324">Views</span></span>  
  
-   <span data-ttu-id="cac14-325">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="cac14-325">Indexes</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="cac14-326">Tabloları ve görünümleri</span><span class="sxs-lookup"><span data-stu-id="cac14-326">Tables and Views</span></span>  
  
|<span data-ttu-id="cac14-327">ColumnName</span><span class="sxs-lookup"><span data-stu-id="cac14-327">ColumnName</span></span>|<span data-ttu-id="cac14-328">Veri türü</span><span class="sxs-lookup"><span data-stu-id="cac14-328">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cac14-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="cac14-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="cac14-330">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-330">String</span></span>|  
|<span data-ttu-id="cac14-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="cac14-331">TABLE_OWNER</span></span>|<span data-ttu-id="cac14-332">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-332">String</span></span>|  
|<span data-ttu-id="cac14-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="cac14-333">TABLE_NAME</span></span>|<span data-ttu-id="cac14-334">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-334">String</span></span>|  
|<span data-ttu-id="cac14-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="cac14-335">TABLE_TYPE</span></span>|<span data-ttu-id="cac14-336">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-336">String</span></span>|  
|<span data-ttu-id="cac14-337">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="cac14-337">REMARKS</span></span>|<span data-ttu-id="cac14-338">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-338">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="cac14-339">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="cac14-339">Columns</span></span>  
  
|<span data-ttu-id="cac14-340">ColumnName</span><span class="sxs-lookup"><span data-stu-id="cac14-340">ColumnName</span></span>|<span data-ttu-id="cac14-341">Veri türü</span><span class="sxs-lookup"><span data-stu-id="cac14-341">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cac14-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="cac14-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="cac14-343">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-343">String</span></span>|  
|<span data-ttu-id="cac14-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="cac14-344">TABLE_OWNER</span></span>|<span data-ttu-id="cac14-345">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-345">String</span></span>|  
|<span data-ttu-id="cac14-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="cac14-346">TABLE_NAME</span></span>|<span data-ttu-id="cac14-347">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-347">String</span></span>|  
|<span data-ttu-id="cac14-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="cac14-348">COLUMN_NAME</span></span>|<span data-ttu-id="cac14-349">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-349">String</span></span>|  
|<span data-ttu-id="cac14-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cac14-350">DATA_TYPE</span></span>|<span data-ttu-id="cac14-351">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-351">Int16</span></span>|  
|<span data-ttu-id="cac14-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="cac14-352">TYPE_NAME</span></span>|<span data-ttu-id="cac14-353">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-353">String</span></span>|  
|<span data-ttu-id="cac14-354">DUYARLIK</span><span class="sxs-lookup"><span data-stu-id="cac14-354">PRECISION</span></span>|<span data-ttu-id="cac14-355">Int32</span><span class="sxs-lookup"><span data-stu-id="cac14-355">Int32</span></span>|  
|<span data-ttu-id="cac14-356">UZUNLUĞU</span><span class="sxs-lookup"><span data-stu-id="cac14-356">LENGTH</span></span>|<span data-ttu-id="cac14-357">Int32</span><span class="sxs-lookup"><span data-stu-id="cac14-357">Int32</span></span>|  
|<span data-ttu-id="cac14-358">ÖLÇEK</span><span class="sxs-lookup"><span data-stu-id="cac14-358">SCALE</span></span>|<span data-ttu-id="cac14-359">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-359">Int16</span></span>|  
|<span data-ttu-id="cac14-360">SAYI TABANI</span><span class="sxs-lookup"><span data-stu-id="cac14-360">RADIX</span></span>|<span data-ttu-id="cac14-361">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-361">Int16</span></span>|  
|<span data-ttu-id="cac14-362">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="cac14-362">NULLABLE</span></span>|<span data-ttu-id="cac14-363">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-363">Int16</span></span>|  
|<span data-ttu-id="cac14-364">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="cac14-364">REMARKS</span></span>|<span data-ttu-id="cac14-365">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-365">String</span></span>|  
|<span data-ttu-id="cac14-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="cac14-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="cac14-367">Int32</span><span class="sxs-lookup"><span data-stu-id="cac14-367">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="cac14-368">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="cac14-368">Procedures</span></span>  
  
|<span data-ttu-id="cac14-369">ColumnName</span><span class="sxs-lookup"><span data-stu-id="cac14-369">ColumnName</span></span>|<span data-ttu-id="cac14-370">Veri türü</span><span class="sxs-lookup"><span data-stu-id="cac14-370">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cac14-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="cac14-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="cac14-372">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-372">String</span></span>|  
|<span data-ttu-id="cac14-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="cac14-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="cac14-374">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-374">String</span></span>|  
|<span data-ttu-id="cac14-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="cac14-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="cac14-376">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-376">String</span></span>|  
|<span data-ttu-id="cac14-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="cac14-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="cac14-378">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-378">Int16</span></span>|  
|<span data-ttu-id="cac14-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="cac14-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="cac14-380">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-380">Int16</span></span>|  
|<span data-ttu-id="cac14-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="cac14-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="cac14-382">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-382">Int16</span></span>|  
|<span data-ttu-id="cac14-383">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="cac14-383">REMARKS</span></span>|<span data-ttu-id="cac14-384">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-384">String</span></span>|  
|<span data-ttu-id="cac14-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="cac14-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="cac14-386">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-386">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="cac14-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="cac14-387">ProcedureColumns</span></span>  
  
|<span data-ttu-id="cac14-388">ColumnName</span><span class="sxs-lookup"><span data-stu-id="cac14-388">ColumnName</span></span>|<span data-ttu-id="cac14-389">Veri türü</span><span class="sxs-lookup"><span data-stu-id="cac14-389">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cac14-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="cac14-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="cac14-391">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-391">String</span></span>|  
|<span data-ttu-id="cac14-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="cac14-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="cac14-393">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-393">String</span></span>|  
|<span data-ttu-id="cac14-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="cac14-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="cac14-395">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-395">String</span></span>|  
|<span data-ttu-id="cac14-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="cac14-396">COLUMN_NAME</span></span>|<span data-ttu-id="cac14-397">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-397">String</span></span>|  
|<span data-ttu-id="cac14-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="cac14-398">COLUMN_TYPE</span></span>|<span data-ttu-id="cac14-399">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-399">Int16</span></span>|  
|<span data-ttu-id="cac14-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cac14-400">DATA_TYPE</span></span>|<span data-ttu-id="cac14-401">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-401">Int16</span></span>|  
|<span data-ttu-id="cac14-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="cac14-402">TYPE_NAME</span></span>|<span data-ttu-id="cac14-403">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-403">String</span></span>|  
|<span data-ttu-id="cac14-404">DUYARLIK</span><span class="sxs-lookup"><span data-stu-id="cac14-404">PRECISION</span></span>|<span data-ttu-id="cac14-405">Int32</span><span class="sxs-lookup"><span data-stu-id="cac14-405">Int32</span></span>|  
|<span data-ttu-id="cac14-406">UZUNLUĞU</span><span class="sxs-lookup"><span data-stu-id="cac14-406">LENGTH</span></span>|<span data-ttu-id="cac14-407">Int32</span><span class="sxs-lookup"><span data-stu-id="cac14-407">Int32</span></span>|  
|<span data-ttu-id="cac14-408">ÖLÇEK</span><span class="sxs-lookup"><span data-stu-id="cac14-408">SCALE</span></span>|<span data-ttu-id="cac14-409">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-409">Int16</span></span>|  
|<span data-ttu-id="cac14-410">SAYI TABANI</span><span class="sxs-lookup"><span data-stu-id="cac14-410">RADIX</span></span>|<span data-ttu-id="cac14-411">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-411">Int16</span></span>|  
|<span data-ttu-id="cac14-412">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="cac14-412">NULLABLE</span></span>|<span data-ttu-id="cac14-413">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-413">Int16</span></span>|  
|<span data-ttu-id="cac14-414">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="cac14-414">REMARKS</span></span>|<span data-ttu-id="cac14-415">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-415">String</span></span>|  
|<span data-ttu-id="cac14-416">AŞIRI YÜKLEME</span><span class="sxs-lookup"><span data-stu-id="cac14-416">OVERLOAD</span></span>|<span data-ttu-id="cac14-417">Int32</span><span class="sxs-lookup"><span data-stu-id="cac14-417">Int32</span></span>|  
|<span data-ttu-id="cac14-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="cac14-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="cac14-419">Int32</span><span class="sxs-lookup"><span data-stu-id="cac14-419">Int32</span></span>|  
  
## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="cac14-420">Microsoft Jet ODBC sürücüsü</span><span class="sxs-lookup"><span data-stu-id="cac14-420">Microsoft Jet ODBC Driver</span></span>  
 <span data-ttu-id="cac14-421">Microsoft Jet ODBC sürücüsü, ortak şema koleksiyonları ek olarak aşağıdaki belirli şema koleksiyonları destekler:</span><span class="sxs-lookup"><span data-stu-id="cac14-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="cac14-422">Tabloları</span><span class="sxs-lookup"><span data-stu-id="cac14-422">Tables</span></span>  
  
-   <span data-ttu-id="cac14-423">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="cac14-423">Indexes</span></span>  
  
-   <span data-ttu-id="cac14-424">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="cac14-424">Columns</span></span>  
  
-   <span data-ttu-id="cac14-425">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="cac14-425">Procedures</span></span>  
  
-   <span data-ttu-id="cac14-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="cac14-426">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="cac14-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="cac14-427">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="cac14-428">Görünümler</span><span class="sxs-lookup"><span data-stu-id="cac14-428">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="cac14-429">Tabloları ve görünümleri</span><span class="sxs-lookup"><span data-stu-id="cac14-429">Tables and Views</span></span>  
  
|<span data-ttu-id="cac14-430">ColumnName</span><span class="sxs-lookup"><span data-stu-id="cac14-430">ColumnName</span></span>|<span data-ttu-id="cac14-431">Veri türü</span><span class="sxs-lookup"><span data-stu-id="cac14-431">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cac14-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="cac14-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="cac14-433">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-433">String</span></span>|  
|<span data-ttu-id="cac14-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="cac14-434">TABLE_OWNER</span></span>|<span data-ttu-id="cac14-435">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-435">String</span></span>|  
|<span data-ttu-id="cac14-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="cac14-436">TABLE_NAME</span></span>|<span data-ttu-id="cac14-437">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-437">String</span></span>|  
|<span data-ttu-id="cac14-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="cac14-438">TABLE_TYPE</span></span>|<span data-ttu-id="cac14-439">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-439">String</span></span>|  
|<span data-ttu-id="cac14-440">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="cac14-440">REMARKS</span></span>|<span data-ttu-id="cac14-441">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-441">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="cac14-442">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="cac14-442">Columns</span></span>  
  
|<span data-ttu-id="cac14-443">ColumnName</span><span class="sxs-lookup"><span data-stu-id="cac14-443">ColumnName</span></span>|<span data-ttu-id="cac14-444">Veri türü</span><span class="sxs-lookup"><span data-stu-id="cac14-444">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cac14-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="cac14-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="cac14-446">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-446">String</span></span>|  
|<span data-ttu-id="cac14-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="cac14-447">TABLE_OWNER</span></span>|<span data-ttu-id="cac14-448">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-448">String</span></span>|  
|<span data-ttu-id="cac14-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="cac14-449">TABLE_NAME</span></span>|<span data-ttu-id="cac14-450">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-450">String</span></span>|  
|<span data-ttu-id="cac14-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="cac14-451">COLUMN_NAME</span></span>|<span data-ttu-id="cac14-452">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-452">String</span></span>|  
|<span data-ttu-id="cac14-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cac14-453">DATA_TYPE</span></span>|<span data-ttu-id="cac14-454">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-454">Int16</span></span>|  
|<span data-ttu-id="cac14-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="cac14-455">TYPE_NAME</span></span>|<span data-ttu-id="cac14-456">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-456">String</span></span>|  
|<span data-ttu-id="cac14-457">DUYARLIK</span><span class="sxs-lookup"><span data-stu-id="cac14-457">PRECISION</span></span>|<span data-ttu-id="cac14-458">Int32</span><span class="sxs-lookup"><span data-stu-id="cac14-458">Int32</span></span>|  
|<span data-ttu-id="cac14-459">UZUNLUĞU</span><span class="sxs-lookup"><span data-stu-id="cac14-459">LENGTH</span></span>|<span data-ttu-id="cac14-460">Int32</span><span class="sxs-lookup"><span data-stu-id="cac14-460">Int32</span></span>|  
|<span data-ttu-id="cac14-461">ÖLÇEK</span><span class="sxs-lookup"><span data-stu-id="cac14-461">SCALE</span></span>|<span data-ttu-id="cac14-462">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-462">Int16</span></span>|  
|<span data-ttu-id="cac14-463">SAYI TABANI</span><span class="sxs-lookup"><span data-stu-id="cac14-463">RADIX</span></span>|<span data-ttu-id="cac14-464">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-464">Int16</span></span>|  
|<span data-ttu-id="cac14-465">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="cac14-465">NULLABLE</span></span>|<span data-ttu-id="cac14-466">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-466">Int16</span></span>|  
|<span data-ttu-id="cac14-467">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="cac14-467">REMARKS</span></span>|<span data-ttu-id="cac14-468">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-468">String</span></span>|  
|<span data-ttu-id="cac14-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="cac14-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="cac14-470">Int32</span><span class="sxs-lookup"><span data-stu-id="cac14-470">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="cac14-471">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="cac14-471">Procedures</span></span>  
  
|<span data-ttu-id="cac14-472">ColumnName</span><span class="sxs-lookup"><span data-stu-id="cac14-472">ColumnName</span></span>|<span data-ttu-id="cac14-473">Veri türü</span><span class="sxs-lookup"><span data-stu-id="cac14-473">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cac14-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="cac14-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="cac14-475">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-475">String</span></span>|  
|<span data-ttu-id="cac14-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="cac14-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="cac14-477">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-477">String</span></span>|  
|<span data-ttu-id="cac14-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="cac14-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="cac14-479">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-479">String</span></span>|  
|<span data-ttu-id="cac14-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="cac14-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="cac14-481">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-481">Int16</span></span>|  
|<span data-ttu-id="cac14-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="cac14-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="cac14-483">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-483">Int16</span></span>|  
|<span data-ttu-id="cac14-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="cac14-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="cac14-485">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-485">Int16</span></span>|  
|<span data-ttu-id="cac14-486">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="cac14-486">REMARKS</span></span>|<span data-ttu-id="cac14-487">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-487">String</span></span>|  
|<span data-ttu-id="cac14-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="cac14-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="cac14-489">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-489">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="cac14-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="cac14-490">ProcedureColumns</span></span>  
  
|<span data-ttu-id="cac14-491">ColumnName</span><span class="sxs-lookup"><span data-stu-id="cac14-491">ColumnName</span></span>|<span data-ttu-id="cac14-492">Veri türü</span><span class="sxs-lookup"><span data-stu-id="cac14-492">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cac14-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="cac14-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="cac14-494">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-494">String</span></span>|  
|<span data-ttu-id="cac14-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="cac14-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="cac14-496">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-496">String</span></span>|  
|<span data-ttu-id="cac14-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="cac14-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="cac14-498">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-498">String</span></span>|  
|<span data-ttu-id="cac14-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="cac14-499">COLUMN_NAME</span></span>|<span data-ttu-id="cac14-500">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-500">String</span></span>|  
|<span data-ttu-id="cac14-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="cac14-501">COLUMN_TYPE</span></span>|<span data-ttu-id="cac14-502">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-502">Int16</span></span>|  
|<span data-ttu-id="cac14-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cac14-503">DATA_TYPE</span></span>|<span data-ttu-id="cac14-504">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-504">Int16</span></span>|  
|<span data-ttu-id="cac14-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="cac14-505">TYPE_NAME</span></span>|<span data-ttu-id="cac14-506">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-506">String</span></span>|  
|<span data-ttu-id="cac14-507">DUYARLIK</span><span class="sxs-lookup"><span data-stu-id="cac14-507">PRECISION</span></span>|<span data-ttu-id="cac14-508">Int32</span><span class="sxs-lookup"><span data-stu-id="cac14-508">Int32</span></span>|  
|<span data-ttu-id="cac14-509">UZUNLUĞU</span><span class="sxs-lookup"><span data-stu-id="cac14-509">LENGTH</span></span>|<span data-ttu-id="cac14-510">Int32</span><span class="sxs-lookup"><span data-stu-id="cac14-510">Int32</span></span>|  
|<span data-ttu-id="cac14-511">ÖLÇEK</span><span class="sxs-lookup"><span data-stu-id="cac14-511">SCALE</span></span>|<span data-ttu-id="cac14-512">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-512">Int16</span></span>|  
|<span data-ttu-id="cac14-513">SAYI TABANI</span><span class="sxs-lookup"><span data-stu-id="cac14-513">RADIX</span></span>|<span data-ttu-id="cac14-514">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-514">Int16</span></span>|  
|<span data-ttu-id="cac14-515">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="cac14-515">NULLABLE</span></span>|<span data-ttu-id="cac14-516">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-516">Int16</span></span>|  
|<span data-ttu-id="cac14-517">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="cac14-517">REMARKS</span></span>|<span data-ttu-id="cac14-518">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-518">String</span></span>|  
|<span data-ttu-id="cac14-519">AŞIRI YÜKLEME</span><span class="sxs-lookup"><span data-stu-id="cac14-519">OVERLOAD</span></span>|<span data-ttu-id="cac14-520">Int32</span><span class="sxs-lookup"><span data-stu-id="cac14-520">Int32</span></span>|  
|<span data-ttu-id="cac14-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="cac14-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="cac14-522">Int32</span><span class="sxs-lookup"><span data-stu-id="cac14-522">Int32</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="cac14-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="cac14-523">ProcedureParameters</span></span>  
  
|<span data-ttu-id="cac14-524">ColumnName</span><span class="sxs-lookup"><span data-stu-id="cac14-524">ColumnName</span></span>|<span data-ttu-id="cac14-525">Veri türü</span><span class="sxs-lookup"><span data-stu-id="cac14-525">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cac14-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="cac14-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="cac14-527">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-527">String</span></span>|  
|<span data-ttu-id="cac14-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="cac14-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="cac14-529">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-529">String</span></span>|  
|<span data-ttu-id="cac14-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="cac14-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="cac14-531">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-531">String</span></span>|  
|<span data-ttu-id="cac14-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="cac14-532">COLUMN_NAME</span></span>|<span data-ttu-id="cac14-533">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-533">String</span></span>|  
|<span data-ttu-id="cac14-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="cac14-534">COLUMN_TYPE</span></span>|<span data-ttu-id="cac14-535">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-535">Int16</span></span>|  
|<span data-ttu-id="cac14-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cac14-536">DATA_TYPE</span></span>|<span data-ttu-id="cac14-537">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-537">Int16</span></span>|  
|<span data-ttu-id="cac14-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="cac14-538">TYPE_NAME</span></span>|<span data-ttu-id="cac14-539">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-539">String</span></span>|  
|<span data-ttu-id="cac14-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="cac14-540">COLUMN_SIZE</span></span>|<span data-ttu-id="cac14-541">Int32</span><span class="sxs-lookup"><span data-stu-id="cac14-541">Int32</span></span>|  
|<span data-ttu-id="cac14-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="cac14-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="cac14-543">Int32</span><span class="sxs-lookup"><span data-stu-id="cac14-543">Int32</span></span>|  
|<span data-ttu-id="cac14-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="cac14-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="cac14-545">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-545">Int16</span></span>|  
|<span data-ttu-id="cac14-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="cac14-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="cac14-547">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-547">Int16</span></span>|  
|<span data-ttu-id="cac14-548">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="cac14-548">NULLABLE</span></span>|<span data-ttu-id="cac14-549">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-549">Int16</span></span>|  
|<span data-ttu-id="cac14-550">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="cac14-550">REMARKS</span></span>|<span data-ttu-id="cac14-551">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-551">String</span></span>|  
|<span data-ttu-id="cac14-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="cac14-552">COLUMN_DEF</span></span>|<span data-ttu-id="cac14-553">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-553">String</span></span>|  
|<span data-ttu-id="cac14-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cac14-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="cac14-555">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-555">Int16</span></span>|  
|<span data-ttu-id="cac14-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="cac14-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="cac14-557">Int16</span><span class="sxs-lookup"><span data-stu-id="cac14-557">Int16</span></span>|  
|<span data-ttu-id="cac14-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="cac14-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="cac14-559">Int32</span><span class="sxs-lookup"><span data-stu-id="cac14-559">Int32</span></span>|  
|<span data-ttu-id="cac14-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="cac14-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="cac14-561">Int32</span><span class="sxs-lookup"><span data-stu-id="cac14-561">Int32</span></span>|  
|<span data-ttu-id="cac14-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="cac14-562">IS_NULLABLE</span></span>|<span data-ttu-id="cac14-563">Dize</span><span class="sxs-lookup"><span data-stu-id="cac14-563">String</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cac14-564">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cac14-564">See Also</span></span>  
 [<span data-ttu-id="cac14-565">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="cac14-565">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
