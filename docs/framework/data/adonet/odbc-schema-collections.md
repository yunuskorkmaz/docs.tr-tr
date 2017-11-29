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
ms.openlocfilehash: 889e84db39af1257d709ef049e18d4397ea700d0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="ed31d-102">ODBC şeması koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="ed31d-102">ODBC Schema Collections</span></span>
<span data-ttu-id="ed31d-103">Bu bölümde, Microsoft SQL Server, Oracle ve Microsoft Jet ODBC sürücüleri için şema koleksiyonu desteği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ed31d-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="ed31d-104">Microsoft SQL Server ODBC sürücüsü</span><span class="sxs-lookup"><span data-stu-id="ed31d-104">Microsoft SQL Server ODBC Driver</span></span>  
 <span data-ttu-id="ed31d-105">Microsoft SQL Server ODBC sürücüsü ortak şeması koleksiyonları ek olarak aşağıdaki belirli şeması koleksiyonları destekler:</span><span class="sxs-lookup"><span data-stu-id="ed31d-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="ed31d-106">tabloları</span><span class="sxs-lookup"><span data-stu-id="ed31d-106">Tables</span></span>  
  
-   <span data-ttu-id="ed31d-107">Dizinler</span><span class="sxs-lookup"><span data-stu-id="ed31d-107">Indexes</span></span>  
  
-   <span data-ttu-id="ed31d-108">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="ed31d-108">Columns</span></span>  
  
-   <span data-ttu-id="ed31d-109">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="ed31d-109">Procedures</span></span>  
  
-   <span data-ttu-id="ed31d-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="ed31d-110">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="ed31d-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="ed31d-111">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="ed31d-112">Görünümler</span><span class="sxs-lookup"><span data-stu-id="ed31d-112">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="ed31d-113">Tabloları ve görünümleri</span><span class="sxs-lookup"><span data-stu-id="ed31d-113">Tables and Views</span></span>  
  
|<span data-ttu-id="ed31d-114">columnName</span><span class="sxs-lookup"><span data-stu-id="ed31d-114">ColumnName</span></span>|<span data-ttu-id="ed31d-115">Veri türü</span><span class="sxs-lookup"><span data-stu-id="ed31d-115">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="ed31d-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="ed31d-116">TABLE_CAT</span></span>|<span data-ttu-id="ed31d-117">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-117">String</span></span>|  
|<span data-ttu-id="ed31d-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="ed31d-118">TABLE_SCHEM</span></span>|<span data-ttu-id="ed31d-119">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-119">String</span></span>|  
|<span data-ttu-id="ed31d-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="ed31d-120">TABLE_NAME</span></span>|<span data-ttu-id="ed31d-121">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-121">String</span></span>|  
|<span data-ttu-id="ed31d-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="ed31d-122">TABLE_TYPE</span></span>|<span data-ttu-id="ed31d-123">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-123">String</span></span>|  
|<span data-ttu-id="ed31d-124">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="ed31d-124">REMARKS</span></span>|<span data-ttu-id="ed31d-125">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-125">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="ed31d-126">Dizinler</span><span class="sxs-lookup"><span data-stu-id="ed31d-126">Indexes</span></span>  
  
|<span data-ttu-id="ed31d-127">columnName</span><span class="sxs-lookup"><span data-stu-id="ed31d-127">ColumnName</span></span>|<span data-ttu-id="ed31d-128">Veri türü</span><span class="sxs-lookup"><span data-stu-id="ed31d-128">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="ed31d-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="ed31d-129">TABLE_CAT</span></span>|<span data-ttu-id="ed31d-130">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-130">String</span></span>|  
|<span data-ttu-id="ed31d-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="ed31d-131">TABLE_SCHEM</span></span>|<span data-ttu-id="ed31d-132">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-132">String</span></span>|  
|<span data-ttu-id="ed31d-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="ed31d-133">TABLE_NAME</span></span>|<span data-ttu-id="ed31d-134">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-134">String</span></span>|  
|<span data-ttu-id="ed31d-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="ed31d-135">NON_UNIQUE</span></span>|<span data-ttu-id="ed31d-136">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-136">Int16</span></span>|  
|<span data-ttu-id="ed31d-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="ed31d-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="ed31d-138">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-138">String</span></span>|  
|<span data-ttu-id="ed31d-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="ed31d-139">INDEX_NAME</span></span>|<span data-ttu-id="ed31d-140">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-140">String</span></span>|  
|<span data-ttu-id="ed31d-141">TÜRÜ</span><span class="sxs-lookup"><span data-stu-id="ed31d-141">TYPE</span></span>|<span data-ttu-id="ed31d-142">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-142">Int16</span></span>|  
|<span data-ttu-id="ed31d-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="ed31d-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="ed31d-144">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-144">Int16</span></span>|  
|<span data-ttu-id="ed31d-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="ed31d-145">COLUMN_NAME</span></span>|<span data-ttu-id="ed31d-146">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-146">String</span></span>|  
|<span data-ttu-id="ed31d-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="ed31d-147">ASC_OR_DESC</span></span>|<span data-ttu-id="ed31d-148">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-148">String</span></span>|  
|<span data-ttu-id="ed31d-149">CARDINATLITY</span><span class="sxs-lookup"><span data-stu-id="ed31d-149">CARDINATLITY</span></span>|<span data-ttu-id="ed31d-150">Int32</span><span class="sxs-lookup"><span data-stu-id="ed31d-150">Int32</span></span>|  
|<span data-ttu-id="ed31d-151">SAYFALARI</span><span class="sxs-lookup"><span data-stu-id="ed31d-151">PAGES</span></span>|<span data-ttu-id="ed31d-152">Int32</span><span class="sxs-lookup"><span data-stu-id="ed31d-152">Int32</span></span>|  
|<span data-ttu-id="ed31d-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="ed31d-153">FILTER_CONDITION</span></span>|<span data-ttu-id="ed31d-154">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-154">String</span></span>|  
|<span data-ttu-id="ed31d-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="ed31d-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="ed31d-156">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-156">String</span></span>|  
|<span data-ttu-id="ed31d-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ed31d-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="ed31d-158">Bayt</span><span class="sxs-lookup"><span data-stu-id="ed31d-158">Byte</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="ed31d-159">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="ed31d-159">Columns</span></span>  
  
