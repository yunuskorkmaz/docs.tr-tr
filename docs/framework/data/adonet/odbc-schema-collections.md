---
title: "ODBC şeması koleksiyonları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: b8c31f4e8b1463c184c9a8ff1cf64808783f030d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="9ce37-102">ODBC şeması koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="9ce37-102">ODBC Schema Collections</span></span>
<span data-ttu-id="9ce37-103">Bu bölümde, Microsoft SQL Server, Oracle ve Microsoft Jet ODBC sürücüleri için şema koleksiyonu desteği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9ce37-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="9ce37-104">Microsoft SQL Server ODBC sürücüsü</span><span class="sxs-lookup"><span data-stu-id="9ce37-104">Microsoft SQL Server ODBC Driver</span></span>  
 <span data-ttu-id="9ce37-105">Microsoft SQL Server ODBC sürücüsü ortak şeması koleksiyonları ek olarak aşağıdaki belirli şeması koleksiyonları destekler:</span><span class="sxs-lookup"><span data-stu-id="9ce37-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="9ce37-106">tabloları</span><span class="sxs-lookup"><span data-stu-id="9ce37-106">Tables</span></span>  
  
-   <span data-ttu-id="9ce37-107">Dizinler</span><span class="sxs-lookup"><span data-stu-id="9ce37-107">Indexes</span></span>  
  
-   <span data-ttu-id="9ce37-108">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="9ce37-108">Columns</span></span>  
  
-   <span data-ttu-id="9ce37-109">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="9ce37-109">Procedures</span></span>  
  
-   <span data-ttu-id="9ce37-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="9ce37-110">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="9ce37-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="9ce37-111">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="9ce37-112">Görünümler</span><span class="sxs-lookup"><span data-stu-id="9ce37-112">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="9ce37-113">Tabloları ve görünümleri</span><span class="sxs-lookup"><span data-stu-id="9ce37-113">Tables and Views</span></span>  
  
|<span data-ttu-id="9ce37-114">columnName</span><span class="sxs-lookup"><span data-stu-id="9ce37-114">ColumnName</span></span>|<span data-ttu-id="9ce37-115">Veri türü</span><span class="sxs-lookup"><span data-stu-id="9ce37-115">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9ce37-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="9ce37-116">TABLE_CAT</span></span>|<span data-ttu-id="9ce37-117">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-117">String</span></span>|  
|<span data-ttu-id="9ce37-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="9ce37-118">TABLE_SCHEM</span></span>|<span data-ttu-id="9ce37-119">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-119">String</span></span>|  
|<span data-ttu-id="9ce37-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9ce37-120">TABLE_NAME</span></span>|<span data-ttu-id="9ce37-121">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-121">String</span></span>|  
|<span data-ttu-id="9ce37-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="9ce37-122">TABLE_TYPE</span></span>|<span data-ttu-id="9ce37-123">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-123">String</span></span>|  
|<span data-ttu-id="9ce37-124">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="9ce37-124">REMARKS</span></span>|<span data-ttu-id="9ce37-125">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-125">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="9ce37-126">Dizinler</span><span class="sxs-lookup"><span data-stu-id="9ce37-126">Indexes</span></span>  
  
|<span data-ttu-id="9ce37-127">columnName</span><span class="sxs-lookup"><span data-stu-id="9ce37-127">ColumnName</span></span>|<span data-ttu-id="9ce37-128">Veri türü</span><span class="sxs-lookup"><span data-stu-id="9ce37-128">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9ce37-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="9ce37-129">TABLE_CAT</span></span>|<span data-ttu-id="9ce37-130">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-130">String</span></span>|  
|<span data-ttu-id="9ce37-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="9ce37-131">TABLE_SCHEM</span></span>|<span data-ttu-id="9ce37-132">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-132">String</span></span>|  
|<span data-ttu-id="9ce37-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9ce37-133">TABLE_NAME</span></span>|<span data-ttu-id="9ce37-134">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-134">String</span></span>|  
|<span data-ttu-id="9ce37-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="9ce37-135">NON_UNIQUE</span></span>|<span data-ttu-id="9ce37-136">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-136">Int16</span></span>|  
|<span data-ttu-id="9ce37-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="9ce37-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="9ce37-138">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-138">String</span></span>|  
|<span data-ttu-id="9ce37-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="9ce37-139">INDEX_NAME</span></span>|<span data-ttu-id="9ce37-140">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-140">String</span></span>|  
|<span data-ttu-id="9ce37-141">TÜRÜ</span><span class="sxs-lookup"><span data-stu-id="9ce37-141">TYPE</span></span>|<span data-ttu-id="9ce37-142">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-142">Int16</span></span>|  
|<span data-ttu-id="9ce37-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="9ce37-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="9ce37-144">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-144">Int16</span></span>|  
|<span data-ttu-id="9ce37-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="9ce37-145">COLUMN_NAME</span></span>|<span data-ttu-id="9ce37-146">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-146">String</span></span>|  
|<span data-ttu-id="9ce37-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="9ce37-147">ASC_OR_DESC</span></span>|<span data-ttu-id="9ce37-148">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-148">String</span></span>|  
|<span data-ttu-id="9ce37-149">CARDINATLITY</span><span class="sxs-lookup"><span data-stu-id="9ce37-149">CARDINATLITY</span></span>|<span data-ttu-id="9ce37-150">Int32</span><span class="sxs-lookup"><span data-stu-id="9ce37-150">Int32</span></span>|  
|<span data-ttu-id="9ce37-151">SAYFALARI</span><span class="sxs-lookup"><span data-stu-id="9ce37-151">PAGES</span></span>|<span data-ttu-id="9ce37-152">Int32</span><span class="sxs-lookup"><span data-stu-id="9ce37-152">Int32</span></span>|  
|<span data-ttu-id="9ce37-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="9ce37-153">FILTER_CONDITION</span></span>|<span data-ttu-id="9ce37-154">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-154">String</span></span>|  
|<span data-ttu-id="9ce37-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9ce37-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="9ce37-156">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-156">String</span></span>|  
|<span data-ttu-id="9ce37-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="9ce37-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="9ce37-158">Bayt</span><span class="sxs-lookup"><span data-stu-id="9ce37-158">Byte</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="9ce37-159">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="9ce37-159">Columns</span></span>  
  
