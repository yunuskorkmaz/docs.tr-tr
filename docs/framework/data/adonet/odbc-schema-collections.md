---
title: ODBC şema koleksiyonları
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: bdedbb11960f02b99dcca6388abf663635238f74
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43877537"
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="e6f56-102">ODBC şema koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="e6f56-102">ODBC Schema Collections</span></span>
<span data-ttu-id="e6f56-103">Bu bölümde, Microsoft SQL Server, Oracle ve Microsoft Jet ODBC sürücüleri için şema koleksiyonu desteği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e6f56-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="e6f56-104">Microsoft SQL Server ODBC sürücüsü</span><span class="sxs-lookup"><span data-stu-id="e6f56-104">Microsoft SQL Server ODBC Driver</span></span>  
 <span data-ttu-id="e6f56-105">Microsoft SQL Server ODBC sürücüsü, ortak şema koleksiyonları ek olarak aşağıdaki belirli şema koleksiyonları destekler:</span><span class="sxs-lookup"><span data-stu-id="e6f56-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="e6f56-106">Tabloları</span><span class="sxs-lookup"><span data-stu-id="e6f56-106">Tables</span></span>  
  
-   <span data-ttu-id="e6f56-107">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="e6f56-107">Indexes</span></span>  
  
-   <span data-ttu-id="e6f56-108">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="e6f56-108">Columns</span></span>  
  
-   <span data-ttu-id="e6f56-109">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="e6f56-109">Procedures</span></span>  
  
-   <span data-ttu-id="e6f56-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="e6f56-110">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="e6f56-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="e6f56-111">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="e6f56-112">Görünümler</span><span class="sxs-lookup"><span data-stu-id="e6f56-112">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="e6f56-113">Tabloları ve görünümleri</span><span class="sxs-lookup"><span data-stu-id="e6f56-113">Tables and Views</span></span>  
  
|<span data-ttu-id="e6f56-114">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e6f56-114">ColumnName</span></span>|<span data-ttu-id="e6f56-115">Veri türü</span><span class="sxs-lookup"><span data-stu-id="e6f56-115">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e6f56-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="e6f56-116">TABLE_CAT</span></span>|<span data-ttu-id="e6f56-117">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-117">String</span></span>|  
|<span data-ttu-id="e6f56-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="e6f56-118">TABLE_SCHEM</span></span>|<span data-ttu-id="e6f56-119">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-119">String</span></span>|  
|<span data-ttu-id="e6f56-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e6f56-120">TABLE_NAME</span></span>|<span data-ttu-id="e6f56-121">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-121">String</span></span>|  
|<span data-ttu-id="e6f56-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6f56-122">TABLE_TYPE</span></span>|<span data-ttu-id="e6f56-123">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-123">String</span></span>|  
|<span data-ttu-id="e6f56-124">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="e6f56-124">REMARKS</span></span>|<span data-ttu-id="e6f56-125">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-125">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="e6f56-126">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="e6f56-126">Indexes</span></span>  
  
|<span data-ttu-id="e6f56-127">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e6f56-127">ColumnName</span></span>|<span data-ttu-id="e6f56-128">Veri türü</span><span class="sxs-lookup"><span data-stu-id="e6f56-128">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e6f56-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="e6f56-129">TABLE_CAT</span></span>|<span data-ttu-id="e6f56-130">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-130">String</span></span>|  
|<span data-ttu-id="e6f56-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="e6f56-131">TABLE_SCHEM</span></span>|<span data-ttu-id="e6f56-132">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-132">String</span></span>|  
|<span data-ttu-id="e6f56-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e6f56-133">TABLE_NAME</span></span>|<span data-ttu-id="e6f56-134">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-134">String</span></span>|  
|<span data-ttu-id="e6f56-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="e6f56-135">NON_UNIQUE</span></span>|<span data-ttu-id="e6f56-136">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-136">Int16</span></span>|  
|<span data-ttu-id="e6f56-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="e6f56-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="e6f56-138">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-138">String</span></span>|  
|<span data-ttu-id="e6f56-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="e6f56-139">INDEX_NAME</span></span>|<span data-ttu-id="e6f56-140">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-140">String</span></span>|  
|<span data-ttu-id="e6f56-141">TÜRÜ</span><span class="sxs-lookup"><span data-stu-id="e6f56-141">TYPE</span></span>|<span data-ttu-id="e6f56-142">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-142">Int16</span></span>|  
|<span data-ttu-id="e6f56-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e6f56-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="e6f56-144">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-144">Int16</span></span>|  
|<span data-ttu-id="e6f56-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e6f56-145">COLUMN_NAME</span></span>|<span data-ttu-id="e6f56-146">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-146">String</span></span>|  
|<span data-ttu-id="e6f56-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="e6f56-147">ASC_OR_DESC</span></span>|<span data-ttu-id="e6f56-148">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-148">String</span></span>|  
|<span data-ttu-id="e6f56-149">CARDINATLITY</span><span class="sxs-lookup"><span data-stu-id="e6f56-149">CARDINATLITY</span></span>|<span data-ttu-id="e6f56-150">Int32</span><span class="sxs-lookup"><span data-stu-id="e6f56-150">Int32</span></span>|  
|<span data-ttu-id="e6f56-151">SAYFALARI</span><span class="sxs-lookup"><span data-stu-id="e6f56-151">PAGES</span></span>|<span data-ttu-id="e6f56-152">Int32</span><span class="sxs-lookup"><span data-stu-id="e6f56-152">Int32</span></span>|  
|<span data-ttu-id="e6f56-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="e6f56-153">FILTER_CONDITION</span></span>|<span data-ttu-id="e6f56-154">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-154">String</span></span>|  
|<span data-ttu-id="e6f56-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e6f56-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="e6f56-156">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-156">String</span></span>|  
|<span data-ttu-id="e6f56-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6f56-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="e6f56-158">Bayt</span><span class="sxs-lookup"><span data-stu-id="e6f56-158">Byte</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="e6f56-159">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="e6f56-159">Columns</span></span>  
  
