---
title: ODBC şema koleksiyonları
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: bdedbb11960f02b99dcca6388abf663635238f74
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43750015"
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="248f6-102">ODBC şema koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="248f6-102">ODBC Schema Collections</span></span>
<span data-ttu-id="248f6-103">Bu bölümde, Microsoft SQL Server, Oracle ve Microsoft Jet ODBC sürücüleri için şema koleksiyonu desteği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="248f6-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="248f6-104">Microsoft SQL Server ODBC sürücüsü</span><span class="sxs-lookup"><span data-stu-id="248f6-104">Microsoft SQL Server ODBC Driver</span></span>  
 <span data-ttu-id="248f6-105">Microsoft SQL Server ODBC sürücüsü, ortak şema koleksiyonları ek olarak aşağıdaki belirli şema koleksiyonları destekler:</span><span class="sxs-lookup"><span data-stu-id="248f6-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="248f6-106">Tabloları</span><span class="sxs-lookup"><span data-stu-id="248f6-106">Tables</span></span>  
  
-   <span data-ttu-id="248f6-107">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="248f6-107">Indexes</span></span>  
  
-   <span data-ttu-id="248f6-108">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="248f6-108">Columns</span></span>  
  
-   <span data-ttu-id="248f6-109">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="248f6-109">Procedures</span></span>  
  
-   <span data-ttu-id="248f6-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="248f6-110">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="248f6-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="248f6-111">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="248f6-112">Görünümler</span><span class="sxs-lookup"><span data-stu-id="248f6-112">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="248f6-113">Tabloları ve görünümleri</span><span class="sxs-lookup"><span data-stu-id="248f6-113">Tables and Views</span></span>  
  
|<span data-ttu-id="248f6-114">ColumnName</span><span class="sxs-lookup"><span data-stu-id="248f6-114">ColumnName</span></span>|<span data-ttu-id="248f6-115">Veri türü</span><span class="sxs-lookup"><span data-stu-id="248f6-115">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="248f6-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="248f6-116">TABLE_CAT</span></span>|<span data-ttu-id="248f6-117">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-117">String</span></span>|  
|<span data-ttu-id="248f6-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="248f6-118">TABLE_SCHEM</span></span>|<span data-ttu-id="248f6-119">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-119">String</span></span>|  
|<span data-ttu-id="248f6-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="248f6-120">TABLE_NAME</span></span>|<span data-ttu-id="248f6-121">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-121">String</span></span>|  
|<span data-ttu-id="248f6-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="248f6-122">TABLE_TYPE</span></span>|<span data-ttu-id="248f6-123">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-123">String</span></span>|  
|<span data-ttu-id="248f6-124">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="248f6-124">REMARKS</span></span>|<span data-ttu-id="248f6-125">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-125">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="248f6-126">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="248f6-126">Indexes</span></span>  
  
|<span data-ttu-id="248f6-127">ColumnName</span><span class="sxs-lookup"><span data-stu-id="248f6-127">ColumnName</span></span>|<span data-ttu-id="248f6-128">Veri türü</span><span class="sxs-lookup"><span data-stu-id="248f6-128">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="248f6-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="248f6-129">TABLE_CAT</span></span>|<span data-ttu-id="248f6-130">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-130">String</span></span>|  
|<span data-ttu-id="248f6-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="248f6-131">TABLE_SCHEM</span></span>|<span data-ttu-id="248f6-132">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-132">String</span></span>|  
|<span data-ttu-id="248f6-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="248f6-133">TABLE_NAME</span></span>|<span data-ttu-id="248f6-134">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-134">String</span></span>|  
|<span data-ttu-id="248f6-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="248f6-135">NON_UNIQUE</span></span>|<span data-ttu-id="248f6-136">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-136">Int16</span></span>|  
|<span data-ttu-id="248f6-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="248f6-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="248f6-138">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-138">String</span></span>|  
|<span data-ttu-id="248f6-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="248f6-139">INDEX_NAME</span></span>|<span data-ttu-id="248f6-140">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-140">String</span></span>|  
|<span data-ttu-id="248f6-141">TÜRÜ</span><span class="sxs-lookup"><span data-stu-id="248f6-141">TYPE</span></span>|<span data-ttu-id="248f6-142">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-142">Int16</span></span>|  
|<span data-ttu-id="248f6-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="248f6-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="248f6-144">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-144">Int16</span></span>|  
|<span data-ttu-id="248f6-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="248f6-145">COLUMN_NAME</span></span>|<span data-ttu-id="248f6-146">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-146">String</span></span>|  
|<span data-ttu-id="248f6-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="248f6-147">ASC_OR_DESC</span></span>|<span data-ttu-id="248f6-148">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-148">String</span></span>|  
|<span data-ttu-id="248f6-149">CARDINATLITY</span><span class="sxs-lookup"><span data-stu-id="248f6-149">CARDINATLITY</span></span>|<span data-ttu-id="248f6-150">Int32</span><span class="sxs-lookup"><span data-stu-id="248f6-150">Int32</span></span>|  
|<span data-ttu-id="248f6-151">SAYFALARI</span><span class="sxs-lookup"><span data-stu-id="248f6-151">PAGES</span></span>|<span data-ttu-id="248f6-152">Int32</span><span class="sxs-lookup"><span data-stu-id="248f6-152">Int32</span></span>|  
|<span data-ttu-id="248f6-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="248f6-153">FILTER_CONDITION</span></span>|<span data-ttu-id="248f6-154">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-154">String</span></span>|  
|<span data-ttu-id="248f6-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="248f6-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="248f6-156">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-156">String</span></span>|  
|<span data-ttu-id="248f6-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="248f6-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="248f6-158">Bayt</span><span class="sxs-lookup"><span data-stu-id="248f6-158">Byte</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="248f6-159">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="248f6-159">Columns</span></span>  
  