|<span data-ttu-id="ed31d-160">columnName</span><span class="sxs-lookup"><span data-stu-id="ed31d-160">ColumnName</span></span>|<span data-ttu-id="ed31d-161">Veri türü</span><span class="sxs-lookup"><span data-stu-id="ed31d-161">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="ed31d-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="ed31d-162">TABLE_CAT</span></span>|<span data-ttu-id="ed31d-163">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-163">String</span></span>|  
|<span data-ttu-id="ed31d-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="ed31d-164">TABLE_SCHEM</span></span>|<span data-ttu-id="ed31d-165">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-165">String</span></span>|  
|<span data-ttu-id="ed31d-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="ed31d-166">TABLE_NAME</span></span>|<span data-ttu-id="ed31d-167">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-167">String</span></span>|  
|<span data-ttu-id="ed31d-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="ed31d-168">COLUMN_NAME</span></span>|<span data-ttu-id="ed31d-169">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-169">String</span></span>|  
|<span data-ttu-id="ed31d-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ed31d-170">DATA_TYPE</span></span>|<span data-ttu-id="ed31d-171">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-171">Int16</span></span>|  
|<span data-ttu-id="ed31d-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="ed31d-172">TYPE_NAME</span></span>|<span data-ttu-id="ed31d-173">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-173">String</span></span>|  
|<span data-ttu-id="ed31d-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="ed31d-174">COLUMN_SIZE</span></span>|<span data-ttu-id="ed31d-175">Int32</span><span class="sxs-lookup"><span data-stu-id="ed31d-175">Int32</span></span>|  
|<span data-ttu-id="ed31d-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="ed31d-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="ed31d-177">Int32</span><span class="sxs-lookup"><span data-stu-id="ed31d-177">Int32</span></span>|  
|<span data-ttu-id="ed31d-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="ed31d-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="ed31d-179">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-179">Int16</span></span>|  
|<span data-ttu-id="ed31d-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="ed31d-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="ed31d-181">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-181">Int16</span></span>|  
|<span data-ttu-id="ed31d-182">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="ed31d-182">NULLABLE</span></span>|<span data-ttu-id="ed31d-183">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-183">Int16</span></span>|  
|<span data-ttu-id="ed31d-184">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="ed31d-184">REMARKS</span></span>|<span data-ttu-id="ed31d-185">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-185">String</span></span>|  
|<span data-ttu-id="ed31d-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="ed31d-186">COLUMN_DEF</span></span>|<span data-ttu-id="ed31d-187">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-187">String</span></span>|  
|<span data-ttu-id="ed31d-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ed31d-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="ed31d-189">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-189">Int16</span></span>|  
|<span data-ttu-id="ed31d-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="ed31d-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="ed31d-191">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-191">Int16</span></span>|  
|<span data-ttu-id="ed31d-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="ed31d-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="ed31d-193">Int32</span><span class="sxs-lookup"><span data-stu-id="ed31d-193">Int32</span></span>|  
|<span data-ttu-id="ed31d-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="ed31d-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="ed31d-195">Int32</span><span class="sxs-lookup"><span data-stu-id="ed31d-195">Int32</span></span>|  
|<span data-ttu-id="ed31d-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="ed31d-196">IS_NULLABLE</span></span>|<span data-ttu-id="ed31d-197">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-197">String</span></span>|  
|<span data-ttu-id="ed31d-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="ed31d-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="ed31d-199">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-199">String</span></span>|  
|<span data-ttu-id="ed31d-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="ed31d-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="ed31d-201">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-201">String</span></span>|  
|<span data-ttu-id="ed31d-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ed31d-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="ed31d-203">Bayt</span><span class="sxs-lookup"><span data-stu-id="ed31d-203">Byte</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="ed31d-204">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="ed31d-204">Procedures</span></span>  
  
