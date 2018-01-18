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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 45cfed80decc2336c5a2bacf24fd075c2b81c531
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="3d11b-102">ODBC şeması koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="3d11b-102">ODBC Schema Collections</span></span>
<span data-ttu-id="3d11b-103">Bu bölümde, Microsoft SQL Server, Oracle ve Microsoft Jet ODBC sürücüleri için şema koleksiyonu desteği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3d11b-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="3d11b-104">Microsoft SQL Server ODBC sürücüsü</span><span class="sxs-lookup"><span data-stu-id="3d11b-104">Microsoft SQL Server ODBC Driver</span></span>  
 <span data-ttu-id="3d11b-105">Microsoft SQL Server ODBC sürücüsü ortak şeması koleksiyonları ek olarak aşağıdaki belirli şeması koleksiyonları destekler:</span><span class="sxs-lookup"><span data-stu-id="3d11b-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="3d11b-106">tabloları</span><span class="sxs-lookup"><span data-stu-id="3d11b-106">Tables</span></span>  
  
-   <span data-ttu-id="3d11b-107">Dizinler</span><span class="sxs-lookup"><span data-stu-id="3d11b-107">Indexes</span></span>  
  
-   <span data-ttu-id="3d11b-108">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="3d11b-108">Columns</span></span>  
  
-   <span data-ttu-id="3d11b-109">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="3d11b-109">Procedures</span></span>  
  
-   <span data-ttu-id="3d11b-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="3d11b-110">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="3d11b-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="3d11b-111">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="3d11b-112">Görünümler</span><span class="sxs-lookup"><span data-stu-id="3d11b-112">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="3d11b-113">Tabloları ve görünümleri</span><span class="sxs-lookup"><span data-stu-id="3d11b-113">Tables and Views</span></span>  
  
|<span data-ttu-id="3d11b-114">columnName</span><span class="sxs-lookup"><span data-stu-id="3d11b-114">ColumnName</span></span>|<span data-ttu-id="3d11b-115">Veri türü</span><span class="sxs-lookup"><span data-stu-id="3d11b-115">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="3d11b-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="3d11b-116">TABLE_CAT</span></span>|<span data-ttu-id="3d11b-117">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-117">String</span></span>|  
|<span data-ttu-id="3d11b-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="3d11b-118">TABLE_SCHEM</span></span>|<span data-ttu-id="3d11b-119">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-119">String</span></span>|  
|<span data-ttu-id="3d11b-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="3d11b-120">TABLE_NAME</span></span>|<span data-ttu-id="3d11b-121">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-121">String</span></span>|  
|<span data-ttu-id="3d11b-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="3d11b-122">TABLE_TYPE</span></span>|<span data-ttu-id="3d11b-123">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-123">String</span></span>|  
|<span data-ttu-id="3d11b-124">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="3d11b-124">REMARKS</span></span>|<span data-ttu-id="3d11b-125">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-125">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="3d11b-126">Dizinler</span><span class="sxs-lookup"><span data-stu-id="3d11b-126">Indexes</span></span>  
  
|<span data-ttu-id="3d11b-127">columnName</span><span class="sxs-lookup"><span data-stu-id="3d11b-127">ColumnName</span></span>|<span data-ttu-id="3d11b-128">Veri türü</span><span class="sxs-lookup"><span data-stu-id="3d11b-128">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="3d11b-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="3d11b-129">TABLE_CAT</span></span>|<span data-ttu-id="3d11b-130">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-130">String</span></span>|  
|<span data-ttu-id="3d11b-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="3d11b-131">TABLE_SCHEM</span></span>|<span data-ttu-id="3d11b-132">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-132">String</span></span>|  
|<span data-ttu-id="3d11b-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="3d11b-133">TABLE_NAME</span></span>|<span data-ttu-id="3d11b-134">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-134">String</span></span>|  
|<span data-ttu-id="3d11b-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="3d11b-135">NON_UNIQUE</span></span>|<span data-ttu-id="3d11b-136">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-136">Int16</span></span>|  
|<span data-ttu-id="3d11b-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="3d11b-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="3d11b-138">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-138">String</span></span>|  
|<span data-ttu-id="3d11b-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="3d11b-139">INDEX_NAME</span></span>|<span data-ttu-id="3d11b-140">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-140">String</span></span>|  
|<span data-ttu-id="3d11b-141">TÜRÜ</span><span class="sxs-lookup"><span data-stu-id="3d11b-141">TYPE</span></span>|<span data-ttu-id="3d11b-142">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-142">Int16</span></span>|  
|<span data-ttu-id="3d11b-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="3d11b-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="3d11b-144">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-144">Int16</span></span>|  
|<span data-ttu-id="3d11b-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="3d11b-145">COLUMN_NAME</span></span>|<span data-ttu-id="3d11b-146">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-146">String</span></span>|  
|<span data-ttu-id="3d11b-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="3d11b-147">ASC_OR_DESC</span></span>|<span data-ttu-id="3d11b-148">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-148">String</span></span>|  
|<span data-ttu-id="3d11b-149">CARDINATLITY</span><span class="sxs-lookup"><span data-stu-id="3d11b-149">CARDINATLITY</span></span>|<span data-ttu-id="3d11b-150">Int32</span><span class="sxs-lookup"><span data-stu-id="3d11b-150">Int32</span></span>|  
|<span data-ttu-id="3d11b-151">SAYFALARI</span><span class="sxs-lookup"><span data-stu-id="3d11b-151">PAGES</span></span>|<span data-ttu-id="3d11b-152">Int32</span><span class="sxs-lookup"><span data-stu-id="3d11b-152">Int32</span></span>|  
|<span data-ttu-id="3d11b-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="3d11b-153">FILTER_CONDITION</span></span>|<span data-ttu-id="3d11b-154">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-154">String</span></span>|  
|<span data-ttu-id="3d11b-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3d11b-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="3d11b-156">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-156">String</span></span>|  
|<span data-ttu-id="3d11b-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="3d11b-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="3d11b-158">Bayt</span><span class="sxs-lookup"><span data-stu-id="3d11b-158">Byte</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="3d11b-159">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="3d11b-159">Columns</span></span>  
  