|<span data-ttu-id="9ce37-160">columnName</span><span class="sxs-lookup"><span data-stu-id="9ce37-160">ColumnName</span></span>|<span data-ttu-id="9ce37-161">Veri türü</span><span class="sxs-lookup"><span data-stu-id="9ce37-161">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9ce37-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="9ce37-162">TABLE_CAT</span></span>|<span data-ttu-id="9ce37-163">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-163">String</span></span>|  
|<span data-ttu-id="9ce37-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="9ce37-164">TABLE_SCHEM</span></span>|<span data-ttu-id="9ce37-165">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-165">String</span></span>|  
|<span data-ttu-id="9ce37-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9ce37-166">TABLE_NAME</span></span>|<span data-ttu-id="9ce37-167">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-167">String</span></span>|  
|<span data-ttu-id="9ce37-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="9ce37-168">COLUMN_NAME</span></span>|<span data-ttu-id="9ce37-169">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-169">String</span></span>|  
|<span data-ttu-id="9ce37-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="9ce37-170">DATA_TYPE</span></span>|<span data-ttu-id="9ce37-171">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-171">Int16</span></span>|  
|<span data-ttu-id="9ce37-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="9ce37-172">TYPE_NAME</span></span>|<span data-ttu-id="9ce37-173">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-173">String</span></span>|  
|<span data-ttu-id="9ce37-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="9ce37-174">COLUMN_SIZE</span></span>|<span data-ttu-id="9ce37-175">Int32</span><span class="sxs-lookup"><span data-stu-id="9ce37-175">Int32</span></span>|  
|<span data-ttu-id="9ce37-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="9ce37-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="9ce37-177">Int32</span><span class="sxs-lookup"><span data-stu-id="9ce37-177">Int32</span></span>|  
|<span data-ttu-id="9ce37-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="9ce37-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="9ce37-179">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-179">Int16</span></span>|  
|<span data-ttu-id="9ce37-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="9ce37-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="9ce37-181">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-181">Int16</span></span>|  
|<span data-ttu-id="9ce37-182">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="9ce37-182">NULLABLE</span></span>|<span data-ttu-id="9ce37-183">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-183">Int16</span></span>|  
|<span data-ttu-id="9ce37-184">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="9ce37-184">REMARKS</span></span>|<span data-ttu-id="9ce37-185">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-185">String</span></span>|  
|<span data-ttu-id="9ce37-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="9ce37-186">COLUMN_DEF</span></span>|<span data-ttu-id="9ce37-187">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-187">String</span></span>|  
|<span data-ttu-id="9ce37-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="9ce37-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="9ce37-189">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-189">Int16</span></span>|  
|<span data-ttu-id="9ce37-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="9ce37-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="9ce37-191">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-191">Int16</span></span>|  
|<span data-ttu-id="9ce37-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="9ce37-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="9ce37-193">Int32</span><span class="sxs-lookup"><span data-stu-id="9ce37-193">Int32</span></span>|  
|<span data-ttu-id="9ce37-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="9ce37-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="9ce37-195">Int32</span><span class="sxs-lookup"><span data-stu-id="9ce37-195">Int32</span></span>|  
|<span data-ttu-id="9ce37-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="9ce37-196">IS_NULLABLE</span></span>|<span data-ttu-id="9ce37-197">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-197">String</span></span>|  
|<span data-ttu-id="9ce37-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9ce37-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="9ce37-199">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-199">String</span></span>|  
|<span data-ttu-id="9ce37-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9ce37-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="9ce37-201">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-201">String</span></span>|  
|<span data-ttu-id="9ce37-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="9ce37-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="9ce37-203">Bayt</span><span class="sxs-lookup"><span data-stu-id="9ce37-203">Byte</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="9ce37-204">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="9ce37-204">Procedures</span></span>  
  