|<span data-ttu-id="e6f56-160">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e6f56-160">ColumnName</span></span>|<span data-ttu-id="e6f56-161">Veri türü</span><span class="sxs-lookup"><span data-stu-id="e6f56-161">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e6f56-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="e6f56-162">TABLE_CAT</span></span>|<span data-ttu-id="e6f56-163">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-163">String</span></span>|  
|<span data-ttu-id="e6f56-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="e6f56-164">TABLE_SCHEM</span></span>|<span data-ttu-id="e6f56-165">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-165">String</span></span>|  
|<span data-ttu-id="e6f56-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e6f56-166">TABLE_NAME</span></span>|<span data-ttu-id="e6f56-167">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-167">String</span></span>|  
|<span data-ttu-id="e6f56-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e6f56-168">COLUMN_NAME</span></span>|<span data-ttu-id="e6f56-169">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-169">String</span></span>|  
|<span data-ttu-id="e6f56-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6f56-170">DATA_TYPE</span></span>|<span data-ttu-id="e6f56-171">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-171">Int16</span></span>|  
|<span data-ttu-id="e6f56-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="e6f56-172">TYPE_NAME</span></span>|<span data-ttu-id="e6f56-173">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-173">String</span></span>|  
|<span data-ttu-id="e6f56-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="e6f56-174">COLUMN_SIZE</span></span>|<span data-ttu-id="e6f56-175">Int32</span><span class="sxs-lookup"><span data-stu-id="e6f56-175">Int32</span></span>|  
|<span data-ttu-id="e6f56-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e6f56-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="e6f56-177">Int32</span><span class="sxs-lookup"><span data-stu-id="e6f56-177">Int32</span></span>|  
|<span data-ttu-id="e6f56-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="e6f56-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="e6f56-179">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-179">Int16</span></span>|  
|<span data-ttu-id="e6f56-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="e6f56-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="e6f56-181">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-181">Int16</span></span>|  
|<span data-ttu-id="e6f56-182">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="e6f56-182">NULLABLE</span></span>|<span data-ttu-id="e6f56-183">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-183">Int16</span></span>|  
|<span data-ttu-id="e6f56-184">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="e6f56-184">REMARKS</span></span>|<span data-ttu-id="e6f56-185">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-185">String</span></span>|  
|<span data-ttu-id="e6f56-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="e6f56-186">COLUMN_DEF</span></span>|<span data-ttu-id="e6f56-187">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-187">String</span></span>|  
|<span data-ttu-id="e6f56-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6f56-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="e6f56-189">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-189">Int16</span></span>|  
|<span data-ttu-id="e6f56-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="e6f56-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="e6f56-191">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-191">Int16</span></span>|  
|<span data-ttu-id="e6f56-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e6f56-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="e6f56-193">Int32</span><span class="sxs-lookup"><span data-stu-id="e6f56-193">Int32</span></span>|  
|<span data-ttu-id="e6f56-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e6f56-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="e6f56-195">Int32</span><span class="sxs-lookup"><span data-stu-id="e6f56-195">Int32</span></span>|  
|<span data-ttu-id="e6f56-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="e6f56-196">IS_NULLABLE</span></span>|<span data-ttu-id="e6f56-197">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-197">String</span></span>|  
|<span data-ttu-id="e6f56-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e6f56-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="e6f56-199">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-199">String</span></span>|  
|<span data-ttu-id="e6f56-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e6f56-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="e6f56-201">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-201">String</span></span>|  
|<span data-ttu-id="e6f56-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6f56-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="e6f56-203">Bayt</span><span class="sxs-lookup"><span data-stu-id="e6f56-203">Byte</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="e6f56-204">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="e6f56-204">Procedures</span></span>  
  