|<span data-ttu-id="248f6-160">ColumnName</span><span class="sxs-lookup"><span data-stu-id="248f6-160">ColumnName</span></span>|<span data-ttu-id="248f6-161">Veri türü</span><span class="sxs-lookup"><span data-stu-id="248f6-161">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="248f6-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="248f6-162">TABLE_CAT</span></span>|<span data-ttu-id="248f6-163">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-163">String</span></span>|  
|<span data-ttu-id="248f6-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="248f6-164">TABLE_SCHEM</span></span>|<span data-ttu-id="248f6-165">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-165">String</span></span>|  
|<span data-ttu-id="248f6-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="248f6-166">TABLE_NAME</span></span>|<span data-ttu-id="248f6-167">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-167">String</span></span>|  
|<span data-ttu-id="248f6-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="248f6-168">COLUMN_NAME</span></span>|<span data-ttu-id="248f6-169">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-169">String</span></span>|  
|<span data-ttu-id="248f6-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="248f6-170">DATA_TYPE</span></span>|<span data-ttu-id="248f6-171">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-171">Int16</span></span>|  
|<span data-ttu-id="248f6-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="248f6-172">TYPE_NAME</span></span>|<span data-ttu-id="248f6-173">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-173">String</span></span>|  
|<span data-ttu-id="248f6-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="248f6-174">COLUMN_SIZE</span></span>|<span data-ttu-id="248f6-175">Int32</span><span class="sxs-lookup"><span data-stu-id="248f6-175">Int32</span></span>|  
|<span data-ttu-id="248f6-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="248f6-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="248f6-177">Int32</span><span class="sxs-lookup"><span data-stu-id="248f6-177">Int32</span></span>|  
|<span data-ttu-id="248f6-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="248f6-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="248f6-179">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-179">Int16</span></span>|  
|<span data-ttu-id="248f6-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="248f6-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="248f6-181">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-181">Int16</span></span>|  
|<span data-ttu-id="248f6-182">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="248f6-182">NULLABLE</span></span>|<span data-ttu-id="248f6-183">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-183">Int16</span></span>|  
|<span data-ttu-id="248f6-184">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="248f6-184">REMARKS</span></span>|<span data-ttu-id="248f6-185">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-185">String</span></span>|  
|<span data-ttu-id="248f6-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="248f6-186">COLUMN_DEF</span></span>|<span data-ttu-id="248f6-187">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-187">String</span></span>|  
|<span data-ttu-id="248f6-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="248f6-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="248f6-189">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-189">Int16</span></span>|  
|<span data-ttu-id="248f6-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="248f6-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="248f6-191">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-191">Int16</span></span>|  
|<span data-ttu-id="248f6-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="248f6-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="248f6-193">Int32</span><span class="sxs-lookup"><span data-stu-id="248f6-193">Int32</span></span>|  
|<span data-ttu-id="248f6-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="248f6-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="248f6-195">Int32</span><span class="sxs-lookup"><span data-stu-id="248f6-195">Int32</span></span>|  
|<span data-ttu-id="248f6-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="248f6-196">IS_NULLABLE</span></span>|<span data-ttu-id="248f6-197">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-197">String</span></span>|  
|<span data-ttu-id="248f6-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="248f6-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="248f6-199">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-199">String</span></span>|  
|<span data-ttu-id="248f6-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="248f6-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="248f6-201">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-201">String</span></span>|  
|<span data-ttu-id="248f6-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="248f6-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="248f6-203">Bayt</span><span class="sxs-lookup"><span data-stu-id="248f6-203">Byte</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="248f6-204">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="248f6-204">Procedures</span></span>  
  
|<span data-ttu-id="248f6-205">ColumnName</span><span class="sxs-lookup"><span data-stu-id="248f6-205">ColumnName</span></span>|<span data-ttu-id="248f6-206">Veri türü</span><span class="sxs-lookup"><span data-stu-id="248f6-206">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="248f6-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="248f6-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="248f6-208">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-208">String</span></span>|  
|<span data-ttu-id="248f6-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="248f6-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="248f6-210">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-210">String</span></span>|  
|<span data-ttu-id="248f6-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="248f6-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="248f6-212">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-212">String</span></span>|  
|<span data-ttu-id="248f6-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="248f6-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="248f6-214">Int32</span><span class="sxs-lookup"><span data-stu-id="248f6-214">Int32</span></span>|  
|<span data-ttu-id="248f6-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="248f6-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="248f6-216">Int32</span><span class="sxs-lookup"><span data-stu-id="248f6-216">Int32</span></span>|  
|<span data-ttu-id="248f6-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="248f6-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="248f6-218">Int32</span><span class="sxs-lookup"><span data-stu-id="248f6-218">Int32</span></span>|  
|<span data-ttu-id="248f6-219">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="248f6-219">REMARKS</span></span>|<span data-ttu-id="248f6-220">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-220">String</span></span>|  
|<span data-ttu-id="248f6-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="248f6-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="248f6-222">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-222">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="248f6-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="248f6-223">ProcedureColumns</span></span>  
  