|<span data-ttu-id="9ce37-205">columnName</span><span class="sxs-lookup"><span data-stu-id="9ce37-205">ColumnName</span></span>|<span data-ttu-id="9ce37-206">Veri türü</span><span class="sxs-lookup"><span data-stu-id="9ce37-206">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9ce37-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="9ce37-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="9ce37-208">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-208">String</span></span>|  
|<span data-ttu-id="9ce37-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="9ce37-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="9ce37-210">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-210">String</span></span>|  
|<span data-ttu-id="9ce37-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="9ce37-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="9ce37-212">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-212">String</span></span>|  
|<span data-ttu-id="9ce37-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="9ce37-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="9ce37-214">Int32</span><span class="sxs-lookup"><span data-stu-id="9ce37-214">Int32</span></span>|  
|<span data-ttu-id="9ce37-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="9ce37-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="9ce37-216">Int32</span><span class="sxs-lookup"><span data-stu-id="9ce37-216">Int32</span></span>|  
|<span data-ttu-id="9ce37-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="9ce37-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="9ce37-218">Int32</span><span class="sxs-lookup"><span data-stu-id="9ce37-218">Int32</span></span>|  
|<span data-ttu-id="9ce37-219">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="9ce37-219">REMARKS</span></span>|<span data-ttu-id="9ce37-220">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-220">String</span></span>|  
|<span data-ttu-id="9ce37-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="9ce37-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="9ce37-222">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-222">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="9ce37-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="9ce37-223">ProcedureColumns</span></span>  
  
|<span data-ttu-id="9ce37-224">columnName</span><span class="sxs-lookup"><span data-stu-id="9ce37-224">ColumnName</span></span>|<span data-ttu-id="9ce37-225">Veri türü</span><span class="sxs-lookup"><span data-stu-id="9ce37-225">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9ce37-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="9ce37-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="9ce37-227">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-227">String</span></span>|  
|<span data-ttu-id="9ce37-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="9ce37-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="9ce37-229">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-229">String</span></span>|  
|<span data-ttu-id="9ce37-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="9ce37-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="9ce37-231">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-231">String</span></span>|  
|<span data-ttu-id="9ce37-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="9ce37-232">COLUMN_NAME</span></span>|<span data-ttu-id="9ce37-233">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-233">String</span></span>|  
|<span data-ttu-id="9ce37-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="9ce37-234">COLUMN_TYPE</span></span>|<span data-ttu-id="9ce37-235">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-235">Int16</span></span>|  
|<span data-ttu-id="9ce37-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="9ce37-236">DATA_TYPE</span></span>|<span data-ttu-id="9ce37-237">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-237">Int16</span></span>|  
|<span data-ttu-id="9ce37-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="9ce37-238">TYPE_NAME</span></span>|<span data-ttu-id="9ce37-239">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-239">String</span></span>|  
|<span data-ttu-id="9ce37-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="9ce37-240">COLUMN_SIZE</span></span>|<span data-ttu-id="9ce37-241">Int32</span><span class="sxs-lookup"><span data-stu-id="9ce37-241">Int32</span></span>|  
|<span data-ttu-id="9ce37-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="9ce37-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="9ce37-243">Int32</span><span class="sxs-lookup"><span data-stu-id="9ce37-243">Int32</span></span>|  
|<span data-ttu-id="9ce37-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="9ce37-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="9ce37-245">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-245">Int16</span></span>|  
|<span data-ttu-id="9ce37-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="9ce37-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="9ce37-247">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-247">Int16</span></span>|  
|<span data-ttu-id="9ce37-248">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="9ce37-248">NULLABLE</span></span>|<span data-ttu-id="9ce37-249">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-249">Int16</span></span>|  
|<span data-ttu-id="9ce37-250">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="9ce37-250">REMARKS</span></span>|<span data-ttu-id="9ce37-251">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-251">String</span></span>|  
|<span data-ttu-id="9ce37-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="9ce37-252">COLUMN_DEF</span></span>|<span data-ttu-id="9ce37-253">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-253">String</span></span>|  
|<span data-ttu-id="9ce37-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="9ce37-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="9ce37-255">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-255">Int16</span></span>|  
|<span data-ttu-id="9ce37-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="9ce37-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="9ce37-257">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-257">Int16</span></span>|  
|<span data-ttu-id="9ce37-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="9ce37-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="9ce37-259">Int32</span><span class="sxs-lookup"><span data-stu-id="9ce37-259">Int32</span></span>|  
|<span data-ttu-id="9ce37-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="9ce37-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="9ce37-261">Int32</span><span class="sxs-lookup"><span data-stu-id="9ce37-261">Int32</span></span>|  
|<span data-ttu-id="9ce37-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="9ce37-262">IS_NULLABLE</span></span>|<span data-ttu-id="9ce37-263">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-263">String</span></span>|  
|<span data-ttu-id="9ce37-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9ce37-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="9ce37-265">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-265">String</span></span>|  
|<span data-ttu-id="9ce37-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9ce37-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="9ce37-267">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-267">String</span></span>|  
|<span data-ttu-id="9ce37-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="9ce37-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="9ce37-269">Bayt</span><span class="sxs-lookup"><span data-stu-id="9ce37-269">Byte</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="9ce37-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="9ce37-270">ProcedureParameters</span></span>  
  