|<span data-ttu-id="3d11b-160">columnName</span><span class="sxs-lookup"><span data-stu-id="3d11b-160">ColumnName</span></span>|<span data-ttu-id="3d11b-161">Veri türü</span><span class="sxs-lookup"><span data-stu-id="3d11b-161">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="3d11b-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="3d11b-162">TABLE_CAT</span></span>|<span data-ttu-id="3d11b-163">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-163">String</span></span>|  
|<span data-ttu-id="3d11b-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="3d11b-164">TABLE_SCHEM</span></span>|<span data-ttu-id="3d11b-165">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-165">String</span></span>|  
|<span data-ttu-id="3d11b-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="3d11b-166">TABLE_NAME</span></span>|<span data-ttu-id="3d11b-167">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-167">String</span></span>|  
|<span data-ttu-id="3d11b-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="3d11b-168">COLUMN_NAME</span></span>|<span data-ttu-id="3d11b-169">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-169">String</span></span>|  
|<span data-ttu-id="3d11b-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="3d11b-170">DATA_TYPE</span></span>|<span data-ttu-id="3d11b-171">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-171">Int16</span></span>|  
|<span data-ttu-id="3d11b-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="3d11b-172">TYPE_NAME</span></span>|<span data-ttu-id="3d11b-173">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-173">String</span></span>|  
|<span data-ttu-id="3d11b-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="3d11b-174">COLUMN_SIZE</span></span>|<span data-ttu-id="3d11b-175">Int32</span><span class="sxs-lookup"><span data-stu-id="3d11b-175">Int32</span></span>|  
|<span data-ttu-id="3d11b-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="3d11b-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="3d11b-177">Int32</span><span class="sxs-lookup"><span data-stu-id="3d11b-177">Int32</span></span>|  
|<span data-ttu-id="3d11b-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="3d11b-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="3d11b-179">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-179">Int16</span></span>|  
|<span data-ttu-id="3d11b-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="3d11b-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="3d11b-181">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-181">Int16</span></span>|  
|<span data-ttu-id="3d11b-182">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="3d11b-182">NULLABLE</span></span>|<span data-ttu-id="3d11b-183">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-183">Int16</span></span>|  
|<span data-ttu-id="3d11b-184">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="3d11b-184">REMARKS</span></span>|<span data-ttu-id="3d11b-185">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-185">String</span></span>|  
|<span data-ttu-id="3d11b-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="3d11b-186">COLUMN_DEF</span></span>|<span data-ttu-id="3d11b-187">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-187">String</span></span>|  
|<span data-ttu-id="3d11b-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="3d11b-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="3d11b-189">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-189">Int16</span></span>|  
|<span data-ttu-id="3d11b-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="3d11b-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="3d11b-191">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-191">Int16</span></span>|  
|<span data-ttu-id="3d11b-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="3d11b-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="3d11b-193">Int32</span><span class="sxs-lookup"><span data-stu-id="3d11b-193">Int32</span></span>|  
|<span data-ttu-id="3d11b-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="3d11b-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="3d11b-195">Int32</span><span class="sxs-lookup"><span data-stu-id="3d11b-195">Int32</span></span>|  
|<span data-ttu-id="3d11b-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="3d11b-196">IS_NULLABLE</span></span>|<span data-ttu-id="3d11b-197">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-197">String</span></span>|  
|<span data-ttu-id="3d11b-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3d11b-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="3d11b-199">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-199">String</span></span>|  
|<span data-ttu-id="3d11b-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3d11b-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="3d11b-201">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-201">String</span></span>|  
|<span data-ttu-id="3d11b-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="3d11b-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="3d11b-203">Bayt</span><span class="sxs-lookup"><span data-stu-id="3d11b-203">Byte</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="3d11b-204">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="3d11b-204">Procedures</span></span>  
  