|<span data-ttu-id="248f6-224">ColumnName</span><span class="sxs-lookup"><span data-stu-id="248f6-224">ColumnName</span></span>|<span data-ttu-id="248f6-225">Veri türü</span><span class="sxs-lookup"><span data-stu-id="248f6-225">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="248f6-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="248f6-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="248f6-227">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-227">String</span></span>|  
|<span data-ttu-id="248f6-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="248f6-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="248f6-229">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-229">String</span></span>|  
|<span data-ttu-id="248f6-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="248f6-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="248f6-231">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-231">String</span></span>|  
|<span data-ttu-id="248f6-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="248f6-232">COLUMN_NAME</span></span>|<span data-ttu-id="248f6-233">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-233">String</span></span>|  
|<span data-ttu-id="248f6-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="248f6-234">COLUMN_TYPE</span></span>|<span data-ttu-id="248f6-235">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-235">Int16</span></span>|  
|<span data-ttu-id="248f6-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="248f6-236">DATA_TYPE</span></span>|<span data-ttu-id="248f6-237">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-237">Int16</span></span>|  
|<span data-ttu-id="248f6-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="248f6-238">TYPE_NAME</span></span>|<span data-ttu-id="248f6-239">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-239">String</span></span>|  
|<span data-ttu-id="248f6-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="248f6-240">COLUMN_SIZE</span></span>|<span data-ttu-id="248f6-241">Int32</span><span class="sxs-lookup"><span data-stu-id="248f6-241">Int32</span></span>|  
|<span data-ttu-id="248f6-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="248f6-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="248f6-243">Int32</span><span class="sxs-lookup"><span data-stu-id="248f6-243">Int32</span></span>|  
|<span data-ttu-id="248f6-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="248f6-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="248f6-245">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-245">Int16</span></span>|  
|<span data-ttu-id="248f6-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="248f6-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="248f6-247">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-247">Int16</span></span>|  
|<span data-ttu-id="248f6-248">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="248f6-248">NULLABLE</span></span>|<span data-ttu-id="248f6-249">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-249">Int16</span></span>|  
|<span data-ttu-id="248f6-250">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="248f6-250">REMARKS</span></span>|<span data-ttu-id="248f6-251">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-251">String</span></span>|  
|<span data-ttu-id="248f6-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="248f6-252">COLUMN_DEF</span></span>|<span data-ttu-id="248f6-253">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-253">String</span></span>|  
|<span data-ttu-id="248f6-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="248f6-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="248f6-255">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-255">Int16</span></span>|  
|<span data-ttu-id="248f6-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="248f6-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="248f6-257">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-257">Int16</span></span>|  
|<span data-ttu-id="248f6-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="248f6-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="248f6-259">Int32</span><span class="sxs-lookup"><span data-stu-id="248f6-259">Int32</span></span>|  
|<span data-ttu-id="248f6-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="248f6-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="248f6-261">Int32</span><span class="sxs-lookup"><span data-stu-id="248f6-261">Int32</span></span>|  
|<span data-ttu-id="248f6-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="248f6-262">IS_NULLABLE</span></span>|<span data-ttu-id="248f6-263">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-263">String</span></span>|  
|<span data-ttu-id="248f6-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="248f6-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="248f6-265">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-265">String</span></span>|  
|<span data-ttu-id="248f6-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="248f6-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="248f6-267">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-267">String</span></span>|  
|<span data-ttu-id="248f6-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="248f6-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="248f6-269">Bayt</span><span class="sxs-lookup"><span data-stu-id="248f6-269">Byte</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="248f6-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="248f6-270">ProcedureParameters</span></span>  
  