|<span data-ttu-id="e6f56-205">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e6f56-205">ColumnName</span></span>|<span data-ttu-id="e6f56-206">Veri türü</span><span class="sxs-lookup"><span data-stu-id="e6f56-206">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e6f56-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="e6f56-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="e6f56-208">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-208">String</span></span>|  
|<span data-ttu-id="e6f56-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="e6f56-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="e6f56-210">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-210">String</span></span>|  
|<span data-ttu-id="e6f56-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="e6f56-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="e6f56-212">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-212">String</span></span>|  
|<span data-ttu-id="e6f56-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="e6f56-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="e6f56-214">Int32</span><span class="sxs-lookup"><span data-stu-id="e6f56-214">Int32</span></span>|  
|<span data-ttu-id="e6f56-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="e6f56-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="e6f56-216">Int32</span><span class="sxs-lookup"><span data-stu-id="e6f56-216">Int32</span></span>|  
|<span data-ttu-id="e6f56-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="e6f56-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="e6f56-218">Int32</span><span class="sxs-lookup"><span data-stu-id="e6f56-218">Int32</span></span>|  
|<span data-ttu-id="e6f56-219">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="e6f56-219">REMARKS</span></span>|<span data-ttu-id="e6f56-220">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-220">String</span></span>|  
|<span data-ttu-id="e6f56-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6f56-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="e6f56-222">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-222">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="e6f56-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="e6f56-223">ProcedureColumns</span></span>  
  
|<span data-ttu-id="e6f56-224">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e6f56-224">ColumnName</span></span>|<span data-ttu-id="e6f56-225">Veri türü</span><span class="sxs-lookup"><span data-stu-id="e6f56-225">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e6f56-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="e6f56-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="e6f56-227">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-227">String</span></span>|  
|<span data-ttu-id="e6f56-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="e6f56-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="e6f56-229">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-229">String</span></span>|  
|<span data-ttu-id="e6f56-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="e6f56-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="e6f56-231">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-231">String</span></span>|  
|<span data-ttu-id="e6f56-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e6f56-232">COLUMN_NAME</span></span>|<span data-ttu-id="e6f56-233">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-233">String</span></span>|  
|<span data-ttu-id="e6f56-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6f56-234">COLUMN_TYPE</span></span>|<span data-ttu-id="e6f56-235">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-235">Int16</span></span>|  
|<span data-ttu-id="e6f56-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6f56-236">DATA_TYPE</span></span>|<span data-ttu-id="e6f56-237">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-237">Int16</span></span>|  
|<span data-ttu-id="e6f56-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="e6f56-238">TYPE_NAME</span></span>|<span data-ttu-id="e6f56-239">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-239">String</span></span>|  
|<span data-ttu-id="e6f56-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="e6f56-240">COLUMN_SIZE</span></span>|<span data-ttu-id="e6f56-241">Int32</span><span class="sxs-lookup"><span data-stu-id="e6f56-241">Int32</span></span>|  
|<span data-ttu-id="e6f56-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e6f56-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="e6f56-243">Int32</span><span class="sxs-lookup"><span data-stu-id="e6f56-243">Int32</span></span>|  
|<span data-ttu-id="e6f56-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="e6f56-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="e6f56-245">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-245">Int16</span></span>|  
|<span data-ttu-id="e6f56-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="e6f56-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="e6f56-247">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-247">Int16</span></span>|  
|<span data-ttu-id="e6f56-248">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="e6f56-248">NULLABLE</span></span>|<span data-ttu-id="e6f56-249">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-249">Int16</span></span>|  
|<span data-ttu-id="e6f56-250">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="e6f56-250">REMARKS</span></span>|<span data-ttu-id="e6f56-251">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-251">String</span></span>|  
|<span data-ttu-id="e6f56-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="e6f56-252">COLUMN_DEF</span></span>|<span data-ttu-id="e6f56-253">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-253">String</span></span>|  
|<span data-ttu-id="e6f56-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6f56-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="e6f56-255">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-255">Int16</span></span>|  
|<span data-ttu-id="e6f56-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="e6f56-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="e6f56-257">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-257">Int16</span></span>|  
|<span data-ttu-id="e6f56-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e6f56-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="e6f56-259">Int32</span><span class="sxs-lookup"><span data-stu-id="e6f56-259">Int32</span></span>|  
|<span data-ttu-id="e6f56-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e6f56-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="e6f56-261">Int32</span><span class="sxs-lookup"><span data-stu-id="e6f56-261">Int32</span></span>|  
|<span data-ttu-id="e6f56-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="e6f56-262">IS_NULLABLE</span></span>|<span data-ttu-id="e6f56-263">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-263">String</span></span>|  
|<span data-ttu-id="e6f56-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e6f56-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="e6f56-265">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-265">String</span></span>|  
|<span data-ttu-id="e6f56-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e6f56-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="e6f56-267">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-267">String</span></span>|  
|<span data-ttu-id="e6f56-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6f56-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="e6f56-269">Bayt</span><span class="sxs-lookup"><span data-stu-id="e6f56-269">Byte</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="e6f56-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="e6f56-270">ProcedureParameters</span></span>  
  