|<span data-ttu-id="3d11b-205">columnName</span><span class="sxs-lookup"><span data-stu-id="3d11b-205">ColumnName</span></span>|<span data-ttu-id="3d11b-206">Veri türü</span><span class="sxs-lookup"><span data-stu-id="3d11b-206">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="3d11b-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="3d11b-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="3d11b-208">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-208">String</span></span>|  
|<span data-ttu-id="3d11b-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="3d11b-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="3d11b-210">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-210">String</span></span>|  
|<span data-ttu-id="3d11b-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="3d11b-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="3d11b-212">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-212">String</span></span>|  
|<span data-ttu-id="3d11b-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="3d11b-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="3d11b-214">Int32</span><span class="sxs-lookup"><span data-stu-id="3d11b-214">Int32</span></span>|  
|<span data-ttu-id="3d11b-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="3d11b-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="3d11b-216">Int32</span><span class="sxs-lookup"><span data-stu-id="3d11b-216">Int32</span></span>|  
|<span data-ttu-id="3d11b-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="3d11b-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="3d11b-218">Int32</span><span class="sxs-lookup"><span data-stu-id="3d11b-218">Int32</span></span>|  
|<span data-ttu-id="3d11b-219">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="3d11b-219">REMARKS</span></span>|<span data-ttu-id="3d11b-220">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-220">String</span></span>|  
|<span data-ttu-id="3d11b-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="3d11b-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="3d11b-222">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-222">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="3d11b-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="3d11b-223">ProcedureColumns</span></span>  
  
|<span data-ttu-id="3d11b-224">columnName</span><span class="sxs-lookup"><span data-stu-id="3d11b-224">ColumnName</span></span>|<span data-ttu-id="3d11b-225">Veri türü</span><span class="sxs-lookup"><span data-stu-id="3d11b-225">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="3d11b-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="3d11b-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="3d11b-227">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-227">String</span></span>|  
|<span data-ttu-id="3d11b-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="3d11b-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="3d11b-229">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-229">String</span></span>|  
|<span data-ttu-id="3d11b-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="3d11b-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="3d11b-231">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-231">String</span></span>|  
|<span data-ttu-id="3d11b-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="3d11b-232">COLUMN_NAME</span></span>|<span data-ttu-id="3d11b-233">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-233">String</span></span>|  
|<span data-ttu-id="3d11b-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="3d11b-234">COLUMN_TYPE</span></span>|<span data-ttu-id="3d11b-235">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-235">Int16</span></span>|  
|<span data-ttu-id="3d11b-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="3d11b-236">DATA_TYPE</span></span>|<span data-ttu-id="3d11b-237">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-237">Int16</span></span>|  
|<span data-ttu-id="3d11b-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="3d11b-238">TYPE_NAME</span></span>|<span data-ttu-id="3d11b-239">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-239">String</span></span>|  
|<span data-ttu-id="3d11b-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="3d11b-240">COLUMN_SIZE</span></span>|<span data-ttu-id="3d11b-241">Int32</span><span class="sxs-lookup"><span data-stu-id="3d11b-241">Int32</span></span>|  
|<span data-ttu-id="3d11b-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="3d11b-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="3d11b-243">Int32</span><span class="sxs-lookup"><span data-stu-id="3d11b-243">Int32</span></span>|  
|<span data-ttu-id="3d11b-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="3d11b-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="3d11b-245">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-245">Int16</span></span>|  
|<span data-ttu-id="3d11b-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="3d11b-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="3d11b-247">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-247">Int16</span></span>|  
|<span data-ttu-id="3d11b-248">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="3d11b-248">NULLABLE</span></span>|<span data-ttu-id="3d11b-249">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-249">Int16</span></span>|  
|<span data-ttu-id="3d11b-250">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="3d11b-250">REMARKS</span></span>|<span data-ttu-id="3d11b-251">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-251">String</span></span>|  
|<span data-ttu-id="3d11b-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="3d11b-252">COLUMN_DEF</span></span>|<span data-ttu-id="3d11b-253">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-253">String</span></span>|  
|<span data-ttu-id="3d11b-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="3d11b-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="3d11b-255">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-255">Int16</span></span>|  
|<span data-ttu-id="3d11b-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="3d11b-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="3d11b-257">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-257">Int16</span></span>|  
|<span data-ttu-id="3d11b-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="3d11b-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="3d11b-259">Int32</span><span class="sxs-lookup"><span data-stu-id="3d11b-259">Int32</span></span>|  
|<span data-ttu-id="3d11b-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="3d11b-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="3d11b-261">Int32</span><span class="sxs-lookup"><span data-stu-id="3d11b-261">Int32</span></span>|  
|<span data-ttu-id="3d11b-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="3d11b-262">IS_NULLABLE</span></span>|<span data-ttu-id="3d11b-263">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-263">String</span></span>|  
|<span data-ttu-id="3d11b-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3d11b-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="3d11b-265">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-265">String</span></span>|  
|<span data-ttu-id="3d11b-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3d11b-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="3d11b-267">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-267">String</span></span>|  
|<span data-ttu-id="3d11b-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="3d11b-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="3d11b-269">Bayt</span><span class="sxs-lookup"><span data-stu-id="3d11b-269">Byte</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="3d11b-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="3d11b-270">ProcedureParameters</span></span>  
  