|<span data-ttu-id="248f6-271">ColumnName</span><span class="sxs-lookup"><span data-stu-id="248f6-271">ColumnName</span></span>|<span data-ttu-id="248f6-272">Veri türü</span><span class="sxs-lookup"><span data-stu-id="248f6-272">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="248f6-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="248f6-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="248f6-274">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-274">String</span></span>|  
|<span data-ttu-id="248f6-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="248f6-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="248f6-276">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-276">String</span></span>|  
|<span data-ttu-id="248f6-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="248f6-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="248f6-278">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-278">String</span></span>|  
|<span data-ttu-id="248f6-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="248f6-279">COLUMN_NAME</span></span>|<span data-ttu-id="248f6-280">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-280">String</span></span>|  
|<span data-ttu-id="248f6-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="248f6-281">COLUMN_TYPE</span></span>|<span data-ttu-id="248f6-282">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-282">Int16</span></span>|  
|<span data-ttu-id="248f6-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="248f6-283">DATA_TYPE</span></span>|<span data-ttu-id="248f6-284">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-284">Int16</span></span>|  
|<span data-ttu-id="248f6-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="248f6-285">TYPE_NAME</span></span>|<span data-ttu-id="248f6-286">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-286">String</span></span>|  
|<span data-ttu-id="248f6-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="248f6-287">COLUMN_SIZE</span></span>|<span data-ttu-id="248f6-288">Int32</span><span class="sxs-lookup"><span data-stu-id="248f6-288">Int32</span></span>|  
|<span data-ttu-id="248f6-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="248f6-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="248f6-290">Int32</span><span class="sxs-lookup"><span data-stu-id="248f6-290">Int32</span></span>|  
|<span data-ttu-id="248f6-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="248f6-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="248f6-292">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-292">Int16</span></span>|  
|<span data-ttu-id="248f6-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="248f6-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="248f6-294">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-294">Int16</span></span>|  
|<span data-ttu-id="248f6-295">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="248f6-295">NULLABLE</span></span>|<span data-ttu-id="248f6-296">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-296">Int16</span></span>|  
|<span data-ttu-id="248f6-297">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="248f6-297">REMARKS</span></span>|<span data-ttu-id="248f6-298">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-298">String</span></span>|  
|<span data-ttu-id="248f6-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="248f6-299">COLUMN_DEF</span></span>|<span data-ttu-id="248f6-300">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-300">String</span></span>|  
|<span data-ttu-id="248f6-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="248f6-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="248f6-302">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-302">Int16</span></span>|  
|<span data-ttu-id="248f6-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="248f6-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="248f6-304">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-304">Int16</span></span>|  
|<span data-ttu-id="248f6-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="248f6-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="248f6-306">Int32</span><span class="sxs-lookup"><span data-stu-id="248f6-306">Int32</span></span>|  
|<span data-ttu-id="248f6-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="248f6-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="248f6-308">Int32</span><span class="sxs-lookup"><span data-stu-id="248f6-308">Int32</span></span>|  
|<span data-ttu-id="248f6-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="248f6-309">IS_NULLABLE</span></span>|<span data-ttu-id="248f6-310">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-310">String</span></span>|  
|<span data-ttu-id="248f6-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="248f6-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="248f6-312">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-312">String</span></span>|  
|<span data-ttu-id="248f6-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="248f6-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="248f6-314">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-314">String</span></span>|  
|<span data-ttu-id="248f6-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="248f6-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="248f6-316">Bayt</span><span class="sxs-lookup"><span data-stu-id="248f6-316">Byte</span></span>|  
  
## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="248f6-317">Microsoft Oracle ODBC sürücüsü</span><span class="sxs-lookup"><span data-stu-id="248f6-317">Microsoft Oracle ODBC Driver</span></span>  
 <span data-ttu-id="248f6-318">Microsoft SQL Server ve Oracle ODBC sürücüsü, ortak şema koleksiyonları ek olarak aşağıdaki belirli şema koleksiyonları destekler:</span><span class="sxs-lookup"><span data-stu-id="248f6-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="248f6-319">Tabloları</span><span class="sxs-lookup"><span data-stu-id="248f6-319">Tables</span></span>  
  
-   <span data-ttu-id="248f6-320">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="248f6-320">Columns</span></span>  
  
-   <span data-ttu-id="248f6-321">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="248f6-321">Procedures</span></span>  
  
-   <span data-ttu-id="248f6-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="248f6-322">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="248f6-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="248f6-323">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="248f6-324">Görünümler</span><span class="sxs-lookup"><span data-stu-id="248f6-324">Views</span></span>  
  
-   <span data-ttu-id="248f6-325">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="248f6-325">Indexes</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="248f6-326">Tabloları ve görünümleri</span><span class="sxs-lookup"><span data-stu-id="248f6-326">Tables and Views</span></span>  
  
|<span data-ttu-id="248f6-327">ColumnName</span><span class="sxs-lookup"><span data-stu-id="248f6-327">ColumnName</span></span>|<span data-ttu-id="248f6-328">Veri türü</span><span class="sxs-lookup"><span data-stu-id="248f6-328">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="248f6-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="248f6-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="248f6-330">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-330">String</span></span>|  
|<span data-ttu-id="248f6-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="248f6-331">TABLE_OWNER</span></span>|<span data-ttu-id="248f6-332">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-332">String</span></span>|  
|<span data-ttu-id="248f6-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="248f6-333">TABLE_NAME</span></span>|<span data-ttu-id="248f6-334">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-334">String</span></span>|  
|<span data-ttu-id="248f6-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="248f6-335">TABLE_TYPE</span></span>|<span data-ttu-id="248f6-336">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-336">String</span></span>|  
|<span data-ttu-id="248f6-337">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="248f6-337">REMARKS</span></span>|<span data-ttu-id="248f6-338">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-338">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="248f6-339">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="248f6-339">Columns</span></span>  
  