|<span data-ttu-id="ed31d-205">columnName</span><span class="sxs-lookup"><span data-stu-id="ed31d-205">ColumnName</span></span>|<span data-ttu-id="ed31d-206">Veri türü</span><span class="sxs-lookup"><span data-stu-id="ed31d-206">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="ed31d-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="ed31d-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="ed31d-208">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-208">String</span></span>|  
|<span data-ttu-id="ed31d-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="ed31d-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="ed31d-210">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-210">String</span></span>|  
|<span data-ttu-id="ed31d-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="ed31d-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="ed31d-212">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-212">String</span></span>|  
|<span data-ttu-id="ed31d-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="ed31d-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="ed31d-214">Int32</span><span class="sxs-lookup"><span data-stu-id="ed31d-214">Int32</span></span>|  
|<span data-ttu-id="ed31d-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="ed31d-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="ed31d-216">Int32</span><span class="sxs-lookup"><span data-stu-id="ed31d-216">Int32</span></span>|  
|<span data-ttu-id="ed31d-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="ed31d-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="ed31d-218">Int32</span><span class="sxs-lookup"><span data-stu-id="ed31d-218">Int32</span></span>|  
|<span data-ttu-id="ed31d-219">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="ed31d-219">REMARKS</span></span>|<span data-ttu-id="ed31d-220">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-220">String</span></span>|  
|<span data-ttu-id="ed31d-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="ed31d-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="ed31d-222">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-222">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="ed31d-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="ed31d-223">ProcedureColumns</span></span>  
  
|<span data-ttu-id="ed31d-224">columnName</span><span class="sxs-lookup"><span data-stu-id="ed31d-224">ColumnName</span></span>|<span data-ttu-id="ed31d-225">Veri türü</span><span class="sxs-lookup"><span data-stu-id="ed31d-225">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="ed31d-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="ed31d-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="ed31d-227">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-227">String</span></span>|  
|<span data-ttu-id="ed31d-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="ed31d-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="ed31d-229">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-229">String</span></span>|  
|<span data-ttu-id="ed31d-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="ed31d-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="ed31d-231">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-231">String</span></span>|  
|<span data-ttu-id="ed31d-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="ed31d-232">COLUMN_NAME</span></span>|<span data-ttu-id="ed31d-233">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-233">String</span></span>|  
|<span data-ttu-id="ed31d-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="ed31d-234">COLUMN_TYPE</span></span>|<span data-ttu-id="ed31d-235">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-235">Int16</span></span>|  
|<span data-ttu-id="ed31d-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ed31d-236">DATA_TYPE</span></span>|<span data-ttu-id="ed31d-237">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-237">Int16</span></span>|  
|<span data-ttu-id="ed31d-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="ed31d-238">TYPE_NAME</span></span>|<span data-ttu-id="ed31d-239">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-239">String</span></span>|  
|<span data-ttu-id="ed31d-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="ed31d-240">COLUMN_SIZE</span></span>|<span data-ttu-id="ed31d-241">Int32</span><span class="sxs-lookup"><span data-stu-id="ed31d-241">Int32</span></span>|  
|<span data-ttu-id="ed31d-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="ed31d-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="ed31d-243">Int32</span><span class="sxs-lookup"><span data-stu-id="ed31d-243">Int32</span></span>|  
|<span data-ttu-id="ed31d-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="ed31d-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="ed31d-245">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-245">Int16</span></span>|  
|<span data-ttu-id="ed31d-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="ed31d-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="ed31d-247">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-247">Int16</span></span>|  
|<span data-ttu-id="ed31d-248">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="ed31d-248">NULLABLE</span></span>|<span data-ttu-id="ed31d-249">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-249">Int16</span></span>|  
|<span data-ttu-id="ed31d-250">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="ed31d-250">REMARKS</span></span>|<span data-ttu-id="ed31d-251">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-251">String</span></span>|  
|<span data-ttu-id="ed31d-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="ed31d-252">COLUMN_DEF</span></span>|<span data-ttu-id="ed31d-253">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-253">String</span></span>|  
|<span data-ttu-id="ed31d-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ed31d-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="ed31d-255">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-255">Int16</span></span>|  
|<span data-ttu-id="ed31d-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="ed31d-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="ed31d-257">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-257">Int16</span></span>|  
|<span data-ttu-id="ed31d-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="ed31d-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="ed31d-259">Int32</span><span class="sxs-lookup"><span data-stu-id="ed31d-259">Int32</span></span>|  
|<span data-ttu-id="ed31d-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="ed31d-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="ed31d-261">Int32</span><span class="sxs-lookup"><span data-stu-id="ed31d-261">Int32</span></span>|  
|<span data-ttu-id="ed31d-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="ed31d-262">IS_NULLABLE</span></span>|<span data-ttu-id="ed31d-263">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-263">String</span></span>|  
|<span data-ttu-id="ed31d-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="ed31d-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="ed31d-265">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-265">String</span></span>|  
|<span data-ttu-id="ed31d-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="ed31d-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="ed31d-267">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-267">String</span></span>|  
|<span data-ttu-id="ed31d-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ed31d-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="ed31d-269">Bayt</span><span class="sxs-lookup"><span data-stu-id="ed31d-269">Byte</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="ed31d-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="ed31d-270">ProcedureParameters</span></span>  
  