|<span data-ttu-id="e6f56-271">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e6f56-271">ColumnName</span></span>|<span data-ttu-id="e6f56-272">Veri türü</span><span class="sxs-lookup"><span data-stu-id="e6f56-272">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e6f56-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="e6f56-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="e6f56-274">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-274">String</span></span>|  
|<span data-ttu-id="e6f56-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="e6f56-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="e6f56-276">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-276">String</span></span>|  
|<span data-ttu-id="e6f56-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="e6f56-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="e6f56-278">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-278">String</span></span>|  
|<span data-ttu-id="e6f56-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e6f56-279">COLUMN_NAME</span></span>|<span data-ttu-id="e6f56-280">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-280">String</span></span>|  
|<span data-ttu-id="e6f56-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6f56-281">COLUMN_TYPE</span></span>|<span data-ttu-id="e6f56-282">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-282">Int16</span></span>|  
|<span data-ttu-id="e6f56-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6f56-283">DATA_TYPE</span></span>|<span data-ttu-id="e6f56-284">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-284">Int16</span></span>|  
|<span data-ttu-id="e6f56-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="e6f56-285">TYPE_NAME</span></span>|<span data-ttu-id="e6f56-286">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-286">String</span></span>|  
|<span data-ttu-id="e6f56-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="e6f56-287">COLUMN_SIZE</span></span>|<span data-ttu-id="e6f56-288">Int32</span><span class="sxs-lookup"><span data-stu-id="e6f56-288">Int32</span></span>|  
|<span data-ttu-id="e6f56-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e6f56-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="e6f56-290">Int32</span><span class="sxs-lookup"><span data-stu-id="e6f56-290">Int32</span></span>|  
|<span data-ttu-id="e6f56-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="e6f56-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="e6f56-292">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-292">Int16</span></span>|  
|<span data-ttu-id="e6f56-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="e6f56-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="e6f56-294">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-294">Int16</span></span>|  
|<span data-ttu-id="e6f56-295">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="e6f56-295">NULLABLE</span></span>|<span data-ttu-id="e6f56-296">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-296">Int16</span></span>|  
|<span data-ttu-id="e6f56-297">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="e6f56-297">REMARKS</span></span>|<span data-ttu-id="e6f56-298">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-298">String</span></span>|  
|<span data-ttu-id="e6f56-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="e6f56-299">COLUMN_DEF</span></span>|<span data-ttu-id="e6f56-300">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-300">String</span></span>|  
|<span data-ttu-id="e6f56-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6f56-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="e6f56-302">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-302">Int16</span></span>|  
|<span data-ttu-id="e6f56-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="e6f56-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="e6f56-304">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-304">Int16</span></span>|  
|<span data-ttu-id="e6f56-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e6f56-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="e6f56-306">Int32</span><span class="sxs-lookup"><span data-stu-id="e6f56-306">Int32</span></span>|  
|<span data-ttu-id="e6f56-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e6f56-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="e6f56-308">Int32</span><span class="sxs-lookup"><span data-stu-id="e6f56-308">Int32</span></span>|  
|<span data-ttu-id="e6f56-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="e6f56-309">IS_NULLABLE</span></span>|<span data-ttu-id="e6f56-310">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-310">String</span></span>|  
|<span data-ttu-id="e6f56-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e6f56-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="e6f56-312">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-312">String</span></span>|  
|<span data-ttu-id="e6f56-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e6f56-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="e6f56-314">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-314">String</span></span>|  
|<span data-ttu-id="e6f56-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6f56-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="e6f56-316">Bayt</span><span class="sxs-lookup"><span data-stu-id="e6f56-316">Byte</span></span>|  
  
## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="e6f56-317">Microsoft Oracle ODBC sürücüsü</span><span class="sxs-lookup"><span data-stu-id="e6f56-317">Microsoft Oracle ODBC Driver</span></span>  
 <span data-ttu-id="e6f56-318">Microsoft SQL Server ve Oracle ODBC sürücüsü, ortak şema koleksiyonları ek olarak aşağıdaki belirli şema koleksiyonları destekler:</span><span class="sxs-lookup"><span data-stu-id="e6f56-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="e6f56-319">Tabloları</span><span class="sxs-lookup"><span data-stu-id="e6f56-319">Tables</span></span>  
  
-   <span data-ttu-id="e6f56-320">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="e6f56-320">Columns</span></span>  
  
-   <span data-ttu-id="e6f56-321">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="e6f56-321">Procedures</span></span>  
  
-   <span data-ttu-id="e6f56-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="e6f56-322">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="e6f56-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="e6f56-323">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="e6f56-324">Görünümler</span><span class="sxs-lookup"><span data-stu-id="e6f56-324">Views</span></span>  
  
-   <span data-ttu-id="e6f56-325">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="e6f56-325">Indexes</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="e6f56-326">Tabloları ve görünümleri</span><span class="sxs-lookup"><span data-stu-id="e6f56-326">Tables and Views</span></span>  
  
|<span data-ttu-id="e6f56-327">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e6f56-327">ColumnName</span></span>|<span data-ttu-id="e6f56-328">Veri türü</span><span class="sxs-lookup"><span data-stu-id="e6f56-328">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e6f56-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="e6f56-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="e6f56-330">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-330">String</span></span>|  
|<span data-ttu-id="e6f56-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="e6f56-331">TABLE_OWNER</span></span>|<span data-ttu-id="e6f56-332">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-332">String</span></span>|  
|<span data-ttu-id="e6f56-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e6f56-333">TABLE_NAME</span></span>|<span data-ttu-id="e6f56-334">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-334">String</span></span>|  
|<span data-ttu-id="e6f56-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6f56-335">TABLE_TYPE</span></span>|<span data-ttu-id="e6f56-336">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-336">String</span></span>|  
|<span data-ttu-id="e6f56-337">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="e6f56-337">REMARKS</span></span>|<span data-ttu-id="e6f56-338">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-338">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="e6f56-339">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="e6f56-339">Columns</span></span>  
  