|<span data-ttu-id="248f6-340">ColumnName</span><span class="sxs-lookup"><span data-stu-id="248f6-340">ColumnName</span></span>|<span data-ttu-id="248f6-341">Veri türü</span><span class="sxs-lookup"><span data-stu-id="248f6-341">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="248f6-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="248f6-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="248f6-343">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-343">String</span></span>|  
|<span data-ttu-id="248f6-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="248f6-344">TABLE_OWNER</span></span>|<span data-ttu-id="248f6-345">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-345">String</span></span>|  
|<span data-ttu-id="248f6-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="248f6-346">TABLE_NAME</span></span>|<span data-ttu-id="248f6-347">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-347">String</span></span>|  
|<span data-ttu-id="248f6-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="248f6-348">COLUMN_NAME</span></span>|<span data-ttu-id="248f6-349">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-349">String</span></span>|  
|<span data-ttu-id="248f6-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="248f6-350">DATA_TYPE</span></span>|<span data-ttu-id="248f6-351">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-351">Int16</span></span>|  
|<span data-ttu-id="248f6-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="248f6-352">TYPE_NAME</span></span>|<span data-ttu-id="248f6-353">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-353">String</span></span>|  
|<span data-ttu-id="248f6-354">DUYARLIK</span><span class="sxs-lookup"><span data-stu-id="248f6-354">PRECISION</span></span>|<span data-ttu-id="248f6-355">Int32</span><span class="sxs-lookup"><span data-stu-id="248f6-355">Int32</span></span>|  
|<span data-ttu-id="248f6-356">UZUNLUĞU</span><span class="sxs-lookup"><span data-stu-id="248f6-356">LENGTH</span></span>|<span data-ttu-id="248f6-357">Int32</span><span class="sxs-lookup"><span data-stu-id="248f6-357">Int32</span></span>|  
|<span data-ttu-id="248f6-358">ÖLÇEK</span><span class="sxs-lookup"><span data-stu-id="248f6-358">SCALE</span></span>|<span data-ttu-id="248f6-359">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-359">Int16</span></span>|  
|<span data-ttu-id="248f6-360">SAYI TABANI</span><span class="sxs-lookup"><span data-stu-id="248f6-360">RADIX</span></span>|<span data-ttu-id="248f6-361">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-361">Int16</span></span>|  
|<span data-ttu-id="248f6-362">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="248f6-362">NULLABLE</span></span>|<span data-ttu-id="248f6-363">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-363">Int16</span></span>|  
|<span data-ttu-id="248f6-364">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="248f6-364">REMARKS</span></span>|<span data-ttu-id="248f6-365">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-365">String</span></span>|  
|<span data-ttu-id="248f6-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="248f6-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="248f6-367">Int32</span><span class="sxs-lookup"><span data-stu-id="248f6-367">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="248f6-368">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="248f6-368">Procedures</span></span>  
  
|<span data-ttu-id="248f6-369">ColumnName</span><span class="sxs-lookup"><span data-stu-id="248f6-369">ColumnName</span></span>|<span data-ttu-id="248f6-370">Veri türü</span><span class="sxs-lookup"><span data-stu-id="248f6-370">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="248f6-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="248f6-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="248f6-372">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-372">String</span></span>|  
|<span data-ttu-id="248f6-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="248f6-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="248f6-374">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-374">String</span></span>|  
|<span data-ttu-id="248f6-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="248f6-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="248f6-376">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-376">String</span></span>|  
|<span data-ttu-id="248f6-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="248f6-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="248f6-378">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-378">Int16</span></span>|  
|<span data-ttu-id="248f6-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="248f6-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="248f6-380">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-380">Int16</span></span>|  
|<span data-ttu-id="248f6-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="248f6-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="248f6-382">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-382">Int16</span></span>|  
|<span data-ttu-id="248f6-383">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="248f6-383">REMARKS</span></span>|<span data-ttu-id="248f6-384">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-384">String</span></span>|  
|<span data-ttu-id="248f6-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="248f6-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="248f6-386">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-386">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="248f6-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="248f6-387">ProcedureColumns</span></span>  
  