|<span data-ttu-id="ed31d-271">columnName</span><span class="sxs-lookup"><span data-stu-id="ed31d-271">ColumnName</span></span>|<span data-ttu-id="ed31d-272">Veri türü</span><span class="sxs-lookup"><span data-stu-id="ed31d-272">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="ed31d-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="ed31d-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="ed31d-274">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-274">String</span></span>|  
|<span data-ttu-id="ed31d-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="ed31d-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="ed31d-276">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-276">String</span></span>|  
|<span data-ttu-id="ed31d-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="ed31d-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="ed31d-278">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-278">String</span></span>|  
|<span data-ttu-id="ed31d-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="ed31d-279">COLUMN_NAME</span></span>|<span data-ttu-id="ed31d-280">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-280">String</span></span>|  
|<span data-ttu-id="ed31d-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="ed31d-281">COLUMN_TYPE</span></span>|<span data-ttu-id="ed31d-282">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-282">Int16</span></span>|  
|<span data-ttu-id="ed31d-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ed31d-283">DATA_TYPE</span></span>|<span data-ttu-id="ed31d-284">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-284">Int16</span></span>|  
|<span data-ttu-id="ed31d-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="ed31d-285">TYPE_NAME</span></span>|<span data-ttu-id="ed31d-286">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-286">String</span></span>|  
|<span data-ttu-id="ed31d-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="ed31d-287">COLUMN_SIZE</span></span>|<span data-ttu-id="ed31d-288">Int32</span><span class="sxs-lookup"><span data-stu-id="ed31d-288">Int32</span></span>|  
|<span data-ttu-id="ed31d-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="ed31d-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="ed31d-290">Int32</span><span class="sxs-lookup"><span data-stu-id="ed31d-290">Int32</span></span>|  
|<span data-ttu-id="ed31d-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="ed31d-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="ed31d-292">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-292">Int16</span></span>|  
|<span data-ttu-id="ed31d-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="ed31d-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="ed31d-294">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-294">Int16</span></span>|  
|<span data-ttu-id="ed31d-295">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="ed31d-295">NULLABLE</span></span>|<span data-ttu-id="ed31d-296">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-296">Int16</span></span>|  
|<span data-ttu-id="ed31d-297">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="ed31d-297">REMARKS</span></span>|<span data-ttu-id="ed31d-298">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-298">String</span></span>|  
|<span data-ttu-id="ed31d-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="ed31d-299">COLUMN_DEF</span></span>|<span data-ttu-id="ed31d-300">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-300">String</span></span>|  
|<span data-ttu-id="ed31d-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ed31d-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="ed31d-302">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-302">Int16</span></span>|  
|<span data-ttu-id="ed31d-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="ed31d-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="ed31d-304">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-304">Int16</span></span>|  
|<span data-ttu-id="ed31d-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="ed31d-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="ed31d-306">Int32</span><span class="sxs-lookup"><span data-stu-id="ed31d-306">Int32</span></span>|  
|<span data-ttu-id="ed31d-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="ed31d-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="ed31d-308">Int32</span><span class="sxs-lookup"><span data-stu-id="ed31d-308">Int32</span></span>|  
|<span data-ttu-id="ed31d-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="ed31d-309">IS_NULLABLE</span></span>|<span data-ttu-id="ed31d-310">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-310">String</span></span>|  
|<span data-ttu-id="ed31d-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="ed31d-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="ed31d-312">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-312">String</span></span>|  
|<span data-ttu-id="ed31d-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="ed31d-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="ed31d-314">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-314">String</span></span>|  
|<span data-ttu-id="ed31d-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ed31d-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="ed31d-316">Bayt</span><span class="sxs-lookup"><span data-stu-id="ed31d-316">Byte</span></span>|  
  
## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="ed31d-317">Microsoft Oracle ODBC sürücüsü</span><span class="sxs-lookup"><span data-stu-id="ed31d-317">Microsoft Oracle ODBC Driver</span></span>  
 <span data-ttu-id="ed31d-318">Microsoft SQL Server Oracle ODBC sürücüsü ortak şeması koleksiyonları ek olarak aşağıdaki belirli şeması koleksiyonları destekler:</span><span class="sxs-lookup"><span data-stu-id="ed31d-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="ed31d-319">tabloları</span><span class="sxs-lookup"><span data-stu-id="ed31d-319">Tables</span></span>  
  
-   <span data-ttu-id="ed31d-320">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="ed31d-320">Columns</span></span>  
  
-   <span data-ttu-id="ed31d-321">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="ed31d-321">Procedures</span></span>  
  
-   <span data-ttu-id="ed31d-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="ed31d-322">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="ed31d-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="ed31d-323">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="ed31d-324">Görünümler</span><span class="sxs-lookup"><span data-stu-id="ed31d-324">Views</span></span>  
  
-   <span data-ttu-id="ed31d-325">Dizinler</span><span class="sxs-lookup"><span data-stu-id="ed31d-325">Indexes</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="ed31d-326">Tabloları ve görünümleri</span><span class="sxs-lookup"><span data-stu-id="ed31d-326">Tables and Views</span></span>  
  
|<span data-ttu-id="ed31d-327">columnName</span><span class="sxs-lookup"><span data-stu-id="ed31d-327">ColumnName</span></span>|<span data-ttu-id="ed31d-328">Veri türü</span><span class="sxs-lookup"><span data-stu-id="ed31d-328">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="ed31d-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="ed31d-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="ed31d-330">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-330">String</span></span>|  
|<span data-ttu-id="ed31d-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="ed31d-331">TABLE_OWNER</span></span>|<span data-ttu-id="ed31d-332">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-332">String</span></span>|  
|<span data-ttu-id="ed31d-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="ed31d-333">TABLE_NAME</span></span>|<span data-ttu-id="ed31d-334">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-334">String</span></span>|  
|<span data-ttu-id="ed31d-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="ed31d-335">TABLE_TYPE</span></span>|<span data-ttu-id="ed31d-336">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-336">String</span></span>|  
|<span data-ttu-id="ed31d-337">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="ed31d-337">REMARKS</span></span>|<span data-ttu-id="ed31d-338">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-338">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="ed31d-339">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="ed31d-339">Columns</span></span>  
  