|<span data-ttu-id="3d11b-271">columnName</span><span class="sxs-lookup"><span data-stu-id="3d11b-271">ColumnName</span></span>|<span data-ttu-id="3d11b-272">Veri türü</span><span class="sxs-lookup"><span data-stu-id="3d11b-272">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="3d11b-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="3d11b-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="3d11b-274">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-274">String</span></span>|  
|<span data-ttu-id="3d11b-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="3d11b-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="3d11b-276">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-276">String</span></span>|  
|<span data-ttu-id="3d11b-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="3d11b-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="3d11b-278">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-278">String</span></span>|  
|<span data-ttu-id="3d11b-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="3d11b-279">COLUMN_NAME</span></span>|<span data-ttu-id="3d11b-280">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-280">String</span></span>|  
|<span data-ttu-id="3d11b-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="3d11b-281">COLUMN_TYPE</span></span>|<span data-ttu-id="3d11b-282">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-282">Int16</span></span>|  
|<span data-ttu-id="3d11b-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="3d11b-283">DATA_TYPE</span></span>|<span data-ttu-id="3d11b-284">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-284">Int16</span></span>|  
|<span data-ttu-id="3d11b-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="3d11b-285">TYPE_NAME</span></span>|<span data-ttu-id="3d11b-286">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-286">String</span></span>|  
|<span data-ttu-id="3d11b-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="3d11b-287">COLUMN_SIZE</span></span>|<span data-ttu-id="3d11b-288">Int32</span><span class="sxs-lookup"><span data-stu-id="3d11b-288">Int32</span></span>|  
|<span data-ttu-id="3d11b-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="3d11b-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="3d11b-290">Int32</span><span class="sxs-lookup"><span data-stu-id="3d11b-290">Int32</span></span>|  
|<span data-ttu-id="3d11b-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="3d11b-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="3d11b-292">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-292">Int16</span></span>|  
|<span data-ttu-id="3d11b-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="3d11b-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="3d11b-294">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-294">Int16</span></span>|  
|<span data-ttu-id="3d11b-295">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="3d11b-295">NULLABLE</span></span>|<span data-ttu-id="3d11b-296">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-296">Int16</span></span>|  
|<span data-ttu-id="3d11b-297">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="3d11b-297">REMARKS</span></span>|<span data-ttu-id="3d11b-298">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-298">String</span></span>|  
|<span data-ttu-id="3d11b-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="3d11b-299">COLUMN_DEF</span></span>|<span data-ttu-id="3d11b-300">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-300">String</span></span>|  
|<span data-ttu-id="3d11b-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="3d11b-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="3d11b-302">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-302">Int16</span></span>|  
|<span data-ttu-id="3d11b-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="3d11b-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="3d11b-304">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-304">Int16</span></span>|  
|<span data-ttu-id="3d11b-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="3d11b-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="3d11b-306">Int32</span><span class="sxs-lookup"><span data-stu-id="3d11b-306">Int32</span></span>|  
|<span data-ttu-id="3d11b-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="3d11b-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="3d11b-308">Int32</span><span class="sxs-lookup"><span data-stu-id="3d11b-308">Int32</span></span>|  
|<span data-ttu-id="3d11b-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="3d11b-309">IS_NULLABLE</span></span>|<span data-ttu-id="3d11b-310">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-310">String</span></span>|  
|<span data-ttu-id="3d11b-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3d11b-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="3d11b-312">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-312">String</span></span>|  
|<span data-ttu-id="3d11b-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3d11b-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="3d11b-314">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-314">String</span></span>|  
|<span data-ttu-id="3d11b-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="3d11b-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="3d11b-316">Bayt</span><span class="sxs-lookup"><span data-stu-id="3d11b-316">Byte</span></span>|  
  
## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="3d11b-317">Microsoft Oracle ODBC Driver</span><span class="sxs-lookup"><span data-stu-id="3d11b-317">Microsoft Oracle ODBC Driver</span></span>  
 <span data-ttu-id="3d11b-318">Microsoft SQL Server Oracle ODBC sürücüsü ortak şeması koleksiyonları ek olarak aşağıdaki belirli şeması koleksiyonları destekler:</span><span class="sxs-lookup"><span data-stu-id="3d11b-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="3d11b-319">tabloları</span><span class="sxs-lookup"><span data-stu-id="3d11b-319">Tables</span></span>  
  
-   <span data-ttu-id="3d11b-320">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="3d11b-320">Columns</span></span>  
  
-   <span data-ttu-id="3d11b-321">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="3d11b-321">Procedures</span></span>  
  
-   <span data-ttu-id="3d11b-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="3d11b-322">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="3d11b-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="3d11b-323">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="3d11b-324">Görünümler</span><span class="sxs-lookup"><span data-stu-id="3d11b-324">Views</span></span>  
  
-   <span data-ttu-id="3d11b-325">Dizinler</span><span class="sxs-lookup"><span data-stu-id="3d11b-325">Indexes</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="3d11b-326">Tabloları ve görünümleri</span><span class="sxs-lookup"><span data-stu-id="3d11b-326">Tables and Views</span></span>  
  
|<span data-ttu-id="3d11b-327">columnName</span><span class="sxs-lookup"><span data-stu-id="3d11b-327">ColumnName</span></span>|<span data-ttu-id="3d11b-328">Veri türü</span><span class="sxs-lookup"><span data-stu-id="3d11b-328">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="3d11b-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="3d11b-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="3d11b-330">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-330">String</span></span>|  
|<span data-ttu-id="3d11b-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="3d11b-331">TABLE_OWNER</span></span>|<span data-ttu-id="3d11b-332">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-332">String</span></span>|  
|<span data-ttu-id="3d11b-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="3d11b-333">TABLE_NAME</span></span>|<span data-ttu-id="3d11b-334">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-334">String</span></span>|  
|<span data-ttu-id="3d11b-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="3d11b-335">TABLE_TYPE</span></span>|<span data-ttu-id="3d11b-336">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-336">String</span></span>|  
|<span data-ttu-id="3d11b-337">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="3d11b-337">REMARKS</span></span>|<span data-ttu-id="3d11b-338">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-338">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="3d11b-339">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="3d11b-339">Columns</span></span>  
  