|<span data-ttu-id="e6f56-340">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e6f56-340">ColumnName</span></span>|<span data-ttu-id="e6f56-341">Veri türü</span><span class="sxs-lookup"><span data-stu-id="e6f56-341">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e6f56-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="e6f56-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="e6f56-343">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-343">String</span></span>|  
|<span data-ttu-id="e6f56-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="e6f56-344">TABLE_OWNER</span></span>|<span data-ttu-id="e6f56-345">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-345">String</span></span>|  
|<span data-ttu-id="e6f56-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e6f56-346">TABLE_NAME</span></span>|<span data-ttu-id="e6f56-347">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-347">String</span></span>|  
|<span data-ttu-id="e6f56-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e6f56-348">COLUMN_NAME</span></span>|<span data-ttu-id="e6f56-349">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-349">String</span></span>|  
|<span data-ttu-id="e6f56-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6f56-350">DATA_TYPE</span></span>|<span data-ttu-id="e6f56-351">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-351">Int16</span></span>|  
|<span data-ttu-id="e6f56-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="e6f56-352">TYPE_NAME</span></span>|<span data-ttu-id="e6f56-353">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-353">String</span></span>|  
|<span data-ttu-id="e6f56-354">DUYARLIK</span><span class="sxs-lookup"><span data-stu-id="e6f56-354">PRECISION</span></span>|<span data-ttu-id="e6f56-355">Int32</span><span class="sxs-lookup"><span data-stu-id="e6f56-355">Int32</span></span>|  
|<span data-ttu-id="e6f56-356">UZUNLUĞU</span><span class="sxs-lookup"><span data-stu-id="e6f56-356">LENGTH</span></span>|<span data-ttu-id="e6f56-357">Int32</span><span class="sxs-lookup"><span data-stu-id="e6f56-357">Int32</span></span>|  
|<span data-ttu-id="e6f56-358">ÖLÇEK</span><span class="sxs-lookup"><span data-stu-id="e6f56-358">SCALE</span></span>|<span data-ttu-id="e6f56-359">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-359">Int16</span></span>|  
|<span data-ttu-id="e6f56-360">SAYI TABANI</span><span class="sxs-lookup"><span data-stu-id="e6f56-360">RADIX</span></span>|<span data-ttu-id="e6f56-361">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-361">Int16</span></span>|  
|<span data-ttu-id="e6f56-362">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="e6f56-362">NULLABLE</span></span>|<span data-ttu-id="e6f56-363">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-363">Int16</span></span>|  
|<span data-ttu-id="e6f56-364">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="e6f56-364">REMARKS</span></span>|<span data-ttu-id="e6f56-365">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-365">String</span></span>|  
|<span data-ttu-id="e6f56-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e6f56-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="e6f56-367">Int32</span><span class="sxs-lookup"><span data-stu-id="e6f56-367">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="e6f56-368">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="e6f56-368">Procedures</span></span>  
  
|<span data-ttu-id="e6f56-369">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e6f56-369">ColumnName</span></span>|<span data-ttu-id="e6f56-370">Veri türü</span><span class="sxs-lookup"><span data-stu-id="e6f56-370">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e6f56-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="e6f56-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="e6f56-372">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-372">String</span></span>|  
|<span data-ttu-id="e6f56-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="e6f56-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="e6f56-374">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-374">String</span></span>|  
|<span data-ttu-id="e6f56-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="e6f56-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="e6f56-376">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-376">String</span></span>|  
|<span data-ttu-id="e6f56-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="e6f56-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="e6f56-378">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-378">Int16</span></span>|  
|<span data-ttu-id="e6f56-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="e6f56-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="e6f56-380">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-380">Int16</span></span>|  
|<span data-ttu-id="e6f56-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="e6f56-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="e6f56-382">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-382">Int16</span></span>|  
|<span data-ttu-id="e6f56-383">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="e6f56-383">REMARKS</span></span>|<span data-ttu-id="e6f56-384">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-384">String</span></span>|  
|<span data-ttu-id="e6f56-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6f56-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="e6f56-386">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-386">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="e6f56-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="e6f56-387">ProcedureColumns</span></span>  
  