|<span data-ttu-id="ed31d-340">columnName</span><span class="sxs-lookup"><span data-stu-id="ed31d-340">ColumnName</span></span>|<span data-ttu-id="ed31d-341">Veri türü</span><span class="sxs-lookup"><span data-stu-id="ed31d-341">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="ed31d-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="ed31d-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="ed31d-343">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-343">String</span></span>|  
|<span data-ttu-id="ed31d-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="ed31d-344">TABLE_OWNER</span></span>|<span data-ttu-id="ed31d-345">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-345">String</span></span>|  
|<span data-ttu-id="ed31d-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="ed31d-346">TABLE_NAME</span></span>|<span data-ttu-id="ed31d-347">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-347">String</span></span>|  
|<span data-ttu-id="ed31d-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="ed31d-348">COLUMN_NAME</span></span>|<span data-ttu-id="ed31d-349">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-349">String</span></span>|  
|<span data-ttu-id="ed31d-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ed31d-350">DATA_TYPE</span></span>|<span data-ttu-id="ed31d-351">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-351">Int16</span></span>|  
|<span data-ttu-id="ed31d-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="ed31d-352">TYPE_NAME</span></span>|<span data-ttu-id="ed31d-353">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-353">String</span></span>|  
|<span data-ttu-id="ed31d-354">DUYARLILIK</span><span class="sxs-lookup"><span data-stu-id="ed31d-354">PRECISION</span></span>|<span data-ttu-id="ed31d-355">Int32</span><span class="sxs-lookup"><span data-stu-id="ed31d-355">Int32</span></span>|  
|<span data-ttu-id="ed31d-356">UZUNLUĞU</span><span class="sxs-lookup"><span data-stu-id="ed31d-356">LENGTH</span></span>|<span data-ttu-id="ed31d-357">Int32</span><span class="sxs-lookup"><span data-stu-id="ed31d-357">Int32</span></span>|  
|<span data-ttu-id="ed31d-358">ÖLÇEK</span><span class="sxs-lookup"><span data-stu-id="ed31d-358">SCALE</span></span>|<span data-ttu-id="ed31d-359">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-359">Int16</span></span>|  
|<span data-ttu-id="ed31d-360">SAYI TABANINI</span><span class="sxs-lookup"><span data-stu-id="ed31d-360">RADIX</span></span>|<span data-ttu-id="ed31d-361">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-361">Int16</span></span>|  
|<span data-ttu-id="ed31d-362">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="ed31d-362">NULLABLE</span></span>|<span data-ttu-id="ed31d-363">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-363">Int16</span></span>|  
|<span data-ttu-id="ed31d-364">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="ed31d-364">REMARKS</span></span>|<span data-ttu-id="ed31d-365">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-365">String</span></span>|  
|<span data-ttu-id="ed31d-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="ed31d-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="ed31d-367">Int32</span><span class="sxs-lookup"><span data-stu-id="ed31d-367">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="ed31d-368">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="ed31d-368">Procedures</span></span>  
  
|<span data-ttu-id="ed31d-369">columnName</span><span class="sxs-lookup"><span data-stu-id="ed31d-369">ColumnName</span></span>|<span data-ttu-id="ed31d-370">Veri türü</span><span class="sxs-lookup"><span data-stu-id="ed31d-370">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="ed31d-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="ed31d-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="ed31d-372">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-372">String</span></span>|  
|<span data-ttu-id="ed31d-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="ed31d-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="ed31d-374">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-374">String</span></span>|  
|<span data-ttu-id="ed31d-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="ed31d-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="ed31d-376">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-376">String</span></span>|  
|<span data-ttu-id="ed31d-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="ed31d-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="ed31d-378">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-378">Int16</span></span>|  
|<span data-ttu-id="ed31d-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="ed31d-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="ed31d-380">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-380">Int16</span></span>|  
|<span data-ttu-id="ed31d-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="ed31d-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="ed31d-382">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-382">Int16</span></span>|  
|<span data-ttu-id="ed31d-383">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="ed31d-383">REMARKS</span></span>|<span data-ttu-id="ed31d-384">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-384">String</span></span>|  
|<span data-ttu-id="ed31d-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="ed31d-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="ed31d-386">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-386">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="ed31d-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="ed31d-387">ProcedureColumns</span></span>  
  