|<span data-ttu-id="248f6-388">ColumnName</span><span class="sxs-lookup"><span data-stu-id="248f6-388">ColumnName</span></span>|<span data-ttu-id="248f6-389">Veri türü</span><span class="sxs-lookup"><span data-stu-id="248f6-389">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="248f6-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="248f6-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="248f6-391">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-391">String</span></span>|  
|<span data-ttu-id="248f6-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="248f6-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="248f6-393">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-393">String</span></span>|  
|<span data-ttu-id="248f6-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="248f6-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="248f6-395">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-395">String</span></span>|  
|<span data-ttu-id="248f6-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="248f6-396">COLUMN_NAME</span></span>|<span data-ttu-id="248f6-397">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-397">String</span></span>|  
|<span data-ttu-id="248f6-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="248f6-398">COLUMN_TYPE</span></span>|<span data-ttu-id="248f6-399">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-399">Int16</span></span>|  
|<span data-ttu-id="248f6-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="248f6-400">DATA_TYPE</span></span>|<span data-ttu-id="248f6-401">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-401">Int16</span></span>|  
|<span data-ttu-id="248f6-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="248f6-402">TYPE_NAME</span></span>|<span data-ttu-id="248f6-403">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-403">String</span></span>|  
|<span data-ttu-id="248f6-404">DUYARLIK</span><span class="sxs-lookup"><span data-stu-id="248f6-404">PRECISION</span></span>|<span data-ttu-id="248f6-405">Int32</span><span class="sxs-lookup"><span data-stu-id="248f6-405">Int32</span></span>|  
|<span data-ttu-id="248f6-406">UZUNLUĞU</span><span class="sxs-lookup"><span data-stu-id="248f6-406">LENGTH</span></span>|<span data-ttu-id="248f6-407">Int32</span><span class="sxs-lookup"><span data-stu-id="248f6-407">Int32</span></span>|  
|<span data-ttu-id="248f6-408">ÖLÇEK</span><span class="sxs-lookup"><span data-stu-id="248f6-408">SCALE</span></span>|<span data-ttu-id="248f6-409">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-409">Int16</span></span>|  
|<span data-ttu-id="248f6-410">SAYI TABANI</span><span class="sxs-lookup"><span data-stu-id="248f6-410">RADIX</span></span>|<span data-ttu-id="248f6-411">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-411">Int16</span></span>|  
|<span data-ttu-id="248f6-412">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="248f6-412">NULLABLE</span></span>|<span data-ttu-id="248f6-413">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-413">Int16</span></span>|  
|<span data-ttu-id="248f6-414">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="248f6-414">REMARKS</span></span>|<span data-ttu-id="248f6-415">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-415">String</span></span>|  
|<span data-ttu-id="248f6-416">AŞIRI YÜKLEME</span><span class="sxs-lookup"><span data-stu-id="248f6-416">OVERLOAD</span></span>|<span data-ttu-id="248f6-417">Int32</span><span class="sxs-lookup"><span data-stu-id="248f6-417">Int32</span></span>|  
|<span data-ttu-id="248f6-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="248f6-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="248f6-419">Int32</span><span class="sxs-lookup"><span data-stu-id="248f6-419">Int32</span></span>|  
  
## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="248f6-420">Microsoft Jet ODBC sürücüsü</span><span class="sxs-lookup"><span data-stu-id="248f6-420">Microsoft Jet ODBC Driver</span></span>  
 <span data-ttu-id="248f6-421">Microsoft Jet ODBC sürücüsü, ortak şema koleksiyonları ek olarak aşağıdaki belirli şema koleksiyonları destekler:</span><span class="sxs-lookup"><span data-stu-id="248f6-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="248f6-422">Tabloları</span><span class="sxs-lookup"><span data-stu-id="248f6-422">Tables</span></span>  
  
-   <span data-ttu-id="248f6-423">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="248f6-423">Indexes</span></span>  
  
-   <span data-ttu-id="248f6-424">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="248f6-424">Columns</span></span>  
  
-   <span data-ttu-id="248f6-425">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="248f6-425">Procedures</span></span>  
  
-   <span data-ttu-id="248f6-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="248f6-426">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="248f6-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="248f6-427">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="248f6-428">Görünümler</span><span class="sxs-lookup"><span data-stu-id="248f6-428">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="248f6-429">Tabloları ve görünümleri</span><span class="sxs-lookup"><span data-stu-id="248f6-429">Tables and Views</span></span>  
  
|<span data-ttu-id="248f6-430">ColumnName</span><span class="sxs-lookup"><span data-stu-id="248f6-430">ColumnName</span></span>|<span data-ttu-id="248f6-431">Veri türü</span><span class="sxs-lookup"><span data-stu-id="248f6-431">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="248f6-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="248f6-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="248f6-433">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-433">String</span></span>|  
|<span data-ttu-id="248f6-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="248f6-434">TABLE_OWNER</span></span>|<span data-ttu-id="248f6-435">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-435">String</span></span>|  
|<span data-ttu-id="248f6-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="248f6-436">TABLE_NAME</span></span>|<span data-ttu-id="248f6-437">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-437">String</span></span>|  
|<span data-ttu-id="248f6-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="248f6-438">TABLE_TYPE</span></span>|<span data-ttu-id="248f6-439">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-439">String</span></span>|  
|<span data-ttu-id="248f6-440">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="248f6-440">REMARKS</span></span>|<span data-ttu-id="248f6-441">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-441">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="248f6-442">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="248f6-442">Columns</span></span>  
  