|<span data-ttu-id="e6f56-388">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e6f56-388">ColumnName</span></span>|<span data-ttu-id="e6f56-389">Veri türü</span><span class="sxs-lookup"><span data-stu-id="e6f56-389">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e6f56-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="e6f56-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="e6f56-391">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-391">String</span></span>|  
|<span data-ttu-id="e6f56-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="e6f56-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="e6f56-393">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-393">String</span></span>|  
|<span data-ttu-id="e6f56-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="e6f56-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="e6f56-395">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-395">String</span></span>|  
|<span data-ttu-id="e6f56-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e6f56-396">COLUMN_NAME</span></span>|<span data-ttu-id="e6f56-397">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-397">String</span></span>|  
|<span data-ttu-id="e6f56-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6f56-398">COLUMN_TYPE</span></span>|<span data-ttu-id="e6f56-399">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-399">Int16</span></span>|  
|<span data-ttu-id="e6f56-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6f56-400">DATA_TYPE</span></span>|<span data-ttu-id="e6f56-401">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-401">Int16</span></span>|  
|<span data-ttu-id="e6f56-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="e6f56-402">TYPE_NAME</span></span>|<span data-ttu-id="e6f56-403">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-403">String</span></span>|  
|<span data-ttu-id="e6f56-404">DUYARLIK</span><span class="sxs-lookup"><span data-stu-id="e6f56-404">PRECISION</span></span>|<span data-ttu-id="e6f56-405">Int32</span><span class="sxs-lookup"><span data-stu-id="e6f56-405">Int32</span></span>|  
|<span data-ttu-id="e6f56-406">UZUNLUĞU</span><span class="sxs-lookup"><span data-stu-id="e6f56-406">LENGTH</span></span>|<span data-ttu-id="e6f56-407">Int32</span><span class="sxs-lookup"><span data-stu-id="e6f56-407">Int32</span></span>|  
|<span data-ttu-id="e6f56-408">ÖLÇEK</span><span class="sxs-lookup"><span data-stu-id="e6f56-408">SCALE</span></span>|<span data-ttu-id="e6f56-409">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-409">Int16</span></span>|  
|<span data-ttu-id="e6f56-410">SAYI TABANI</span><span class="sxs-lookup"><span data-stu-id="e6f56-410">RADIX</span></span>|<span data-ttu-id="e6f56-411">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-411">Int16</span></span>|  
|<span data-ttu-id="e6f56-412">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="e6f56-412">NULLABLE</span></span>|<span data-ttu-id="e6f56-413">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-413">Int16</span></span>|  
|<span data-ttu-id="e6f56-414">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="e6f56-414">REMARKS</span></span>|<span data-ttu-id="e6f56-415">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-415">String</span></span>|  
|<span data-ttu-id="e6f56-416">AŞIRI YÜKLEME</span><span class="sxs-lookup"><span data-stu-id="e6f56-416">OVERLOAD</span></span>|<span data-ttu-id="e6f56-417">Int32</span><span class="sxs-lookup"><span data-stu-id="e6f56-417">Int32</span></span>|  
|<span data-ttu-id="e6f56-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e6f56-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="e6f56-419">Int32</span><span class="sxs-lookup"><span data-stu-id="e6f56-419">Int32</span></span>|  
  
## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="e6f56-420">Microsoft Jet ODBC sürücüsü</span><span class="sxs-lookup"><span data-stu-id="e6f56-420">Microsoft Jet ODBC Driver</span></span>  
 <span data-ttu-id="e6f56-421">Microsoft Jet ODBC sürücüsü, ortak şema koleksiyonları ek olarak aşağıdaki belirli şema koleksiyonları destekler:</span><span class="sxs-lookup"><span data-stu-id="e6f56-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="e6f56-422">Tabloları</span><span class="sxs-lookup"><span data-stu-id="e6f56-422">Tables</span></span>  
  
-   <span data-ttu-id="e6f56-423">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="e6f56-423">Indexes</span></span>  
  
-   <span data-ttu-id="e6f56-424">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="e6f56-424">Columns</span></span>  
  
-   <span data-ttu-id="e6f56-425">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="e6f56-425">Procedures</span></span>  
  
-   <span data-ttu-id="e6f56-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="e6f56-426">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="e6f56-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="e6f56-427">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="e6f56-428">Görünümler</span><span class="sxs-lookup"><span data-stu-id="e6f56-428">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="e6f56-429">Tabloları ve görünümleri</span><span class="sxs-lookup"><span data-stu-id="e6f56-429">Tables and Views</span></span>  
  
|<span data-ttu-id="e6f56-430">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e6f56-430">ColumnName</span></span>|<span data-ttu-id="e6f56-431">Veri türü</span><span class="sxs-lookup"><span data-stu-id="e6f56-431">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e6f56-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="e6f56-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="e6f56-433">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-433">String</span></span>|  
|<span data-ttu-id="e6f56-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="e6f56-434">TABLE_OWNER</span></span>|<span data-ttu-id="e6f56-435">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-435">String</span></span>|  
|<span data-ttu-id="e6f56-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e6f56-436">TABLE_NAME</span></span>|<span data-ttu-id="e6f56-437">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-437">String</span></span>|  
|<span data-ttu-id="e6f56-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6f56-438">TABLE_TYPE</span></span>|<span data-ttu-id="e6f56-439">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-439">String</span></span>|  
|<span data-ttu-id="e6f56-440">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="e6f56-440">REMARKS</span></span>|<span data-ttu-id="e6f56-441">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-441">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="e6f56-442">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="e6f56-442">Columns</span></span>  
  