|<span data-ttu-id="ed31d-388">columnName</span><span class="sxs-lookup"><span data-stu-id="ed31d-388">ColumnName</span></span>|<span data-ttu-id="ed31d-389">Veri türü</span><span class="sxs-lookup"><span data-stu-id="ed31d-389">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="ed31d-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="ed31d-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="ed31d-391">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-391">String</span></span>|  
|<span data-ttu-id="ed31d-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="ed31d-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="ed31d-393">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-393">String</span></span>|  
|<span data-ttu-id="ed31d-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="ed31d-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="ed31d-395">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-395">String</span></span>|  
|<span data-ttu-id="ed31d-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="ed31d-396">COLUMN_NAME</span></span>|<span data-ttu-id="ed31d-397">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-397">String</span></span>|  
|<span data-ttu-id="ed31d-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="ed31d-398">COLUMN_TYPE</span></span>|<span data-ttu-id="ed31d-399">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-399">Int16</span></span>|  
|<span data-ttu-id="ed31d-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ed31d-400">DATA_TYPE</span></span>|<span data-ttu-id="ed31d-401">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-401">Int16</span></span>|  
|<span data-ttu-id="ed31d-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="ed31d-402">TYPE_NAME</span></span>|<span data-ttu-id="ed31d-403">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-403">String</span></span>|  
|<span data-ttu-id="ed31d-404">DUYARLILIK</span><span class="sxs-lookup"><span data-stu-id="ed31d-404">PRECISION</span></span>|<span data-ttu-id="ed31d-405">Int32</span><span class="sxs-lookup"><span data-stu-id="ed31d-405">Int32</span></span>|  
|<span data-ttu-id="ed31d-406">UZUNLUĞU</span><span class="sxs-lookup"><span data-stu-id="ed31d-406">LENGTH</span></span>|<span data-ttu-id="ed31d-407">Int32</span><span class="sxs-lookup"><span data-stu-id="ed31d-407">Int32</span></span>|  
|<span data-ttu-id="ed31d-408">ÖLÇEK</span><span class="sxs-lookup"><span data-stu-id="ed31d-408">SCALE</span></span>|<span data-ttu-id="ed31d-409">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-409">Int16</span></span>|  
|<span data-ttu-id="ed31d-410">SAYI TABANINI</span><span class="sxs-lookup"><span data-stu-id="ed31d-410">RADIX</span></span>|<span data-ttu-id="ed31d-411">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-411">Int16</span></span>|  
|<span data-ttu-id="ed31d-412">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="ed31d-412">NULLABLE</span></span>|<span data-ttu-id="ed31d-413">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-413">Int16</span></span>|  
|<span data-ttu-id="ed31d-414">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="ed31d-414">REMARKS</span></span>|<span data-ttu-id="ed31d-415">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-415">String</span></span>|  
|<span data-ttu-id="ed31d-416">AŞIRI YÜKLEME</span><span class="sxs-lookup"><span data-stu-id="ed31d-416">OVERLOAD</span></span>|<span data-ttu-id="ed31d-417">Int32</span><span class="sxs-lookup"><span data-stu-id="ed31d-417">Int32</span></span>|  
|<span data-ttu-id="ed31d-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="ed31d-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="ed31d-419">Int32</span><span class="sxs-lookup"><span data-stu-id="ed31d-419">Int32</span></span>|  
  
## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="ed31d-420">Microsoft Jet ODBC sürücüsü</span><span class="sxs-lookup"><span data-stu-id="ed31d-420">Microsoft Jet ODBC Driver</span></span>  
 <span data-ttu-id="ed31d-421">Microsoft Jet ODBC sürücüsü ortak şeması koleksiyonları ek olarak aşağıdaki belirli şeması koleksiyonları destekler:</span><span class="sxs-lookup"><span data-stu-id="ed31d-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="ed31d-422">tabloları</span><span class="sxs-lookup"><span data-stu-id="ed31d-422">Tables</span></span>  
  
-   <span data-ttu-id="ed31d-423">Dizinler</span><span class="sxs-lookup"><span data-stu-id="ed31d-423">Indexes</span></span>  
  
-   <span data-ttu-id="ed31d-424">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="ed31d-424">Columns</span></span>  
  
-   <span data-ttu-id="ed31d-425">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="ed31d-425">Procedures</span></span>  
  
-   <span data-ttu-id="ed31d-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="ed31d-426">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="ed31d-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="ed31d-427">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="ed31d-428">Görünümler</span><span class="sxs-lookup"><span data-stu-id="ed31d-428">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="ed31d-429">Tabloları ve görünümleri</span><span class="sxs-lookup"><span data-stu-id="ed31d-429">Tables and Views</span></span>  
  
|<span data-ttu-id="ed31d-430">columnName</span><span class="sxs-lookup"><span data-stu-id="ed31d-430">ColumnName</span></span>|<span data-ttu-id="ed31d-431">Veri türü</span><span class="sxs-lookup"><span data-stu-id="ed31d-431">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="ed31d-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="ed31d-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="ed31d-433">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-433">String</span></span>|  
|<span data-ttu-id="ed31d-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="ed31d-434">TABLE_OWNER</span></span>|<span data-ttu-id="ed31d-435">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-435">String</span></span>|  
|<span data-ttu-id="ed31d-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="ed31d-436">TABLE_NAME</span></span>|<span data-ttu-id="ed31d-437">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-437">String</span></span>|  
|<span data-ttu-id="ed31d-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="ed31d-438">TABLE_TYPE</span></span>|<span data-ttu-id="ed31d-439">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-439">String</span></span>|  
|<span data-ttu-id="ed31d-440">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="ed31d-440">REMARKS</span></span>|<span data-ttu-id="ed31d-441">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-441">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="ed31d-442">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="ed31d-442">Columns</span></span>  
  