|<span data-ttu-id="9ce37-271">columnName</span><span class="sxs-lookup"><span data-stu-id="9ce37-271">ColumnName</span></span>|<span data-ttu-id="9ce37-272">Veri türü</span><span class="sxs-lookup"><span data-stu-id="9ce37-272">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9ce37-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="9ce37-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="9ce37-274">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-274">String</span></span>|  
|<span data-ttu-id="9ce37-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="9ce37-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="9ce37-276">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-276">String</span></span>|  
|<span data-ttu-id="9ce37-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="9ce37-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="9ce37-278">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-278">String</span></span>|  
|<span data-ttu-id="9ce37-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="9ce37-279">COLUMN_NAME</span></span>|<span data-ttu-id="9ce37-280">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-280">String</span></span>|  
|<span data-ttu-id="9ce37-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="9ce37-281">COLUMN_TYPE</span></span>|<span data-ttu-id="9ce37-282">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-282">Int16</span></span>|  
|<span data-ttu-id="9ce37-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="9ce37-283">DATA_TYPE</span></span>|<span data-ttu-id="9ce37-284">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-284">Int16</span></span>|  
|<span data-ttu-id="9ce37-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="9ce37-285">TYPE_NAME</span></span>|<span data-ttu-id="9ce37-286">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-286">String</span></span>|  
|<span data-ttu-id="9ce37-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="9ce37-287">COLUMN_SIZE</span></span>|<span data-ttu-id="9ce37-288">Int32</span><span class="sxs-lookup"><span data-stu-id="9ce37-288">Int32</span></span>|  
|<span data-ttu-id="9ce37-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="9ce37-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="9ce37-290">Int32</span><span class="sxs-lookup"><span data-stu-id="9ce37-290">Int32</span></span>|  
|<span data-ttu-id="9ce37-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="9ce37-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="9ce37-292">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-292">Int16</span></span>|  
|<span data-ttu-id="9ce37-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="9ce37-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="9ce37-294">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-294">Int16</span></span>|  
|<span data-ttu-id="9ce37-295">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="9ce37-295">NULLABLE</span></span>|<span data-ttu-id="9ce37-296">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-296">Int16</span></span>|  
|<span data-ttu-id="9ce37-297">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="9ce37-297">REMARKS</span></span>|<span data-ttu-id="9ce37-298">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-298">String</span></span>|  
|<span data-ttu-id="9ce37-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="9ce37-299">COLUMN_DEF</span></span>|<span data-ttu-id="9ce37-300">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-300">String</span></span>|  
|<span data-ttu-id="9ce37-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="9ce37-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="9ce37-302">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-302">Int16</span></span>|  
|<span data-ttu-id="9ce37-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="9ce37-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="9ce37-304">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-304">Int16</span></span>|  
|<span data-ttu-id="9ce37-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="9ce37-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="9ce37-306">Int32</span><span class="sxs-lookup"><span data-stu-id="9ce37-306">Int32</span></span>|  
|<span data-ttu-id="9ce37-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="9ce37-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="9ce37-308">Int32</span><span class="sxs-lookup"><span data-stu-id="9ce37-308">Int32</span></span>|  
|<span data-ttu-id="9ce37-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="9ce37-309">IS_NULLABLE</span></span>|<span data-ttu-id="9ce37-310">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-310">String</span></span>|  
|<span data-ttu-id="9ce37-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9ce37-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="9ce37-312">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-312">String</span></span>|  
|<span data-ttu-id="9ce37-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9ce37-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="9ce37-314">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-314">String</span></span>|  
|<span data-ttu-id="9ce37-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="9ce37-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="9ce37-316">Bayt</span><span class="sxs-lookup"><span data-stu-id="9ce37-316">Byte</span></span>|  
  
## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="9ce37-317">Microsoft Oracle ODBC sürücüsü</span><span class="sxs-lookup"><span data-stu-id="9ce37-317">Microsoft Oracle ODBC Driver</span></span>  
 <span data-ttu-id="9ce37-318">Microsoft SQL Server Oracle ODBC sürücüsü ortak şeması koleksiyonları ek olarak aşağıdaki belirli şeması koleksiyonları destekler:</span><span class="sxs-lookup"><span data-stu-id="9ce37-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="9ce37-319">tabloları</span><span class="sxs-lookup"><span data-stu-id="9ce37-319">Tables</span></span>  
  
-   <span data-ttu-id="9ce37-320">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="9ce37-320">Columns</span></span>  
  
-   <span data-ttu-id="9ce37-321">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="9ce37-321">Procedures</span></span>  
  
-   <span data-ttu-id="9ce37-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="9ce37-322">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="9ce37-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="9ce37-323">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="9ce37-324">Görünümler</span><span class="sxs-lookup"><span data-stu-id="9ce37-324">Views</span></span>  
  
-   <span data-ttu-id="9ce37-325">Dizinler</span><span class="sxs-lookup"><span data-stu-id="9ce37-325">Indexes</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="9ce37-326">Tabloları ve görünümleri</span><span class="sxs-lookup"><span data-stu-id="9ce37-326">Tables and Views</span></span>  
  
|<span data-ttu-id="9ce37-327">columnName</span><span class="sxs-lookup"><span data-stu-id="9ce37-327">ColumnName</span></span>|<span data-ttu-id="9ce37-328">Veri türü</span><span class="sxs-lookup"><span data-stu-id="9ce37-328">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9ce37-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="9ce37-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="9ce37-330">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-330">String</span></span>|  
|<span data-ttu-id="9ce37-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="9ce37-331">TABLE_OWNER</span></span>|<span data-ttu-id="9ce37-332">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-332">String</span></span>|  
|<span data-ttu-id="9ce37-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9ce37-333">TABLE_NAME</span></span>|<span data-ttu-id="9ce37-334">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-334">String</span></span>|  
|<span data-ttu-id="9ce37-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="9ce37-335">TABLE_TYPE</span></span>|<span data-ttu-id="9ce37-336">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-336">String</span></span>|  
|<span data-ttu-id="9ce37-337">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="9ce37-337">REMARKS</span></span>|<span data-ttu-id="9ce37-338">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-338">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="9ce37-339">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="9ce37-339">Columns</span></span>  
  