|<span data-ttu-id="248f6-443">ColumnName</span><span class="sxs-lookup"><span data-stu-id="248f6-443">ColumnName</span></span>|<span data-ttu-id="248f6-444">Veri türü</span><span class="sxs-lookup"><span data-stu-id="248f6-444">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="248f6-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="248f6-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="248f6-446">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-446">String</span></span>|  
|<span data-ttu-id="248f6-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="248f6-447">TABLE_OWNER</span></span>|<span data-ttu-id="248f6-448">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-448">String</span></span>|  
|<span data-ttu-id="248f6-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="248f6-449">TABLE_NAME</span></span>|<span data-ttu-id="248f6-450">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-450">String</span></span>|  
|<span data-ttu-id="248f6-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="248f6-451">COLUMN_NAME</span></span>|<span data-ttu-id="248f6-452">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-452">String</span></span>|  
|<span data-ttu-id="248f6-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="248f6-453">DATA_TYPE</span></span>|<span data-ttu-id="248f6-454">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-454">Int16</span></span>|  
|<span data-ttu-id="248f6-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="248f6-455">TYPE_NAME</span></span>|<span data-ttu-id="248f6-456">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-456">String</span></span>|  
|<span data-ttu-id="248f6-457">DUYARLIK</span><span class="sxs-lookup"><span data-stu-id="248f6-457">PRECISION</span></span>|<span data-ttu-id="248f6-458">Int32</span><span class="sxs-lookup"><span data-stu-id="248f6-458">Int32</span></span>|  
|<span data-ttu-id="248f6-459">UZUNLUĞU</span><span class="sxs-lookup"><span data-stu-id="248f6-459">LENGTH</span></span>|<span data-ttu-id="248f6-460">Int32</span><span class="sxs-lookup"><span data-stu-id="248f6-460">Int32</span></span>|  
|<span data-ttu-id="248f6-461">ÖLÇEK</span><span class="sxs-lookup"><span data-stu-id="248f6-461">SCALE</span></span>|<span data-ttu-id="248f6-462">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-462">Int16</span></span>|  
|<span data-ttu-id="248f6-463">SAYI TABANI</span><span class="sxs-lookup"><span data-stu-id="248f6-463">RADIX</span></span>|<span data-ttu-id="248f6-464">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-464">Int16</span></span>|  
|<span data-ttu-id="248f6-465">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="248f6-465">NULLABLE</span></span>|<span data-ttu-id="248f6-466">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-466">Int16</span></span>|  
|<span data-ttu-id="248f6-467">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="248f6-467">REMARKS</span></span>|<span data-ttu-id="248f6-468">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-468">String</span></span>|  
|<span data-ttu-id="248f6-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="248f6-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="248f6-470">Int32</span><span class="sxs-lookup"><span data-stu-id="248f6-470">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="248f6-471">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="248f6-471">Procedures</span></span>  
  
|<span data-ttu-id="248f6-472">ColumnName</span><span class="sxs-lookup"><span data-stu-id="248f6-472">ColumnName</span></span>|<span data-ttu-id="248f6-473">Veri türü</span><span class="sxs-lookup"><span data-stu-id="248f6-473">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="248f6-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="248f6-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="248f6-475">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-475">String</span></span>|  
|<span data-ttu-id="248f6-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="248f6-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="248f6-477">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-477">String</span></span>|  
|<span data-ttu-id="248f6-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="248f6-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="248f6-479">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-479">String</span></span>|  
|<span data-ttu-id="248f6-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="248f6-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="248f6-481">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-481">Int16</span></span>|  
|<span data-ttu-id="248f6-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="248f6-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="248f6-483">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-483">Int16</span></span>|  
|<span data-ttu-id="248f6-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="248f6-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="248f6-485">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-485">Int16</span></span>|  
|<span data-ttu-id="248f6-486">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="248f6-486">REMARKS</span></span>|<span data-ttu-id="248f6-487">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-487">String</span></span>|  
|<span data-ttu-id="248f6-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="248f6-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="248f6-489">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-489">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="248f6-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="248f6-490">ProcedureColumns</span></span>  
  