|<span data-ttu-id="3d11b-340">columnName</span><span class="sxs-lookup"><span data-stu-id="3d11b-340">ColumnName</span></span>|<span data-ttu-id="3d11b-341">Veri türü</span><span class="sxs-lookup"><span data-stu-id="3d11b-341">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="3d11b-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="3d11b-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="3d11b-343">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-343">String</span></span>|  
|<span data-ttu-id="3d11b-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="3d11b-344">TABLE_OWNER</span></span>|<span data-ttu-id="3d11b-345">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-345">String</span></span>|  
|<span data-ttu-id="3d11b-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="3d11b-346">TABLE_NAME</span></span>|<span data-ttu-id="3d11b-347">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-347">String</span></span>|  
|<span data-ttu-id="3d11b-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="3d11b-348">COLUMN_NAME</span></span>|<span data-ttu-id="3d11b-349">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-349">String</span></span>|  
|<span data-ttu-id="3d11b-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="3d11b-350">DATA_TYPE</span></span>|<span data-ttu-id="3d11b-351">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-351">Int16</span></span>|  
|<span data-ttu-id="3d11b-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="3d11b-352">TYPE_NAME</span></span>|<span data-ttu-id="3d11b-353">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-353">String</span></span>|  
|<span data-ttu-id="3d11b-354">DUYARLILIK</span><span class="sxs-lookup"><span data-stu-id="3d11b-354">PRECISION</span></span>|<span data-ttu-id="3d11b-355">Int32</span><span class="sxs-lookup"><span data-stu-id="3d11b-355">Int32</span></span>|  
|<span data-ttu-id="3d11b-356">UZUNLUĞU</span><span class="sxs-lookup"><span data-stu-id="3d11b-356">LENGTH</span></span>|<span data-ttu-id="3d11b-357">Int32</span><span class="sxs-lookup"><span data-stu-id="3d11b-357">Int32</span></span>|  
|<span data-ttu-id="3d11b-358">ÖLÇEK</span><span class="sxs-lookup"><span data-stu-id="3d11b-358">SCALE</span></span>|<span data-ttu-id="3d11b-359">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-359">Int16</span></span>|  
|<span data-ttu-id="3d11b-360">RADIX</span><span class="sxs-lookup"><span data-stu-id="3d11b-360">RADIX</span></span>|<span data-ttu-id="3d11b-361">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-361">Int16</span></span>|  
|<span data-ttu-id="3d11b-362">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="3d11b-362">NULLABLE</span></span>|<span data-ttu-id="3d11b-363">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-363">Int16</span></span>|  
|<span data-ttu-id="3d11b-364">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="3d11b-364">REMARKS</span></span>|<span data-ttu-id="3d11b-365">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-365">String</span></span>|  
|<span data-ttu-id="3d11b-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="3d11b-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="3d11b-367">Int32</span><span class="sxs-lookup"><span data-stu-id="3d11b-367">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="3d11b-368">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="3d11b-368">Procedures</span></span>  
  
|<span data-ttu-id="3d11b-369">columnName</span><span class="sxs-lookup"><span data-stu-id="3d11b-369">ColumnName</span></span>|<span data-ttu-id="3d11b-370">Veri türü</span><span class="sxs-lookup"><span data-stu-id="3d11b-370">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="3d11b-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="3d11b-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="3d11b-372">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-372">String</span></span>|  
|<span data-ttu-id="3d11b-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="3d11b-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="3d11b-374">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-374">String</span></span>|  
|<span data-ttu-id="3d11b-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="3d11b-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="3d11b-376">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-376">String</span></span>|  
|<span data-ttu-id="3d11b-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="3d11b-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="3d11b-378">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-378">Int16</span></span>|  
|<span data-ttu-id="3d11b-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="3d11b-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="3d11b-380">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-380">Int16</span></span>|  
|<span data-ttu-id="3d11b-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="3d11b-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="3d11b-382">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-382">Int16</span></span>|  
|<span data-ttu-id="3d11b-383">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="3d11b-383">REMARKS</span></span>|<span data-ttu-id="3d11b-384">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-384">String</span></span>|  
|<span data-ttu-id="3d11b-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="3d11b-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="3d11b-386">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-386">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="3d11b-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="3d11b-387">ProcedureColumns</span></span>  
  