|<span data-ttu-id="9ce37-340">columnName</span><span class="sxs-lookup"><span data-stu-id="9ce37-340">ColumnName</span></span>|<span data-ttu-id="9ce37-341">Veri türü</span><span class="sxs-lookup"><span data-stu-id="9ce37-341">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9ce37-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="9ce37-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="9ce37-343">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-343">String</span></span>|  
|<span data-ttu-id="9ce37-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="9ce37-344">TABLE_OWNER</span></span>|<span data-ttu-id="9ce37-345">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-345">String</span></span>|  
|<span data-ttu-id="9ce37-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9ce37-346">TABLE_NAME</span></span>|<span data-ttu-id="9ce37-347">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-347">String</span></span>|  
|<span data-ttu-id="9ce37-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="9ce37-348">COLUMN_NAME</span></span>|<span data-ttu-id="9ce37-349">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-349">String</span></span>|  
|<span data-ttu-id="9ce37-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="9ce37-350">DATA_TYPE</span></span>|<span data-ttu-id="9ce37-351">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-351">Int16</span></span>|  
|<span data-ttu-id="9ce37-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="9ce37-352">TYPE_NAME</span></span>|<span data-ttu-id="9ce37-353">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-353">String</span></span>|  
|<span data-ttu-id="9ce37-354">DUYARLILIK</span><span class="sxs-lookup"><span data-stu-id="9ce37-354">PRECISION</span></span>|<span data-ttu-id="9ce37-355">Int32</span><span class="sxs-lookup"><span data-stu-id="9ce37-355">Int32</span></span>|  
|<span data-ttu-id="9ce37-356">UZUNLUĞU</span><span class="sxs-lookup"><span data-stu-id="9ce37-356">LENGTH</span></span>|<span data-ttu-id="9ce37-357">Int32</span><span class="sxs-lookup"><span data-stu-id="9ce37-357">Int32</span></span>|  
|<span data-ttu-id="9ce37-358">ÖLÇEK</span><span class="sxs-lookup"><span data-stu-id="9ce37-358">SCALE</span></span>|<span data-ttu-id="9ce37-359">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-359">Int16</span></span>|  
|<span data-ttu-id="9ce37-360">SAYI TABANINI</span><span class="sxs-lookup"><span data-stu-id="9ce37-360">RADIX</span></span>|<span data-ttu-id="9ce37-361">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-361">Int16</span></span>|  
|<span data-ttu-id="9ce37-362">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="9ce37-362">NULLABLE</span></span>|<span data-ttu-id="9ce37-363">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-363">Int16</span></span>|  
|<span data-ttu-id="9ce37-364">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="9ce37-364">REMARKS</span></span>|<span data-ttu-id="9ce37-365">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-365">String</span></span>|  
|<span data-ttu-id="9ce37-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="9ce37-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="9ce37-367">Int32</span><span class="sxs-lookup"><span data-stu-id="9ce37-367">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="9ce37-368">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="9ce37-368">Procedures</span></span>  
  
|<span data-ttu-id="9ce37-369">columnName</span><span class="sxs-lookup"><span data-stu-id="9ce37-369">ColumnName</span></span>|<span data-ttu-id="9ce37-370">Veri türü</span><span class="sxs-lookup"><span data-stu-id="9ce37-370">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9ce37-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="9ce37-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="9ce37-372">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-372">String</span></span>|  
|<span data-ttu-id="9ce37-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="9ce37-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="9ce37-374">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-374">String</span></span>|  
|<span data-ttu-id="9ce37-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="9ce37-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="9ce37-376">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-376">String</span></span>|  
|<span data-ttu-id="9ce37-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="9ce37-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="9ce37-378">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-378">Int16</span></span>|  
|<span data-ttu-id="9ce37-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="9ce37-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="9ce37-380">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-380">Int16</span></span>|  
|<span data-ttu-id="9ce37-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="9ce37-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="9ce37-382">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-382">Int16</span></span>|  
|<span data-ttu-id="9ce37-383">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="9ce37-383">REMARKS</span></span>|<span data-ttu-id="9ce37-384">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-384">String</span></span>|  
|<span data-ttu-id="9ce37-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="9ce37-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="9ce37-386">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-386">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="9ce37-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="9ce37-387">ProcedureColumns</span></span>  
  