|<span data-ttu-id="e6f56-443">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e6f56-443">ColumnName</span></span>|<span data-ttu-id="e6f56-444">Veri türü</span><span class="sxs-lookup"><span data-stu-id="e6f56-444">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e6f56-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="e6f56-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="e6f56-446">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-446">String</span></span>|  
|<span data-ttu-id="e6f56-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="e6f56-447">TABLE_OWNER</span></span>|<span data-ttu-id="e6f56-448">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-448">String</span></span>|  
|<span data-ttu-id="e6f56-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e6f56-449">TABLE_NAME</span></span>|<span data-ttu-id="e6f56-450">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-450">String</span></span>|  
|<span data-ttu-id="e6f56-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e6f56-451">COLUMN_NAME</span></span>|<span data-ttu-id="e6f56-452">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-452">String</span></span>|  
|<span data-ttu-id="e6f56-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6f56-453">DATA_TYPE</span></span>|<span data-ttu-id="e6f56-454">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-454">Int16</span></span>|  
|<span data-ttu-id="e6f56-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="e6f56-455">TYPE_NAME</span></span>|<span data-ttu-id="e6f56-456">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-456">String</span></span>|  
|<span data-ttu-id="e6f56-457">DUYARLIK</span><span class="sxs-lookup"><span data-stu-id="e6f56-457">PRECISION</span></span>|<span data-ttu-id="e6f56-458">Int32</span><span class="sxs-lookup"><span data-stu-id="e6f56-458">Int32</span></span>|  
|<span data-ttu-id="e6f56-459">UZUNLUĞU</span><span class="sxs-lookup"><span data-stu-id="e6f56-459">LENGTH</span></span>|<span data-ttu-id="e6f56-460">Int32</span><span class="sxs-lookup"><span data-stu-id="e6f56-460">Int32</span></span>|  
|<span data-ttu-id="e6f56-461">ÖLÇEK</span><span class="sxs-lookup"><span data-stu-id="e6f56-461">SCALE</span></span>|<span data-ttu-id="e6f56-462">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-462">Int16</span></span>|  
|<span data-ttu-id="e6f56-463">SAYI TABANI</span><span class="sxs-lookup"><span data-stu-id="e6f56-463">RADIX</span></span>|<span data-ttu-id="e6f56-464">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-464">Int16</span></span>|  
|<span data-ttu-id="e6f56-465">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="e6f56-465">NULLABLE</span></span>|<span data-ttu-id="e6f56-466">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-466">Int16</span></span>|  
|<span data-ttu-id="e6f56-467">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="e6f56-467">REMARKS</span></span>|<span data-ttu-id="e6f56-468">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-468">String</span></span>|  
|<span data-ttu-id="e6f56-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e6f56-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="e6f56-470">Int32</span><span class="sxs-lookup"><span data-stu-id="e6f56-470">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="e6f56-471">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="e6f56-471">Procedures</span></span>  
  
|<span data-ttu-id="e6f56-472">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e6f56-472">ColumnName</span></span>|<span data-ttu-id="e6f56-473">Veri türü</span><span class="sxs-lookup"><span data-stu-id="e6f56-473">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e6f56-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="e6f56-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="e6f56-475">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-475">String</span></span>|  
|<span data-ttu-id="e6f56-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="e6f56-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="e6f56-477">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-477">String</span></span>|  
|<span data-ttu-id="e6f56-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="e6f56-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="e6f56-479">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-479">String</span></span>|  
|<span data-ttu-id="e6f56-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="e6f56-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="e6f56-481">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-481">Int16</span></span>|  
|<span data-ttu-id="e6f56-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="e6f56-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="e6f56-483">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-483">Int16</span></span>|  
|<span data-ttu-id="e6f56-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="e6f56-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="e6f56-485">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-485">Int16</span></span>|  
|<span data-ttu-id="e6f56-486">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="e6f56-486">REMARKS</span></span>|<span data-ttu-id="e6f56-487">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-487">String</span></span>|  
|<span data-ttu-id="e6f56-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6f56-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="e6f56-489">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-489">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="e6f56-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="e6f56-490">ProcedureColumns</span></span>  
  