|<span data-ttu-id="ed31d-443">columnName</span><span class="sxs-lookup"><span data-stu-id="ed31d-443">ColumnName</span></span>|<span data-ttu-id="ed31d-444">Veri türü</span><span class="sxs-lookup"><span data-stu-id="ed31d-444">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="ed31d-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="ed31d-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="ed31d-446">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-446">String</span></span>|  
|<span data-ttu-id="ed31d-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="ed31d-447">TABLE_OWNER</span></span>|<span data-ttu-id="ed31d-448">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-448">String</span></span>|  
|<span data-ttu-id="ed31d-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="ed31d-449">TABLE_NAME</span></span>|<span data-ttu-id="ed31d-450">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-450">String</span></span>|  
|<span data-ttu-id="ed31d-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="ed31d-451">COLUMN_NAME</span></span>|<span data-ttu-id="ed31d-452">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-452">String</span></span>|  
|<span data-ttu-id="ed31d-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ed31d-453">DATA_TYPE</span></span>|<span data-ttu-id="ed31d-454">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-454">Int16</span></span>|  
|<span data-ttu-id="ed31d-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="ed31d-455">TYPE_NAME</span></span>|<span data-ttu-id="ed31d-456">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-456">String</span></span>|  
|<span data-ttu-id="ed31d-457">DUYARLILIK</span><span class="sxs-lookup"><span data-stu-id="ed31d-457">PRECISION</span></span>|<span data-ttu-id="ed31d-458">Int32</span><span class="sxs-lookup"><span data-stu-id="ed31d-458">Int32</span></span>|  
|<span data-ttu-id="ed31d-459">UZUNLUĞU</span><span class="sxs-lookup"><span data-stu-id="ed31d-459">LENGTH</span></span>|<span data-ttu-id="ed31d-460">Int32</span><span class="sxs-lookup"><span data-stu-id="ed31d-460">Int32</span></span>|  
|<span data-ttu-id="ed31d-461">ÖLÇEK</span><span class="sxs-lookup"><span data-stu-id="ed31d-461">SCALE</span></span>|<span data-ttu-id="ed31d-462">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-462">Int16</span></span>|  
|<span data-ttu-id="ed31d-463">SAYI TABANINI</span><span class="sxs-lookup"><span data-stu-id="ed31d-463">RADIX</span></span>|<span data-ttu-id="ed31d-464">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-464">Int16</span></span>|  
|<span data-ttu-id="ed31d-465">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="ed31d-465">NULLABLE</span></span>|<span data-ttu-id="ed31d-466">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-466">Int16</span></span>|  
|<span data-ttu-id="ed31d-467">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="ed31d-467">REMARKS</span></span>|<span data-ttu-id="ed31d-468">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-468">String</span></span>|  
|<span data-ttu-id="ed31d-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="ed31d-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="ed31d-470">Int32</span><span class="sxs-lookup"><span data-stu-id="ed31d-470">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="ed31d-471">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="ed31d-471">Procedures</span></span>  
  
|<span data-ttu-id="ed31d-472">columnName</span><span class="sxs-lookup"><span data-stu-id="ed31d-472">ColumnName</span></span>|<span data-ttu-id="ed31d-473">Veri türü</span><span class="sxs-lookup"><span data-stu-id="ed31d-473">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="ed31d-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="ed31d-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="ed31d-475">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-475">String</span></span>|  
|<span data-ttu-id="ed31d-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="ed31d-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="ed31d-477">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-477">String</span></span>|  
|<span data-ttu-id="ed31d-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="ed31d-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="ed31d-479">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-479">String</span></span>|  
|<span data-ttu-id="ed31d-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="ed31d-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="ed31d-481">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-481">Int16</span></span>|  
|<span data-ttu-id="ed31d-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="ed31d-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="ed31d-483">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-483">Int16</span></span>|  
|<span data-ttu-id="ed31d-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="ed31d-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="ed31d-485">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-485">Int16</span></span>|  
|<span data-ttu-id="ed31d-486">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="ed31d-486">REMARKS</span></span>|<span data-ttu-id="ed31d-487">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-487">String</span></span>|  
|<span data-ttu-id="ed31d-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="ed31d-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="ed31d-489">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-489">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="ed31d-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="ed31d-490">ProcedureColumns</span></span>  
  