|<span data-ttu-id="9ce37-388">columnName</span><span class="sxs-lookup"><span data-stu-id="9ce37-388">ColumnName</span></span>|<span data-ttu-id="9ce37-389">Veri türü</span><span class="sxs-lookup"><span data-stu-id="9ce37-389">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9ce37-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="9ce37-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="9ce37-391">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-391">String</span></span>|  
|<span data-ttu-id="9ce37-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="9ce37-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="9ce37-393">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-393">String</span></span>|  
|<span data-ttu-id="9ce37-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="9ce37-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="9ce37-395">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-395">String</span></span>|  
|<span data-ttu-id="9ce37-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="9ce37-396">COLUMN_NAME</span></span>|<span data-ttu-id="9ce37-397">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-397">String</span></span>|  
|<span data-ttu-id="9ce37-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="9ce37-398">COLUMN_TYPE</span></span>|<span data-ttu-id="9ce37-399">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-399">Int16</span></span>|  
|<span data-ttu-id="9ce37-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="9ce37-400">DATA_TYPE</span></span>|<span data-ttu-id="9ce37-401">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-401">Int16</span></span>|  
|<span data-ttu-id="9ce37-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="9ce37-402">TYPE_NAME</span></span>|<span data-ttu-id="9ce37-403">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-403">String</span></span>|  
|<span data-ttu-id="9ce37-404">DUYARLILIK</span><span class="sxs-lookup"><span data-stu-id="9ce37-404">PRECISION</span></span>|<span data-ttu-id="9ce37-405">Int32</span><span class="sxs-lookup"><span data-stu-id="9ce37-405">Int32</span></span>|  
|<span data-ttu-id="9ce37-406">UZUNLUĞU</span><span class="sxs-lookup"><span data-stu-id="9ce37-406">LENGTH</span></span>|<span data-ttu-id="9ce37-407">Int32</span><span class="sxs-lookup"><span data-stu-id="9ce37-407">Int32</span></span>|  
|<span data-ttu-id="9ce37-408">ÖLÇEK</span><span class="sxs-lookup"><span data-stu-id="9ce37-408">SCALE</span></span>|<span data-ttu-id="9ce37-409">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-409">Int16</span></span>|  
|<span data-ttu-id="9ce37-410">SAYI TABANINI</span><span class="sxs-lookup"><span data-stu-id="9ce37-410">RADIX</span></span>|<span data-ttu-id="9ce37-411">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-411">Int16</span></span>|  
|<span data-ttu-id="9ce37-412">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="9ce37-412">NULLABLE</span></span>|<span data-ttu-id="9ce37-413">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-413">Int16</span></span>|  
|<span data-ttu-id="9ce37-414">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="9ce37-414">REMARKS</span></span>|<span data-ttu-id="9ce37-415">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-415">String</span></span>|  
|<span data-ttu-id="9ce37-416">AŞIRI YÜKLEME</span><span class="sxs-lookup"><span data-stu-id="9ce37-416">OVERLOAD</span></span>|<span data-ttu-id="9ce37-417">Int32</span><span class="sxs-lookup"><span data-stu-id="9ce37-417">Int32</span></span>|  
|<span data-ttu-id="9ce37-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="9ce37-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="9ce37-419">Int32</span><span class="sxs-lookup"><span data-stu-id="9ce37-419">Int32</span></span>|  
  
## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="9ce37-420">Microsoft Jet ODBC sürücüsü</span><span class="sxs-lookup"><span data-stu-id="9ce37-420">Microsoft Jet ODBC Driver</span></span>  
 <span data-ttu-id="9ce37-421">Microsoft Jet ODBC sürücüsü ortak şeması koleksiyonları ek olarak aşağıdaki belirli şeması koleksiyonları destekler:</span><span class="sxs-lookup"><span data-stu-id="9ce37-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="9ce37-422">tabloları</span><span class="sxs-lookup"><span data-stu-id="9ce37-422">Tables</span></span>  
  
-   <span data-ttu-id="9ce37-423">Dizinler</span><span class="sxs-lookup"><span data-stu-id="9ce37-423">Indexes</span></span>  
  
-   <span data-ttu-id="9ce37-424">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="9ce37-424">Columns</span></span>  
  
-   <span data-ttu-id="9ce37-425">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="9ce37-425">Procedures</span></span>  
  
-   <span data-ttu-id="9ce37-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="9ce37-426">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="9ce37-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="9ce37-427">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="9ce37-428">Görünümler</span><span class="sxs-lookup"><span data-stu-id="9ce37-428">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="9ce37-429">Tabloları ve görünümleri</span><span class="sxs-lookup"><span data-stu-id="9ce37-429">Tables and Views</span></span>  
  
|<span data-ttu-id="9ce37-430">columnName</span><span class="sxs-lookup"><span data-stu-id="9ce37-430">ColumnName</span></span>|<span data-ttu-id="9ce37-431">Veri türü</span><span class="sxs-lookup"><span data-stu-id="9ce37-431">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9ce37-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="9ce37-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="9ce37-433">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-433">String</span></span>|  
|<span data-ttu-id="9ce37-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="9ce37-434">TABLE_OWNER</span></span>|<span data-ttu-id="9ce37-435">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-435">String</span></span>|  
|<span data-ttu-id="9ce37-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9ce37-436">TABLE_NAME</span></span>|<span data-ttu-id="9ce37-437">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-437">String</span></span>|  
|<span data-ttu-id="9ce37-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="9ce37-438">TABLE_TYPE</span></span>|<span data-ttu-id="9ce37-439">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-439">String</span></span>|  
|<span data-ttu-id="9ce37-440">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="9ce37-440">REMARKS</span></span>|<span data-ttu-id="9ce37-441">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-441">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="9ce37-442">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="9ce37-442">Columns</span></span>  
  