|<span data-ttu-id="e6f56-491">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e6f56-491">ColumnName</span></span>|<span data-ttu-id="e6f56-492">Veri türü</span><span class="sxs-lookup"><span data-stu-id="e6f56-492">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e6f56-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="e6f56-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="e6f56-494">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-494">String</span></span>|  
|<span data-ttu-id="e6f56-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="e6f56-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="e6f56-496">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-496">String</span></span>|  
|<span data-ttu-id="e6f56-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="e6f56-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="e6f56-498">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-498">String</span></span>|  
|<span data-ttu-id="e6f56-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e6f56-499">COLUMN_NAME</span></span>|<span data-ttu-id="e6f56-500">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-500">String</span></span>|  
|<span data-ttu-id="e6f56-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6f56-501">COLUMN_TYPE</span></span>|<span data-ttu-id="e6f56-502">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-502">Int16</span></span>|  
|<span data-ttu-id="e6f56-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6f56-503">DATA_TYPE</span></span>|<span data-ttu-id="e6f56-504">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-504">Int16</span></span>|  
|<span data-ttu-id="e6f56-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="e6f56-505">TYPE_NAME</span></span>|<span data-ttu-id="e6f56-506">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-506">String</span></span>|  
|<span data-ttu-id="e6f56-507">DUYARLIK</span><span class="sxs-lookup"><span data-stu-id="e6f56-507">PRECISION</span></span>|<span data-ttu-id="e6f56-508">Int32</span><span class="sxs-lookup"><span data-stu-id="e6f56-508">Int32</span></span>|  
|<span data-ttu-id="e6f56-509">UZUNLUĞU</span><span class="sxs-lookup"><span data-stu-id="e6f56-509">LENGTH</span></span>|<span data-ttu-id="e6f56-510">Int32</span><span class="sxs-lookup"><span data-stu-id="e6f56-510">Int32</span></span>|  
|<span data-ttu-id="e6f56-511">ÖLÇEK</span><span class="sxs-lookup"><span data-stu-id="e6f56-511">SCALE</span></span>|<span data-ttu-id="e6f56-512">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-512">Int16</span></span>|  
|<span data-ttu-id="e6f56-513">SAYI TABANI</span><span class="sxs-lookup"><span data-stu-id="e6f56-513">RADIX</span></span>|<span data-ttu-id="e6f56-514">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-514">Int16</span></span>|  
|<span data-ttu-id="e6f56-515">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="e6f56-515">NULLABLE</span></span>|<span data-ttu-id="e6f56-516">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-516">Int16</span></span>|  
|<span data-ttu-id="e6f56-517">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="e6f56-517">REMARKS</span></span>|<span data-ttu-id="e6f56-518">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-518">String</span></span>|  
|<span data-ttu-id="e6f56-519">AŞIRI YÜKLEME</span><span class="sxs-lookup"><span data-stu-id="e6f56-519">OVERLOAD</span></span>|<span data-ttu-id="e6f56-520">Int32</span><span class="sxs-lookup"><span data-stu-id="e6f56-520">Int32</span></span>|  
|<span data-ttu-id="e6f56-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e6f56-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="e6f56-522">Int32</span><span class="sxs-lookup"><span data-stu-id="e6f56-522">Int32</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="e6f56-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="e6f56-523">ProcedureParameters</span></span>  
  
|<span data-ttu-id="e6f56-524">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e6f56-524">ColumnName</span></span>|<span data-ttu-id="e6f56-525">Veri türü</span><span class="sxs-lookup"><span data-stu-id="e6f56-525">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e6f56-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="e6f56-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="e6f56-527">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-527">String</span></span>|  
|<span data-ttu-id="e6f56-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="e6f56-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="e6f56-529">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-529">String</span></span>|  
|<span data-ttu-id="e6f56-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="e6f56-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="e6f56-531">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-531">String</span></span>|  
|<span data-ttu-id="e6f56-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e6f56-532">COLUMN_NAME</span></span>|<span data-ttu-id="e6f56-533">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-533">String</span></span>|  
|<span data-ttu-id="e6f56-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6f56-534">COLUMN_TYPE</span></span>|<span data-ttu-id="e6f56-535">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-535">Int16</span></span>|  
|<span data-ttu-id="e6f56-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6f56-536">DATA_TYPE</span></span>|<span data-ttu-id="e6f56-537">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-537">Int16</span></span>|  
|<span data-ttu-id="e6f56-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="e6f56-538">TYPE_NAME</span></span>|<span data-ttu-id="e6f56-539">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-539">String</span></span>|  
|<span data-ttu-id="e6f56-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="e6f56-540">COLUMN_SIZE</span></span>|<span data-ttu-id="e6f56-541">Int32</span><span class="sxs-lookup"><span data-stu-id="e6f56-541">Int32</span></span>|  
|<span data-ttu-id="e6f56-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e6f56-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="e6f56-543">Int32</span><span class="sxs-lookup"><span data-stu-id="e6f56-543">Int32</span></span>|  
|<span data-ttu-id="e6f56-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="e6f56-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="e6f56-545">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-545">Int16</span></span>|  
|<span data-ttu-id="e6f56-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="e6f56-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="e6f56-547">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-547">Int16</span></span>|  
|<span data-ttu-id="e6f56-548">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="e6f56-548">NULLABLE</span></span>|<span data-ttu-id="e6f56-549">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-549">Int16</span></span>|  
|<span data-ttu-id="e6f56-550">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="e6f56-550">REMARKS</span></span>|<span data-ttu-id="e6f56-551">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-551">String</span></span>|  
|<span data-ttu-id="e6f56-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="e6f56-552">COLUMN_DEF</span></span>|<span data-ttu-id="e6f56-553">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-553">String</span></span>|  
|<span data-ttu-id="e6f56-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6f56-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="e6f56-555">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-555">Int16</span></span>|  
|<span data-ttu-id="e6f56-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="e6f56-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="e6f56-557">Int16</span><span class="sxs-lookup"><span data-stu-id="e6f56-557">Int16</span></span>|  
|<span data-ttu-id="e6f56-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e6f56-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="e6f56-559">Int32</span><span class="sxs-lookup"><span data-stu-id="e6f56-559">Int32</span></span>|  
|<span data-ttu-id="e6f56-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e6f56-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="e6f56-561">Int32</span><span class="sxs-lookup"><span data-stu-id="e6f56-561">Int32</span></span>|  
|<span data-ttu-id="e6f56-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="e6f56-562">IS_NULLABLE</span></span>|<span data-ttu-id="e6f56-563">Dize</span><span class="sxs-lookup"><span data-stu-id="e6f56-563">String</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e6f56-564">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e6f56-564">See Also</span></span>  
 [<span data-ttu-id="e6f56-565">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="e6f56-565">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