|<span data-ttu-id="ed31d-491">columnName</span><span class="sxs-lookup"><span data-stu-id="ed31d-491">ColumnName</span></span>|<span data-ttu-id="ed31d-492">Veri türü</span><span class="sxs-lookup"><span data-stu-id="ed31d-492">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="ed31d-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="ed31d-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="ed31d-494">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-494">String</span></span>|  
|<span data-ttu-id="ed31d-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="ed31d-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="ed31d-496">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-496">String</span></span>|  
|<span data-ttu-id="ed31d-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="ed31d-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="ed31d-498">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-498">String</span></span>|  
|<span data-ttu-id="ed31d-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="ed31d-499">COLUMN_NAME</span></span>|<span data-ttu-id="ed31d-500">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-500">String</span></span>|  
|<span data-ttu-id="ed31d-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="ed31d-501">COLUMN_TYPE</span></span>|<span data-ttu-id="ed31d-502">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-502">Int16</span></span>|  
|<span data-ttu-id="ed31d-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ed31d-503">DATA_TYPE</span></span>|<span data-ttu-id="ed31d-504">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-504">Int16</span></span>|  
|<span data-ttu-id="ed31d-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="ed31d-505">TYPE_NAME</span></span>|<span data-ttu-id="ed31d-506">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-506">String</span></span>|  
|<span data-ttu-id="ed31d-507">DUYARLILIK</span><span class="sxs-lookup"><span data-stu-id="ed31d-507">PRECISION</span></span>|<span data-ttu-id="ed31d-508">Int32</span><span class="sxs-lookup"><span data-stu-id="ed31d-508">Int32</span></span>|  
|<span data-ttu-id="ed31d-509">UZUNLUĞU</span><span class="sxs-lookup"><span data-stu-id="ed31d-509">LENGTH</span></span>|<span data-ttu-id="ed31d-510">Int32</span><span class="sxs-lookup"><span data-stu-id="ed31d-510">Int32</span></span>|  
|<span data-ttu-id="ed31d-511">ÖLÇEK</span><span class="sxs-lookup"><span data-stu-id="ed31d-511">SCALE</span></span>|<span data-ttu-id="ed31d-512">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-512">Int16</span></span>|  
|<span data-ttu-id="ed31d-513">SAYI TABANINI</span><span class="sxs-lookup"><span data-stu-id="ed31d-513">RADIX</span></span>|<span data-ttu-id="ed31d-514">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-514">Int16</span></span>|  
|<span data-ttu-id="ed31d-515">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="ed31d-515">NULLABLE</span></span>|<span data-ttu-id="ed31d-516">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-516">Int16</span></span>|  
|<span data-ttu-id="ed31d-517">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="ed31d-517">REMARKS</span></span>|<span data-ttu-id="ed31d-518">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-518">String</span></span>|  
|<span data-ttu-id="ed31d-519">AŞIRI YÜKLEME</span><span class="sxs-lookup"><span data-stu-id="ed31d-519">OVERLOAD</span></span>|<span data-ttu-id="ed31d-520">Int32</span><span class="sxs-lookup"><span data-stu-id="ed31d-520">Int32</span></span>|  
|<span data-ttu-id="ed31d-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="ed31d-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="ed31d-522">Int32</span><span class="sxs-lookup"><span data-stu-id="ed31d-522">Int32</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="ed31d-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="ed31d-523">ProcedureParameters</span></span>  
  
|<span data-ttu-id="ed31d-524">columnName</span><span class="sxs-lookup"><span data-stu-id="ed31d-524">ColumnName</span></span>|<span data-ttu-id="ed31d-525">Veri türü</span><span class="sxs-lookup"><span data-stu-id="ed31d-525">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="ed31d-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="ed31d-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="ed31d-527">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-527">String</span></span>|  
|<span data-ttu-id="ed31d-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="ed31d-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="ed31d-529">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-529">String</span></span>|  
|<span data-ttu-id="ed31d-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="ed31d-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="ed31d-531">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-531">String</span></span>|  
|<span data-ttu-id="ed31d-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="ed31d-532">COLUMN_NAME</span></span>|<span data-ttu-id="ed31d-533">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-533">String</span></span>|  
|<span data-ttu-id="ed31d-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="ed31d-534">COLUMN_TYPE</span></span>|<span data-ttu-id="ed31d-535">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-535">Int16</span></span>|  
|<span data-ttu-id="ed31d-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ed31d-536">DATA_TYPE</span></span>|<span data-ttu-id="ed31d-537">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-537">Int16</span></span>|  
|<span data-ttu-id="ed31d-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="ed31d-538">TYPE_NAME</span></span>|<span data-ttu-id="ed31d-539">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-539">String</span></span>|  
|<span data-ttu-id="ed31d-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="ed31d-540">COLUMN_SIZE</span></span>|<span data-ttu-id="ed31d-541">Int32</span><span class="sxs-lookup"><span data-stu-id="ed31d-541">Int32</span></span>|  
|<span data-ttu-id="ed31d-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="ed31d-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="ed31d-543">Int32</span><span class="sxs-lookup"><span data-stu-id="ed31d-543">Int32</span></span>|  
|<span data-ttu-id="ed31d-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="ed31d-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="ed31d-545">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-545">Int16</span></span>|  
|<span data-ttu-id="ed31d-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="ed31d-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="ed31d-547">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-547">Int16</span></span>|  
|<span data-ttu-id="ed31d-548">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="ed31d-548">NULLABLE</span></span>|<span data-ttu-id="ed31d-549">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-549">Int16</span></span>|  
|<span data-ttu-id="ed31d-550">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="ed31d-550">REMARKS</span></span>|<span data-ttu-id="ed31d-551">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-551">String</span></span>|  
|<span data-ttu-id="ed31d-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="ed31d-552">COLUMN_DEF</span></span>|<span data-ttu-id="ed31d-553">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-553">String</span></span>|  
|<span data-ttu-id="ed31d-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ed31d-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="ed31d-555">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-555">Int16</span></span>|  
|<span data-ttu-id="ed31d-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="ed31d-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="ed31d-557">Int16</span><span class="sxs-lookup"><span data-stu-id="ed31d-557">Int16</span></span>|  
|<span data-ttu-id="ed31d-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="ed31d-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="ed31d-559">Int32</span><span class="sxs-lookup"><span data-stu-id="ed31d-559">Int32</span></span>|  
|<span data-ttu-id="ed31d-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="ed31d-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="ed31d-561">Int32</span><span class="sxs-lookup"><span data-stu-id="ed31d-561">Int32</span></span>|  
|<span data-ttu-id="ed31d-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="ed31d-562">IS_NULLABLE</span></span>|<span data-ttu-id="ed31d-563">Dize</span><span class="sxs-lookup"><span data-stu-id="ed31d-563">String</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ed31d-564">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ed31d-564">See Also</span></span>  
 [<span data-ttu-id="ed31d-565">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="ed31d-565">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