|<span data-ttu-id="248f6-491">ColumnName</span><span class="sxs-lookup"><span data-stu-id="248f6-491">ColumnName</span></span>|<span data-ttu-id="248f6-492">Veri türü</span><span class="sxs-lookup"><span data-stu-id="248f6-492">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="248f6-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="248f6-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="248f6-494">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-494">String</span></span>|  
|<span data-ttu-id="248f6-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="248f6-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="248f6-496">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-496">String</span></span>|  
|<span data-ttu-id="248f6-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="248f6-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="248f6-498">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-498">String</span></span>|  
|<span data-ttu-id="248f6-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="248f6-499">COLUMN_NAME</span></span>|<span data-ttu-id="248f6-500">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-500">String</span></span>|  
|<span data-ttu-id="248f6-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="248f6-501">COLUMN_TYPE</span></span>|<span data-ttu-id="248f6-502">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-502">Int16</span></span>|  
|<span data-ttu-id="248f6-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="248f6-503">DATA_TYPE</span></span>|<span data-ttu-id="248f6-504">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-504">Int16</span></span>|  
|<span data-ttu-id="248f6-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="248f6-505">TYPE_NAME</span></span>|<span data-ttu-id="248f6-506">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-506">String</span></span>|  
|<span data-ttu-id="248f6-507">DUYARLIK</span><span class="sxs-lookup"><span data-stu-id="248f6-507">PRECISION</span></span>|<span data-ttu-id="248f6-508">Int32</span><span class="sxs-lookup"><span data-stu-id="248f6-508">Int32</span></span>|  
|<span data-ttu-id="248f6-509">UZUNLUĞU</span><span class="sxs-lookup"><span data-stu-id="248f6-509">LENGTH</span></span>|<span data-ttu-id="248f6-510">Int32</span><span class="sxs-lookup"><span data-stu-id="248f6-510">Int32</span></span>|  
|<span data-ttu-id="248f6-511">ÖLÇEK</span><span class="sxs-lookup"><span data-stu-id="248f6-511">SCALE</span></span>|<span data-ttu-id="248f6-512">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-512">Int16</span></span>|  
|<span data-ttu-id="248f6-513">SAYI TABANI</span><span class="sxs-lookup"><span data-stu-id="248f6-513">RADIX</span></span>|<span data-ttu-id="248f6-514">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-514">Int16</span></span>|  
|<span data-ttu-id="248f6-515">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="248f6-515">NULLABLE</span></span>|<span data-ttu-id="248f6-516">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-516">Int16</span></span>|  
|<span data-ttu-id="248f6-517">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="248f6-517">REMARKS</span></span>|<span data-ttu-id="248f6-518">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-518">String</span></span>|  
|<span data-ttu-id="248f6-519">AŞIRI YÜKLEME</span><span class="sxs-lookup"><span data-stu-id="248f6-519">OVERLOAD</span></span>|<span data-ttu-id="248f6-520">Int32</span><span class="sxs-lookup"><span data-stu-id="248f6-520">Int32</span></span>|  
|<span data-ttu-id="248f6-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="248f6-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="248f6-522">Int32</span><span class="sxs-lookup"><span data-stu-id="248f6-522">Int32</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="248f6-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="248f6-523">ProcedureParameters</span></span>  
  
|<span data-ttu-id="248f6-524">ColumnName</span><span class="sxs-lookup"><span data-stu-id="248f6-524">ColumnName</span></span>|<span data-ttu-id="248f6-525">Veri türü</span><span class="sxs-lookup"><span data-stu-id="248f6-525">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="248f6-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="248f6-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="248f6-527">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-527">String</span></span>|  
|<span data-ttu-id="248f6-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="248f6-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="248f6-529">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-529">String</span></span>|  
|<span data-ttu-id="248f6-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="248f6-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="248f6-531">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-531">String</span></span>|  
|<span data-ttu-id="248f6-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="248f6-532">COLUMN_NAME</span></span>|<span data-ttu-id="248f6-533">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-533">String</span></span>|  
|<span data-ttu-id="248f6-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="248f6-534">COLUMN_TYPE</span></span>|<span data-ttu-id="248f6-535">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-535">Int16</span></span>|  
|<span data-ttu-id="248f6-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="248f6-536">DATA_TYPE</span></span>|<span data-ttu-id="248f6-537">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-537">Int16</span></span>|  
|<span data-ttu-id="248f6-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="248f6-538">TYPE_NAME</span></span>|<span data-ttu-id="248f6-539">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-539">String</span></span>|  
|<span data-ttu-id="248f6-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="248f6-540">COLUMN_SIZE</span></span>|<span data-ttu-id="248f6-541">Int32</span><span class="sxs-lookup"><span data-stu-id="248f6-541">Int32</span></span>|  
|<span data-ttu-id="248f6-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="248f6-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="248f6-543">Int32</span><span class="sxs-lookup"><span data-stu-id="248f6-543">Int32</span></span>|  
|<span data-ttu-id="248f6-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="248f6-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="248f6-545">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-545">Int16</span></span>|  
|<span data-ttu-id="248f6-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="248f6-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="248f6-547">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-547">Int16</span></span>|  
|<span data-ttu-id="248f6-548">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="248f6-548">NULLABLE</span></span>|<span data-ttu-id="248f6-549">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-549">Int16</span></span>|  
|<span data-ttu-id="248f6-550">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="248f6-550">REMARKS</span></span>|<span data-ttu-id="248f6-551">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-551">String</span></span>|  
|<span data-ttu-id="248f6-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="248f6-552">COLUMN_DEF</span></span>|<span data-ttu-id="248f6-553">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-553">String</span></span>|  
|<span data-ttu-id="248f6-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="248f6-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="248f6-555">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-555">Int16</span></span>|  
|<span data-ttu-id="248f6-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="248f6-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="248f6-557">Int16</span><span class="sxs-lookup"><span data-stu-id="248f6-557">Int16</span></span>|  
|<span data-ttu-id="248f6-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="248f6-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="248f6-559">Int32</span><span class="sxs-lookup"><span data-stu-id="248f6-559">Int32</span></span>|  
|<span data-ttu-id="248f6-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="248f6-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="248f6-561">Int32</span><span class="sxs-lookup"><span data-stu-id="248f6-561">Int32</span></span>|  
|<span data-ttu-id="248f6-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="248f6-562">IS_NULLABLE</span></span>|<span data-ttu-id="248f6-563">Dize</span><span class="sxs-lookup"><span data-stu-id="248f6-563">String</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="248f6-564">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="248f6-564">See Also</span></span>  
 [<span data-ttu-id="248f6-565">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="248f6-565">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