|<span data-ttu-id="9ce37-443">columnName</span><span class="sxs-lookup"><span data-stu-id="9ce37-443">ColumnName</span></span>|<span data-ttu-id="9ce37-444">Veri türü</span><span class="sxs-lookup"><span data-stu-id="9ce37-444">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9ce37-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="9ce37-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="9ce37-446">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-446">String</span></span>|  
|<span data-ttu-id="9ce37-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="9ce37-447">TABLE_OWNER</span></span>|<span data-ttu-id="9ce37-448">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-448">String</span></span>|  
|<span data-ttu-id="9ce37-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9ce37-449">TABLE_NAME</span></span>|<span data-ttu-id="9ce37-450">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-450">String</span></span>|  
|<span data-ttu-id="9ce37-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="9ce37-451">COLUMN_NAME</span></span>|<span data-ttu-id="9ce37-452">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-452">String</span></span>|  
|<span data-ttu-id="9ce37-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="9ce37-453">DATA_TYPE</span></span>|<span data-ttu-id="9ce37-454">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-454">Int16</span></span>|  
|<span data-ttu-id="9ce37-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="9ce37-455">TYPE_NAME</span></span>|<span data-ttu-id="9ce37-456">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-456">String</span></span>|  
|<span data-ttu-id="9ce37-457">DUYARLILIK</span><span class="sxs-lookup"><span data-stu-id="9ce37-457">PRECISION</span></span>|<span data-ttu-id="9ce37-458">Int32</span><span class="sxs-lookup"><span data-stu-id="9ce37-458">Int32</span></span>|  
|<span data-ttu-id="9ce37-459">UZUNLUĞU</span><span class="sxs-lookup"><span data-stu-id="9ce37-459">LENGTH</span></span>|<span data-ttu-id="9ce37-460">Int32</span><span class="sxs-lookup"><span data-stu-id="9ce37-460">Int32</span></span>|  
|<span data-ttu-id="9ce37-461">ÖLÇEK</span><span class="sxs-lookup"><span data-stu-id="9ce37-461">SCALE</span></span>|<span data-ttu-id="9ce37-462">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-462">Int16</span></span>|  
|<span data-ttu-id="9ce37-463">SAYI TABANINI</span><span class="sxs-lookup"><span data-stu-id="9ce37-463">RADIX</span></span>|<span data-ttu-id="9ce37-464">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-464">Int16</span></span>|  
|<span data-ttu-id="9ce37-465">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="9ce37-465">NULLABLE</span></span>|<span data-ttu-id="9ce37-466">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-466">Int16</span></span>|  
|<span data-ttu-id="9ce37-467">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="9ce37-467">REMARKS</span></span>|<span data-ttu-id="9ce37-468">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-468">String</span></span>|  
|<span data-ttu-id="9ce37-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="9ce37-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="9ce37-470">Int32</span><span class="sxs-lookup"><span data-stu-id="9ce37-470">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="9ce37-471">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="9ce37-471">Procedures</span></span>  
  
|<span data-ttu-id="9ce37-472">columnName</span><span class="sxs-lookup"><span data-stu-id="9ce37-472">ColumnName</span></span>|<span data-ttu-id="9ce37-473">Veri türü</span><span class="sxs-lookup"><span data-stu-id="9ce37-473">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9ce37-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="9ce37-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="9ce37-475">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-475">String</span></span>|  
|<span data-ttu-id="9ce37-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="9ce37-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="9ce37-477">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-477">String</span></span>|  
|<span data-ttu-id="9ce37-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="9ce37-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="9ce37-479">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-479">String</span></span>|  
|<span data-ttu-id="9ce37-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="9ce37-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="9ce37-481">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-481">Int16</span></span>|  
|<span data-ttu-id="9ce37-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="9ce37-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="9ce37-483">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-483">Int16</span></span>|  
|<span data-ttu-id="9ce37-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="9ce37-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="9ce37-485">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-485">Int16</span></span>|  
|<span data-ttu-id="9ce37-486">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="9ce37-486">REMARKS</span></span>|<span data-ttu-id="9ce37-487">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-487">String</span></span>|  
|<span data-ttu-id="9ce37-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="9ce37-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="9ce37-489">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-489">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="9ce37-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="9ce37-490">ProcedureColumns</span></span>  
  