|<span data-ttu-id="3d11b-388">columnName</span><span class="sxs-lookup"><span data-stu-id="3d11b-388">ColumnName</span></span>|<span data-ttu-id="3d11b-389">Veri türü</span><span class="sxs-lookup"><span data-stu-id="3d11b-389">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="3d11b-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="3d11b-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="3d11b-391">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-391">String</span></span>|  
|<span data-ttu-id="3d11b-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="3d11b-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="3d11b-393">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-393">String</span></span>|  
|<span data-ttu-id="3d11b-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="3d11b-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="3d11b-395">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-395">String</span></span>|  
|<span data-ttu-id="3d11b-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="3d11b-396">COLUMN_NAME</span></span>|<span data-ttu-id="3d11b-397">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-397">String</span></span>|  
|<span data-ttu-id="3d11b-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="3d11b-398">COLUMN_TYPE</span></span>|<span data-ttu-id="3d11b-399">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-399">Int16</span></span>|  
|<span data-ttu-id="3d11b-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="3d11b-400">DATA_TYPE</span></span>|<span data-ttu-id="3d11b-401">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-401">Int16</span></span>|  
|<span data-ttu-id="3d11b-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="3d11b-402">TYPE_NAME</span></span>|<span data-ttu-id="3d11b-403">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-403">String</span></span>|  
|<span data-ttu-id="3d11b-404">DUYARLILIK</span><span class="sxs-lookup"><span data-stu-id="3d11b-404">PRECISION</span></span>|<span data-ttu-id="3d11b-405">Int32</span><span class="sxs-lookup"><span data-stu-id="3d11b-405">Int32</span></span>|  
|<span data-ttu-id="3d11b-406">UZUNLUĞU</span><span class="sxs-lookup"><span data-stu-id="3d11b-406">LENGTH</span></span>|<span data-ttu-id="3d11b-407">Int32</span><span class="sxs-lookup"><span data-stu-id="3d11b-407">Int32</span></span>|  
|<span data-ttu-id="3d11b-408">ÖLÇEK</span><span class="sxs-lookup"><span data-stu-id="3d11b-408">SCALE</span></span>|<span data-ttu-id="3d11b-409">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-409">Int16</span></span>|  
|<span data-ttu-id="3d11b-410">RADIX</span><span class="sxs-lookup"><span data-stu-id="3d11b-410">RADIX</span></span>|<span data-ttu-id="3d11b-411">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-411">Int16</span></span>|  
|<span data-ttu-id="3d11b-412">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="3d11b-412">NULLABLE</span></span>|<span data-ttu-id="3d11b-413">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-413">Int16</span></span>|  
|<span data-ttu-id="3d11b-414">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="3d11b-414">REMARKS</span></span>|<span data-ttu-id="3d11b-415">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-415">String</span></span>|  
|<span data-ttu-id="3d11b-416">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="3d11b-416">OVERLOAD</span></span>|<span data-ttu-id="3d11b-417">Int32</span><span class="sxs-lookup"><span data-stu-id="3d11b-417">Int32</span></span>|  
|<span data-ttu-id="3d11b-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="3d11b-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="3d11b-419">Int32</span><span class="sxs-lookup"><span data-stu-id="3d11b-419">Int32</span></span>|  
  
## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="3d11b-420">Microsoft Jet ODBC sürücüsü</span><span class="sxs-lookup"><span data-stu-id="3d11b-420">Microsoft Jet ODBC Driver</span></span>  
 <span data-ttu-id="3d11b-421">Microsoft Jet ODBC sürücüsü ortak şeması koleksiyonları ek olarak aşağıdaki belirli şeması koleksiyonları destekler:</span><span class="sxs-lookup"><span data-stu-id="3d11b-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="3d11b-422">tabloları</span><span class="sxs-lookup"><span data-stu-id="3d11b-422">Tables</span></span>  
  
-   <span data-ttu-id="3d11b-423">Dizinler</span><span class="sxs-lookup"><span data-stu-id="3d11b-423">Indexes</span></span>  
  
-   <span data-ttu-id="3d11b-424">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="3d11b-424">Columns</span></span>  
  
-   <span data-ttu-id="3d11b-425">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="3d11b-425">Procedures</span></span>  
  
-   <span data-ttu-id="3d11b-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="3d11b-426">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="3d11b-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="3d11b-427">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="3d11b-428">Görünümler</span><span class="sxs-lookup"><span data-stu-id="3d11b-428">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="3d11b-429">Tabloları ve görünümleri</span><span class="sxs-lookup"><span data-stu-id="3d11b-429">Tables and Views</span></span>  
  
|<span data-ttu-id="3d11b-430">columnName</span><span class="sxs-lookup"><span data-stu-id="3d11b-430">ColumnName</span></span>|<span data-ttu-id="3d11b-431">Veri türü</span><span class="sxs-lookup"><span data-stu-id="3d11b-431">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="3d11b-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="3d11b-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="3d11b-433">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-433">String</span></span>|  
|<span data-ttu-id="3d11b-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="3d11b-434">TABLE_OWNER</span></span>|<span data-ttu-id="3d11b-435">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-435">String</span></span>|  
|<span data-ttu-id="3d11b-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="3d11b-436">TABLE_NAME</span></span>|<span data-ttu-id="3d11b-437">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-437">String</span></span>|  
|<span data-ttu-id="3d11b-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="3d11b-438">TABLE_TYPE</span></span>|<span data-ttu-id="3d11b-439">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-439">String</span></span>|  
|<span data-ttu-id="3d11b-440">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="3d11b-440">REMARKS</span></span>|<span data-ttu-id="3d11b-441">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-441">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="3d11b-442">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="3d11b-442">Columns</span></span>  
  
|<span data-ttu-id="3d11b-443">columnName</span><span class="sxs-lookup"><span data-stu-id="3d11b-443">ColumnName</span></span>|<span data-ttu-id="3d11b-444">Veri türü</span><span class="sxs-lookup"><span data-stu-id="3d11b-444">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="3d11b-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="3d11b-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="3d11b-446">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-446">String</span></span>|  
|<span data-ttu-id="3d11b-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="3d11b-447">TABLE_OWNER</span></span>|<span data-ttu-id="3d11b-448">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-448">String</span></span>|  
|<span data-ttu-id="3d11b-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="3d11b-449">TABLE_NAME</span></span>|<span data-ttu-id="3d11b-450">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-450">String</span></span>|  
|<span data-ttu-id="3d11b-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="3d11b-451">COLUMN_NAME</span></span>|<span data-ttu-id="3d11b-452">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-452">String</span></span>|  
|<span data-ttu-id="3d11b-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="3d11b-453">DATA_TYPE</span></span>|<span data-ttu-id="3d11b-454">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-454">Int16</span></span>|  
|<span data-ttu-id="3d11b-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="3d11b-455">TYPE_NAME</span></span>|<span data-ttu-id="3d11b-456">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-456">String</span></span>|  
|<span data-ttu-id="3d11b-457">DUYARLILIK</span><span class="sxs-lookup"><span data-stu-id="3d11b-457">PRECISION</span></span>|<span data-ttu-id="3d11b-458">Int32</span><span class="sxs-lookup"><span data-stu-id="3d11b-458">Int32</span></span>|  
|<span data-ttu-id="3d11b-459">UZUNLUĞU</span><span class="sxs-lookup"><span data-stu-id="3d11b-459">LENGTH</span></span>|<span data-ttu-id="3d11b-460">Int32</span><span class="sxs-lookup"><span data-stu-id="3d11b-460">Int32</span></span>|  
|<span data-ttu-id="3d11b-461">ÖLÇEK</span><span class="sxs-lookup"><span data-stu-id="3d11b-461">SCALE</span></span>|<span data-ttu-id="3d11b-462">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-462">Int16</span></span>|  
|<span data-ttu-id="3d11b-463">RADIX</span><span class="sxs-lookup"><span data-stu-id="3d11b-463">RADIX</span></span>|<span data-ttu-id="3d11b-464">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-464">Int16</span></span>|  
|<span data-ttu-id="3d11b-465">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="3d11b-465">NULLABLE</span></span>|<span data-ttu-id="3d11b-466">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-466">Int16</span></span>|  
|<span data-ttu-id="3d11b-467">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="3d11b-467">REMARKS</span></span>|<span data-ttu-id="3d11b-468">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-468">String</span></span>|  
|<span data-ttu-id="3d11b-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="3d11b-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="3d11b-470">Int32</span><span class="sxs-lookup"><span data-stu-id="3d11b-470">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="3d11b-471">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="3d11b-471">Procedures</span></span>  
  
|<span data-ttu-id="3d11b-472">columnName</span><span class="sxs-lookup"><span data-stu-id="3d11b-472">ColumnName</span></span>|<span data-ttu-id="3d11b-473">Veri türü</span><span class="sxs-lookup"><span data-stu-id="3d11b-473">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="3d11b-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="3d11b-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="3d11b-475">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-475">String</span></span>|  
|<span data-ttu-id="3d11b-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="3d11b-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="3d11b-477">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-477">String</span></span>|  
|<span data-ttu-id="3d11b-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="3d11b-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="3d11b-479">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-479">String</span></span>|  
|<span data-ttu-id="3d11b-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="3d11b-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="3d11b-481">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-481">Int16</span></span>|  
|<span data-ttu-id="3d11b-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="3d11b-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="3d11b-483">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-483">Int16</span></span>|  
|<span data-ttu-id="3d11b-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="3d11b-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="3d11b-485">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-485">Int16</span></span>|  
|<span data-ttu-id="3d11b-486">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="3d11b-486">REMARKS</span></span>|<span data-ttu-id="3d11b-487">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-487">String</span></span>|  
|<span data-ttu-id="3d11b-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="3d11b-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="3d11b-489">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-489">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="3d11b-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="3d11b-490">ProcedureColumns</span></span>  
  
|<span data-ttu-id="3d11b-491">columnName</span><span class="sxs-lookup"><span data-stu-id="3d11b-491">ColumnName</span></span>|<span data-ttu-id="3d11b-492">Veri türü</span><span class="sxs-lookup"><span data-stu-id="3d11b-492">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="3d11b-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="3d11b-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="3d11b-494">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-494">String</span></span>|  
|<span data-ttu-id="3d11b-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="3d11b-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="3d11b-496">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-496">String</span></span>|  
|<span data-ttu-id="3d11b-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="3d11b-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="3d11b-498">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-498">String</span></span>|  
|<span data-ttu-id="3d11b-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="3d11b-499">COLUMN_NAME</span></span>|<span data-ttu-id="3d11b-500">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-500">String</span></span>|  
|<span data-ttu-id="3d11b-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="3d11b-501">COLUMN_TYPE</span></span>|<span data-ttu-id="3d11b-502">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-502">Int16</span></span>|  
|<span data-ttu-id="3d11b-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="3d11b-503">DATA_TYPE</span></span>|<span data-ttu-id="3d11b-504">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-504">Int16</span></span>|  
|<span data-ttu-id="3d11b-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="3d11b-505">TYPE_NAME</span></span>|<span data-ttu-id="3d11b-506">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-506">String</span></span>|  
|<span data-ttu-id="3d11b-507">DUYARLILIK</span><span class="sxs-lookup"><span data-stu-id="3d11b-507">PRECISION</span></span>|<span data-ttu-id="3d11b-508">Int32</span><span class="sxs-lookup"><span data-stu-id="3d11b-508">Int32</span></span>|  
|<span data-ttu-id="3d11b-509">UZUNLUĞU</span><span class="sxs-lookup"><span data-stu-id="3d11b-509">LENGTH</span></span>|<span data-ttu-id="3d11b-510">Int32</span><span class="sxs-lookup"><span data-stu-id="3d11b-510">Int32</span></span>|  
|<span data-ttu-id="3d11b-511">ÖLÇEK</span><span class="sxs-lookup"><span data-stu-id="3d11b-511">SCALE</span></span>|<span data-ttu-id="3d11b-512">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-512">Int16</span></span>|  
|<span data-ttu-id="3d11b-513">RADIX</span><span class="sxs-lookup"><span data-stu-id="3d11b-513">RADIX</span></span>|<span data-ttu-id="3d11b-514">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-514">Int16</span></span>|  
|<span data-ttu-id="3d11b-515">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="3d11b-515">NULLABLE</span></span>|<span data-ttu-id="3d11b-516">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-516">Int16</span></span>|  
|<span data-ttu-id="3d11b-517">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="3d11b-517">REMARKS</span></span>|<span data-ttu-id="3d11b-518">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-518">String</span></span>|  
|<span data-ttu-id="3d11b-519">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="3d11b-519">OVERLOAD</span></span>|<span data-ttu-id="3d11b-520">Int32</span><span class="sxs-lookup"><span data-stu-id="3d11b-520">Int32</span></span>|  
|<span data-ttu-id="3d11b-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="3d11b-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="3d11b-522">Int32</span><span class="sxs-lookup"><span data-stu-id="3d11b-522">Int32</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="3d11b-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="3d11b-523">ProcedureParameters</span></span>  
  