|<span data-ttu-id="9ce37-491">columnName</span><span class="sxs-lookup"><span data-stu-id="9ce37-491">ColumnName</span></span>|<span data-ttu-id="9ce37-492">Veri türü</span><span class="sxs-lookup"><span data-stu-id="9ce37-492">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9ce37-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="9ce37-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="9ce37-494">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-494">String</span></span>|  
|<span data-ttu-id="9ce37-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="9ce37-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="9ce37-496">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-496">String</span></span>|  
|<span data-ttu-id="9ce37-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="9ce37-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="9ce37-498">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-498">String</span></span>|  
|<span data-ttu-id="9ce37-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="9ce37-499">COLUMN_NAME</span></span>|<span data-ttu-id="9ce37-500">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-500">String</span></span>|  
|<span data-ttu-id="9ce37-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="9ce37-501">COLUMN_TYPE</span></span>|<span data-ttu-id="9ce37-502">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-502">Int16</span></span>|  
|<span data-ttu-id="9ce37-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="9ce37-503">DATA_TYPE</span></span>|<span data-ttu-id="9ce37-504">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-504">Int16</span></span>|  
|<span data-ttu-id="9ce37-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="9ce37-505">TYPE_NAME</span></span>|<span data-ttu-id="9ce37-506">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-506">String</span></span>|  
|<span data-ttu-id="9ce37-507">DUYARLILIK</span><span class="sxs-lookup"><span data-stu-id="9ce37-507">PRECISION</span></span>|<span data-ttu-id="9ce37-508">Int32</span><span class="sxs-lookup"><span data-stu-id="9ce37-508">Int32</span></span>|  
|<span data-ttu-id="9ce37-509">UZUNLUĞU</span><span class="sxs-lookup"><span data-stu-id="9ce37-509">LENGTH</span></span>|<span data-ttu-id="9ce37-510">Int32</span><span class="sxs-lookup"><span data-stu-id="9ce37-510">Int32</span></span>|  
|<span data-ttu-id="9ce37-511">ÖLÇEK</span><span class="sxs-lookup"><span data-stu-id="9ce37-511">SCALE</span></span>|<span data-ttu-id="9ce37-512">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-512">Int16</span></span>|  
|<span data-ttu-id="9ce37-513">SAYI TABANINI</span><span class="sxs-lookup"><span data-stu-id="9ce37-513">RADIX</span></span>|<span data-ttu-id="9ce37-514">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-514">Int16</span></span>|  
|<span data-ttu-id="9ce37-515">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="9ce37-515">NULLABLE</span></span>|<span data-ttu-id="9ce37-516">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-516">Int16</span></span>|  
|<span data-ttu-id="9ce37-517">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="9ce37-517">REMARKS</span></span>|<span data-ttu-id="9ce37-518">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-518">String</span></span>|  
|<span data-ttu-id="9ce37-519">AŞIRI YÜKLEME</span><span class="sxs-lookup"><span data-stu-id="9ce37-519">OVERLOAD</span></span>|<span data-ttu-id="9ce37-520">Int32</span><span class="sxs-lookup"><span data-stu-id="9ce37-520">Int32</span></span>|  
|<span data-ttu-id="9ce37-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="9ce37-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="9ce37-522">Int32</span><span class="sxs-lookup"><span data-stu-id="9ce37-522">Int32</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="9ce37-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="9ce37-523">ProcedureParameters</span></span>  
  
|<span data-ttu-id="9ce37-524">columnName</span><span class="sxs-lookup"><span data-stu-id="9ce37-524">ColumnName</span></span>|<span data-ttu-id="9ce37-525">Veri türü</span><span class="sxs-lookup"><span data-stu-id="9ce37-525">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9ce37-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="9ce37-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="9ce37-527">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-527">String</span></span>|  
|<span data-ttu-id="9ce37-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="9ce37-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="9ce37-529">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-529">String</span></span>|  
|<span data-ttu-id="9ce37-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="9ce37-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="9ce37-531">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-531">String</span></span>|  
|<span data-ttu-id="9ce37-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="9ce37-532">COLUMN_NAME</span></span>|<span data-ttu-id="9ce37-533">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-533">String</span></span>|  
|<span data-ttu-id="9ce37-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="9ce37-534">COLUMN_TYPE</span></span>|<span data-ttu-id="9ce37-535">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-535">Int16</span></span>|  
|<span data-ttu-id="9ce37-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="9ce37-536">DATA_TYPE</span></span>|<span data-ttu-id="9ce37-537">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-537">Int16</span></span>|  
|<span data-ttu-id="9ce37-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="9ce37-538">TYPE_NAME</span></span>|<span data-ttu-id="9ce37-539">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-539">String</span></span>|  
|<span data-ttu-id="9ce37-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="9ce37-540">COLUMN_SIZE</span></span>|<span data-ttu-id="9ce37-541">Int32</span><span class="sxs-lookup"><span data-stu-id="9ce37-541">Int32</span></span>|  
|<span data-ttu-id="9ce37-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="9ce37-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="9ce37-543">Int32</span><span class="sxs-lookup"><span data-stu-id="9ce37-543">Int32</span></span>|  
|<span data-ttu-id="9ce37-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="9ce37-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="9ce37-545">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-545">Int16</span></span>|  
|<span data-ttu-id="9ce37-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="9ce37-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="9ce37-547">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-547">Int16</span></span>|  
|<span data-ttu-id="9ce37-548">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="9ce37-548">NULLABLE</span></span>|<span data-ttu-id="9ce37-549">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-549">Int16</span></span>|  
|<span data-ttu-id="9ce37-550">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="9ce37-550">REMARKS</span></span>|<span data-ttu-id="9ce37-551">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-551">String</span></span>|  
|<span data-ttu-id="9ce37-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="9ce37-552">COLUMN_DEF</span></span>|<span data-ttu-id="9ce37-553">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-553">String</span></span>|  
|<span data-ttu-id="9ce37-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="9ce37-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="9ce37-555">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-555">Int16</span></span>|  
|<span data-ttu-id="9ce37-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="9ce37-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="9ce37-557">Int16</span><span class="sxs-lookup"><span data-stu-id="9ce37-557">Int16</span></span>|  
|<span data-ttu-id="9ce37-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="9ce37-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="9ce37-559">Int32</span><span class="sxs-lookup"><span data-stu-id="9ce37-559">Int32</span></span>|  
|<span data-ttu-id="9ce37-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="9ce37-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="9ce37-561">Int32</span><span class="sxs-lookup"><span data-stu-id="9ce37-561">Int32</span></span>|  
|<span data-ttu-id="9ce37-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="9ce37-562">IS_NULLABLE</span></span>|<span data-ttu-id="9ce37-563">Dize</span><span class="sxs-lookup"><span data-stu-id="9ce37-563">String</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9ce37-564">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9ce37-564">See Also</span></span>  
 [<span data-ttu-id="9ce37-565">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="9ce37-565">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