|<span data-ttu-id="3d11b-524">columnName</span><span class="sxs-lookup"><span data-stu-id="3d11b-524">ColumnName</span></span>|<span data-ttu-id="3d11b-525">Veri türü</span><span class="sxs-lookup"><span data-stu-id="3d11b-525">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="3d11b-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="3d11b-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="3d11b-527">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-527">String</span></span>|  
|<span data-ttu-id="3d11b-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="3d11b-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="3d11b-529">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-529">String</span></span>|  
|<span data-ttu-id="3d11b-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="3d11b-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="3d11b-531">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-531">String</span></span>|  
|<span data-ttu-id="3d11b-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="3d11b-532">COLUMN_NAME</span></span>|<span data-ttu-id="3d11b-533">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-533">String</span></span>|  
|<span data-ttu-id="3d11b-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="3d11b-534">COLUMN_TYPE</span></span>|<span data-ttu-id="3d11b-535">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-535">Int16</span></span>|  
|<span data-ttu-id="3d11b-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="3d11b-536">DATA_TYPE</span></span>|<span data-ttu-id="3d11b-537">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-537">Int16</span></span>|  
|<span data-ttu-id="3d11b-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="3d11b-538">TYPE_NAME</span></span>|<span data-ttu-id="3d11b-539">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-539">String</span></span>|  
|<span data-ttu-id="3d11b-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="3d11b-540">COLUMN_SIZE</span></span>|<span data-ttu-id="3d11b-541">Int32</span><span class="sxs-lookup"><span data-stu-id="3d11b-541">Int32</span></span>|  
|<span data-ttu-id="3d11b-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="3d11b-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="3d11b-543">Int32</span><span class="sxs-lookup"><span data-stu-id="3d11b-543">Int32</span></span>|  
|<span data-ttu-id="3d11b-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="3d11b-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="3d11b-545">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-545">Int16</span></span>|  
|<span data-ttu-id="3d11b-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="3d11b-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="3d11b-547">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-547">Int16</span></span>|  
|<span data-ttu-id="3d11b-548">BOŞ DEĞER ATANABİLİR</span><span class="sxs-lookup"><span data-stu-id="3d11b-548">NULLABLE</span></span>|<span data-ttu-id="3d11b-549">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-549">Int16</span></span>|  
|<span data-ttu-id="3d11b-550">AÇIKLAMALAR</span><span class="sxs-lookup"><span data-stu-id="3d11b-550">REMARKS</span></span>|<span data-ttu-id="3d11b-551">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-551">String</span></span>|  
|<span data-ttu-id="3d11b-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="3d11b-552">COLUMN_DEF</span></span>|<span data-ttu-id="3d11b-553">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-553">String</span></span>|  
|<span data-ttu-id="3d11b-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="3d11b-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="3d11b-555">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-555">Int16</span></span>|  
|<span data-ttu-id="3d11b-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="3d11b-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="3d11b-557">Int16</span><span class="sxs-lookup"><span data-stu-id="3d11b-557">Int16</span></span>|  
|<span data-ttu-id="3d11b-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="3d11b-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="3d11b-559">Int32</span><span class="sxs-lookup"><span data-stu-id="3d11b-559">Int32</span></span>|  
|<span data-ttu-id="3d11b-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="3d11b-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="3d11b-561">Int32</span><span class="sxs-lookup"><span data-stu-id="3d11b-561">Int32</span></span>|  
|<span data-ttu-id="3d11b-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="3d11b-562">IS_NULLABLE</span></span>|<span data-ttu-id="3d11b-563">Dize</span><span class="sxs-lookup"><span data-stu-id="3d11b-563">String</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3d11b-564">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3d11b-564">See Also</span></span>  
 [<span data-ttu-id="3d11b-565">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="3d11b-565">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
