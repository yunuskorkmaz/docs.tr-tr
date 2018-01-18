---
title: "OLE DB şeması koleksiyonları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 33e794559abd7f619f7431683f06e59705b57d41
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="71e68-102">OLE DB şeması koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="71e68-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="71e68-103">Bu bölümde, Microsoft SQL Server, Oracle ve Microsoft Jet için OLE DB sağlayıcıları şema koleksiyonu desteği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="71e68-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="71e68-104">Microsoft SQL Server OLE DB sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="71e68-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="71e68-105">Microsoft SQL Server OLE DB sürücüsü ortak şeması koleksiyonları ek olarak aşağıdaki belirli şeması koleksiyonları destekler:</span><span class="sxs-lookup"><span data-stu-id="71e68-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="71e68-106">tabloları</span><span class="sxs-lookup"><span data-stu-id="71e68-106">Tables</span></span>  
  
-   <span data-ttu-id="71e68-107">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="71e68-107">Columns</span></span>  
  
-   <span data-ttu-id="71e68-108">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="71e68-108">Procedures</span></span>  
  
-   <span data-ttu-id="71e68-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="71e68-109">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="71e68-110">Katalog</span><span class="sxs-lookup"><span data-stu-id="71e68-110">Catalog</span></span>  
  
-   <span data-ttu-id="71e68-111">Dizinler</span><span class="sxs-lookup"><span data-stu-id="71e68-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="71e68-112">tabloları</span><span class="sxs-lookup"><span data-stu-id="71e68-112">Tables</span></span>  
  
|<span data-ttu-id="71e68-113">columnName</span><span class="sxs-lookup"><span data-stu-id="71e68-113">ColumnName</span></span>|<span data-ttu-id="71e68-114">Veri türü</span><span class="sxs-lookup"><span data-stu-id="71e68-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="71e68-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="71e68-115">TABLE_CATALOG</span></span>|<span data-ttu-id="71e68-116">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-116">String</span></span>|  
|<span data-ttu-id="71e68-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="71e68-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="71e68-118">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-118">String</span></span>|  
|<span data-ttu-id="71e68-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="71e68-119">TABLE_NAME</span></span>|<span data-ttu-id="71e68-120">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-120">String</span></span>|  
|<span data-ttu-id="71e68-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="71e68-121">TABLE_TYPE</span></span>|<span data-ttu-id="71e68-122">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-122">String</span></span>|  
|<span data-ttu-id="71e68-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="71e68-123">TABLE_GUID</span></span>|<span data-ttu-id="71e68-124">Guid</span><span class="sxs-lookup"><span data-stu-id="71e68-124">Guid</span></span>|  
|<span data-ttu-id="71e68-125">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="71e68-125">DESCRIPTION</span></span>|<span data-ttu-id="71e68-126">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-126">String</span></span>|  
|<span data-ttu-id="71e68-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="71e68-127">TABLE_PROPID</span></span>|<span data-ttu-id="71e68-128">Int64</span><span class="sxs-lookup"><span data-stu-id="71e68-128">Int64</span></span>|  
|<span data-ttu-id="71e68-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="71e68-129">DATE_CREATED</span></span>|<span data-ttu-id="71e68-130">DateTime</span><span class="sxs-lookup"><span data-stu-id="71e68-130">DateTime</span></span>|  
|<span data-ttu-id="71e68-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="71e68-131">DATE_MODIFIED</span></span>|<span data-ttu-id="71e68-132">DateTime</span><span class="sxs-lookup"><span data-stu-id="71e68-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="71e68-133">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="71e68-133">Columns</span></span>  
  
|<span data-ttu-id="71e68-134">columnName</span><span class="sxs-lookup"><span data-stu-id="71e68-134">ColumnName</span></span>|<span data-ttu-id="71e68-135">Veri türü</span><span class="sxs-lookup"><span data-stu-id="71e68-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="71e68-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="71e68-136">TABLE_CATALOG</span></span>|<span data-ttu-id="71e68-137">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-137">String</span></span>|  
|<span data-ttu-id="71e68-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="71e68-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="71e68-139">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-139">String</span></span>|  
|<span data-ttu-id="71e68-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="71e68-140">TABLE_NAME</span></span>|<span data-ttu-id="71e68-141">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-141">String</span></span>|  
|<span data-ttu-id="71e68-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="71e68-142">COLUMN_NAME</span></span>|<span data-ttu-id="71e68-143">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-143">String</span></span>|  
|<span data-ttu-id="71e68-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="71e68-144">COLUMN_GUID</span></span>|<span data-ttu-id="71e68-145">Guid</span><span class="sxs-lookup"><span data-stu-id="71e68-145">Guid</span></span>|  
|<span data-ttu-id="71e68-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="71e68-146">COLUMN_PROPID</span></span>|<span data-ttu-id="71e68-147">Int64</span><span class="sxs-lookup"><span data-stu-id="71e68-147">Int64</span></span>|  
|<span data-ttu-id="71e68-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="71e68-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="71e68-149">Int64</span><span class="sxs-lookup"><span data-stu-id="71e68-149">Int64</span></span>|  
|<span data-ttu-id="71e68-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="71e68-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="71e68-151">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="71e68-151">Boolean</span></span>|  
|<span data-ttu-id="71e68-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="71e68-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="71e68-153">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-153">String</span></span>|  
|<span data-ttu-id="71e68-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="71e68-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="71e68-155">Int64</span><span class="sxs-lookup"><span data-stu-id="71e68-155">Int64</span></span>|  
|<span data-ttu-id="71e68-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="71e68-156">IS_NULLABLE</span></span>|<span data-ttu-id="71e68-157">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="71e68-157">Boolean</span></span>|  
|<span data-ttu-id="71e68-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="71e68-158">DATA_TYPE</span></span>|<span data-ttu-id="71e68-159">Int32</span><span class="sxs-lookup"><span data-stu-id="71e68-159">Int32</span></span>|  
|<span data-ttu-id="71e68-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="71e68-160">TYPE_GUID</span></span>|<span data-ttu-id="71e68-161">Guid</span><span class="sxs-lookup"><span data-stu-id="71e68-161">Guid</span></span>|  
|<span data-ttu-id="71e68-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="71e68-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="71e68-163">Int64</span><span class="sxs-lookup"><span data-stu-id="71e68-163">Int64</span></span>|  
|<span data-ttu-id="71e68-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="71e68-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="71e68-165">Int64</span><span class="sxs-lookup"><span data-stu-id="71e68-165">Int64</span></span>|  
|<span data-ttu-id="71e68-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="71e68-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="71e68-167">Int32</span><span class="sxs-lookup"><span data-stu-id="71e68-167">Int32</span></span>|  
|<span data-ttu-id="71e68-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="71e68-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="71e68-169">Int16</span><span class="sxs-lookup"><span data-stu-id="71e68-169">Int16</span></span>|  
|<span data-ttu-id="71e68-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="71e68-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="71e68-171">Int64</span><span class="sxs-lookup"><span data-stu-id="71e68-171">Int64</span></span>|  
|<span data-ttu-id="71e68-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="71e68-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="71e68-173">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-173">String</span></span>|  
|<span data-ttu-id="71e68-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="71e68-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="71e68-175">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-175">String</span></span>|  
|<span data-ttu-id="71e68-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="71e68-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="71e68-177">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-177">String</span></span>|  
|<span data-ttu-id="71e68-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="71e68-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="71e68-179">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-179">String</span></span>|  
|<span data-ttu-id="71e68-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="71e68-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="71e68-181">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-181">String</span></span>|  
|<span data-ttu-id="71e68-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="71e68-182">COLLATION_NAME</span></span>|<span data-ttu-id="71e68-183">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-183">String</span></span>|  
|<span data-ttu-id="71e68-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="71e68-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="71e68-185">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-185">String</span></span>|  
|<span data-ttu-id="71e68-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="71e68-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="71e68-187">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-187">String</span></span>|  
|<span data-ttu-id="71e68-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="71e68-188">DOMAIN_NAME</span></span>|<span data-ttu-id="71e68-189">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-189">String</span></span>|  
|<span data-ttu-id="71e68-190">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="71e68-190">DESCRIPTION</span></span>|<span data-ttu-id="71e68-191">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-191">String</span></span>|  
|<span data-ttu-id="71e68-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="71e68-192">COLUMN_LCID</span></span>|<span data-ttu-id="71e68-193">Int32</span><span class="sxs-lookup"><span data-stu-id="71e68-193">Int32</span></span>|  
|<span data-ttu-id="71e68-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="71e68-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="71e68-195">Int32</span><span class="sxs-lookup"><span data-stu-id="71e68-195">Int32</span></span>|  
|<span data-ttu-id="71e68-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="71e68-196">COLUMN_SORTID</span></span>|<span data-ttu-id="71e68-197">Int32</span><span class="sxs-lookup"><span data-stu-id="71e68-197">Int32</span></span>|  
|<span data-ttu-id="71e68-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="71e68-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="71e68-199">Byte]</span><span class="sxs-lookup"><span data-stu-id="71e68-199">Byte[]</span></span>|  
|<span data-ttu-id="71e68-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="71e68-200">IS_COMPUTED</span></span>|<span data-ttu-id="71e68-201">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="71e68-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="71e68-202">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="71e68-202">Procedures</span></span>  
  
|<span data-ttu-id="71e68-203">columnName</span><span class="sxs-lookup"><span data-stu-id="71e68-203">ColumnName</span></span>|<span data-ttu-id="71e68-204">Veri türü</span><span class="sxs-lookup"><span data-stu-id="71e68-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="71e68-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="71e68-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="71e68-206">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-206">String</span></span>|  
|<span data-ttu-id="71e68-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="71e68-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="71e68-208">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-208">String</span></span>|  
|<span data-ttu-id="71e68-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="71e68-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="71e68-210">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-210">String</span></span>|  
|<span data-ttu-id="71e68-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="71e68-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="71e68-212">Int16</span><span class="sxs-lookup"><span data-stu-id="71e68-212">Int16</span></span>|  
|<span data-ttu-id="71e68-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="71e68-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="71e68-214">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-214">String</span></span>|  
|<span data-ttu-id="71e68-215">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="71e68-215">DESCRIPTION</span></span>|<span data-ttu-id="71e68-216">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-216">String</span></span>|  
|<span data-ttu-id="71e68-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="71e68-217">DATE_CREATED</span></span>|<span data-ttu-id="71e68-218">DateTime</span><span class="sxs-lookup"><span data-stu-id="71e68-218">DateTime</span></span>|  
|<span data-ttu-id="71e68-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="71e68-219">DATE_MODIFIED</span></span>|<span data-ttu-id="71e68-220">DateTime</span><span class="sxs-lookup"><span data-stu-id="71e68-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="71e68-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="71e68-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="71e68-222">columnName</span><span class="sxs-lookup"><span data-stu-id="71e68-222">ColumnName</span></span>|<span data-ttu-id="71e68-223">Veri türü</span><span class="sxs-lookup"><span data-stu-id="71e68-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="71e68-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="71e68-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="71e68-225">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-225">String</span></span>|  
|<span data-ttu-id="71e68-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="71e68-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="71e68-227">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-227">String</span></span>|  
|<span data-ttu-id="71e68-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="71e68-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="71e68-229">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-229">String</span></span>|  
|<span data-ttu-id="71e68-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="71e68-230">PARAMETER_NAME</span></span>|<span data-ttu-id="71e68-231">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-231">String</span></span>|  
|<span data-ttu-id="71e68-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="71e68-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="71e68-233">Int32</span><span class="sxs-lookup"><span data-stu-id="71e68-233">Int32</span></span>|  
|<span data-ttu-id="71e68-234">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="71e68-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="71e68-235">Int32</span><span class="sxs-lookup"><span data-stu-id="71e68-235">Int32</span></span>|  
|<span data-ttu-id="71e68-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="71e68-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="71e68-237">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="71e68-237">Boolean</span></span>|  
|<span data-ttu-id="71e68-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="71e68-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="71e68-239">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-239">String</span></span>|  
|<span data-ttu-id="71e68-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="71e68-240">IS_NULLABLE</span></span>|<span data-ttu-id="71e68-241">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="71e68-241">Boolean</span></span>|  
|<span data-ttu-id="71e68-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="71e68-242">DATA_TYPE</span></span>|<span data-ttu-id="71e68-243">Int32</span><span class="sxs-lookup"><span data-stu-id="71e68-243">Int32</span></span>|  
|<span data-ttu-id="71e68-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="71e68-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="71e68-245">Int64</span><span class="sxs-lookup"><span data-stu-id="71e68-245">Int64</span></span>|  
|<span data-ttu-id="71e68-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="71e68-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="71e68-247">Int64</span><span class="sxs-lookup"><span data-stu-id="71e68-247">Int64</span></span>|  
|<span data-ttu-id="71e68-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="71e68-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="71e68-249">Int32</span><span class="sxs-lookup"><span data-stu-id="71e68-249">Int32</span></span>|  
|<span data-ttu-id="71e68-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="71e68-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="71e68-251">Int16</span><span class="sxs-lookup"><span data-stu-id="71e68-251">Int16</span></span>|  
|<span data-ttu-id="71e68-252">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="71e68-252">DESCRIPTION</span></span>|<span data-ttu-id="71e68-253">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-253">String</span></span>|  
|<span data-ttu-id="71e68-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="71e68-254">TYPE_NAME</span></span>|<span data-ttu-id="71e68-255">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-255">String</span></span>|  
|<span data-ttu-id="71e68-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="71e68-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="71e68-257">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="71e68-258">Katalog</span><span class="sxs-lookup"><span data-stu-id="71e68-258">Catalog</span></span>  
  
|<span data-ttu-id="71e68-259">columnName</span><span class="sxs-lookup"><span data-stu-id="71e68-259">ColumnName</span></span>|<span data-ttu-id="71e68-260">Veri türü</span><span class="sxs-lookup"><span data-stu-id="71e68-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="71e68-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="71e68-261">CATALOG_NAME</span></span>|<span data-ttu-id="71e68-262">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-262">String</span></span>|  
|<span data-ttu-id="71e68-263">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="71e68-263">DESCRIPTION</span></span>|<span data-ttu-id="71e68-264">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="71e68-265">Dizinler</span><span class="sxs-lookup"><span data-stu-id="71e68-265">Indexes</span></span>  
  
|<span data-ttu-id="71e68-266">columnName</span><span class="sxs-lookup"><span data-stu-id="71e68-266">ColumnName</span></span>|<span data-ttu-id="71e68-267">Veri türü</span><span class="sxs-lookup"><span data-stu-id="71e68-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="71e68-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="71e68-268">TABLE_CATALOG</span></span>|<span data-ttu-id="71e68-269">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-269">String</span></span>|  
|<span data-ttu-id="71e68-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="71e68-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="71e68-271">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-271">String</span></span>|  
|<span data-ttu-id="71e68-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="71e68-272">TABLE_NAME</span></span>|<span data-ttu-id="71e68-273">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-273">String</span></span>|  
|<span data-ttu-id="71e68-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="71e68-274">INDEX_CATALOG</span></span>|<span data-ttu-id="71e68-275">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-275">String</span></span>|  
|<span data-ttu-id="71e68-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="71e68-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="71e68-277">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-277">String</span></span>|  
|<span data-ttu-id="71e68-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="71e68-278">INDEX_NAME</span></span>|<span data-ttu-id="71e68-279">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-279">String</span></span>|  
|<span data-ttu-id="71e68-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="71e68-280">PRIMARY_KEY</span></span>|<span data-ttu-id="71e68-281">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="71e68-281">Boolean</span></span>|  
|<span data-ttu-id="71e68-282">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="71e68-282">UNIQUE</span></span>|<span data-ttu-id="71e68-283">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="71e68-283">Boolean</span></span>|  
|<span data-ttu-id="71e68-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="71e68-284">CLUSTERED</span></span>|<span data-ttu-id="71e68-285">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="71e68-285">Boolean</span></span>|  
|<span data-ttu-id="71e68-286">TÜRÜ</span><span class="sxs-lookup"><span data-stu-id="71e68-286">TYPE</span></span>|<span data-ttu-id="71e68-287">Int32</span><span class="sxs-lookup"><span data-stu-id="71e68-287">Int32</span></span>|  
|<span data-ttu-id="71e68-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="71e68-288">FILL_FACTOR</span></span>|<span data-ttu-id="71e68-289">Int32</span><span class="sxs-lookup"><span data-stu-id="71e68-289">Int32</span></span>|  
|<span data-ttu-id="71e68-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="71e68-290">INITIAL_SIZE</span></span>|<span data-ttu-id="71e68-291">Int32</span><span class="sxs-lookup"><span data-stu-id="71e68-291">Int32</span></span>|  
|<span data-ttu-id="71e68-292">NULLS</span><span class="sxs-lookup"><span data-stu-id="71e68-292">NULLS</span></span>|<span data-ttu-id="71e68-293">Int32</span><span class="sxs-lookup"><span data-stu-id="71e68-293">Int32</span></span>|  
|<span data-ttu-id="71e68-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="71e68-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="71e68-295">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="71e68-295">Boolean</span></span>|  
|<span data-ttu-id="71e68-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="71e68-296">AUTO_UPDATE</span></span>|<span data-ttu-id="71e68-297">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="71e68-297">Boolean</span></span>|  
|<span data-ttu-id="71e68-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="71e68-298">NULL_COLLATION</span></span>|<span data-ttu-id="71e68-299">Int32</span><span class="sxs-lookup"><span data-stu-id="71e68-299">Int32</span></span>|  
|<span data-ttu-id="71e68-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="71e68-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="71e68-301">Int64</span><span class="sxs-lookup"><span data-stu-id="71e68-301">Int64</span></span>|  
|<span data-ttu-id="71e68-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="71e68-302">COLUMN_NAME</span></span>|<span data-ttu-id="71e68-303">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-303">String</span></span>|  
|<span data-ttu-id="71e68-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="71e68-304">COLUMN_GUID</span></span>|<span data-ttu-id="71e68-305">Guid</span><span class="sxs-lookup"><span data-stu-id="71e68-305">Guid</span></span>|  
|<span data-ttu-id="71e68-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="71e68-306">COLUMN_PROPID</span></span>|<span data-ttu-id="71e68-307">Int64</span><span class="sxs-lookup"><span data-stu-id="71e68-307">Int64</span></span>|  
|<span data-ttu-id="71e68-308">HARMANLAMA</span><span class="sxs-lookup"><span data-stu-id="71e68-308">COLLATION</span></span>|<span data-ttu-id="71e68-309">Int16</span><span class="sxs-lookup"><span data-stu-id="71e68-309">Int16</span></span>|  
|<span data-ttu-id="71e68-310">ÖNEM DÜZEYİ</span><span class="sxs-lookup"><span data-stu-id="71e68-310">CARDINALITY</span></span>|<span data-ttu-id="71e68-311">Ondalık</span><span class="sxs-lookup"><span data-stu-id="71e68-311">Decimal</span></span>|  
|<span data-ttu-id="71e68-312">SAYFALARI</span><span class="sxs-lookup"><span data-stu-id="71e68-312">PAGES</span></span>|<span data-ttu-id="71e68-313">Int32</span><span class="sxs-lookup"><span data-stu-id="71e68-313">Int32</span></span>|  
|<span data-ttu-id="71e68-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="71e68-314">FILTER_CONDITION</span></span>|<span data-ttu-id="71e68-315">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-315">String</span></span>|  
|<span data-ttu-id="71e68-316">TÜMLEŞİK</span><span class="sxs-lookup"><span data-stu-id="71e68-316">INTEGRATED</span></span>|<span data-ttu-id="71e68-317">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="71e68-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="71e68-318">Microsoft Oracle OLE DB Provider</span><span class="sxs-lookup"><span data-stu-id="71e68-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="71e68-319">Microsoft Oracle OLE DB sürücü ortak şeması koleksiyonları ek olarak aşağıdaki belirli şeması koleksiyonları destekler:</span><span class="sxs-lookup"><span data-stu-id="71e68-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="71e68-320">tabloları</span><span class="sxs-lookup"><span data-stu-id="71e68-320">Tables</span></span>  
  
-   <span data-ttu-id="71e68-321">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="71e68-321">Columns</span></span>  
  
-   <span data-ttu-id="71e68-322">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="71e68-322">Procedures</span></span>  
  
-   <span data-ttu-id="71e68-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="71e68-323">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="71e68-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="71e68-324">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="71e68-325">Görünümler</span><span class="sxs-lookup"><span data-stu-id="71e68-325">Views</span></span>  
  
-   <span data-ttu-id="71e68-326">Dizinler</span><span class="sxs-lookup"><span data-stu-id="71e68-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="71e68-327">tabloları</span><span class="sxs-lookup"><span data-stu-id="71e68-327">Tables</span></span>  
  
|<span data-ttu-id="71e68-328">columnName</span><span class="sxs-lookup"><span data-stu-id="71e68-328">ColumnName</span></span>|<span data-ttu-id="71e68-329">Veri türü</span><span class="sxs-lookup"><span data-stu-id="71e68-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="71e68-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="71e68-330">TABLE_CATALOG</span></span>|<span data-ttu-id="71e68-331">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-331">String</span></span>|  
|<span data-ttu-id="71e68-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="71e68-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="71e68-333">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-333">String</span></span>|  
|<span data-ttu-id="71e68-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="71e68-334">TABLE_NAME</span></span>|<span data-ttu-id="71e68-335">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-335">String</span></span>|  
|<span data-ttu-id="71e68-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="71e68-336">TABLE_TYPE</span></span>|<span data-ttu-id="71e68-337">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-337">String</span></span>|  
|<span data-ttu-id="71e68-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="71e68-338">TABLE_GUID</span></span>|<span data-ttu-id="71e68-339">Guid</span><span class="sxs-lookup"><span data-stu-id="71e68-339">Guid</span></span>|  
|<span data-ttu-id="71e68-340">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="71e68-340">DESCRIPTION</span></span>|<span data-ttu-id="71e68-341">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-341">String</span></span>|  
|<span data-ttu-id="71e68-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="71e68-342">TABLE_PROPID</span></span>|<span data-ttu-id="71e68-343">Int64</span><span class="sxs-lookup"><span data-stu-id="71e68-343">Int64</span></span>|  
|<span data-ttu-id="71e68-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="71e68-344">DATE_CREATED</span></span>|<span data-ttu-id="71e68-345">DateTime</span><span class="sxs-lookup"><span data-stu-id="71e68-345">DateTime</span></span>|  
|<span data-ttu-id="71e68-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="71e68-346">DATE_MODIFIED</span></span>|<span data-ttu-id="71e68-347">DateTime</span><span class="sxs-lookup"><span data-stu-id="71e68-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="71e68-348">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="71e68-348">Columns</span></span>  
  
|<span data-ttu-id="71e68-349">columnName</span><span class="sxs-lookup"><span data-stu-id="71e68-349">ColumnName</span></span>|<span data-ttu-id="71e68-350">Veri türü</span><span class="sxs-lookup"><span data-stu-id="71e68-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="71e68-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="71e68-351">TABLE_CATALOG</span></span>|<span data-ttu-id="71e68-352">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-352">String</span></span>|  
|<span data-ttu-id="71e68-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="71e68-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="71e68-354">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-354">String</span></span>|  
|<span data-ttu-id="71e68-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="71e68-355">TABLE_NAME</span></span>|<span data-ttu-id="71e68-356">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-356">String</span></span>|  
|<span data-ttu-id="71e68-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="71e68-357">COLUMN_NAME</span></span>|<span data-ttu-id="71e68-358">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-358">String</span></span>|  
|<span data-ttu-id="71e68-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="71e68-359">COLUMN_GUID</span></span>|<span data-ttu-id="71e68-360">Guid</span><span class="sxs-lookup"><span data-stu-id="71e68-360">Guid</span></span>|  
|<span data-ttu-id="71e68-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="71e68-361">COLUMN_PROPID</span></span>|<span data-ttu-id="71e68-362">Int64</span><span class="sxs-lookup"><span data-stu-id="71e68-362">Int64</span></span>|  
|<span data-ttu-id="71e68-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="71e68-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="71e68-364">Int64</span><span class="sxs-lookup"><span data-stu-id="71e68-364">Int64</span></span>|  
|<span data-ttu-id="71e68-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="71e68-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="71e68-366">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="71e68-366">Boolean</span></span>|  
|<span data-ttu-id="71e68-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="71e68-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="71e68-368">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-368">String</span></span>|  
|<span data-ttu-id="71e68-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="71e68-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="71e68-370">Int64</span><span class="sxs-lookup"><span data-stu-id="71e68-370">Int64</span></span>|  
|<span data-ttu-id="71e68-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="71e68-371">IS_NULLABLE</span></span>|<span data-ttu-id="71e68-372">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="71e68-372">Boolean</span></span>|  
|<span data-ttu-id="71e68-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="71e68-373">DATA_TYPE</span></span>|<span data-ttu-id="71e68-374">Int32</span><span class="sxs-lookup"><span data-stu-id="71e68-374">Int32</span></span>|  
|<span data-ttu-id="71e68-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="71e68-375">TYPE_GUID</span></span>|<span data-ttu-id="71e68-376">Guid</span><span class="sxs-lookup"><span data-stu-id="71e68-376">Guid</span></span>|  
|<span data-ttu-id="71e68-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="71e68-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="71e68-378">Int64</span><span class="sxs-lookup"><span data-stu-id="71e68-378">Int64</span></span>|  
|<span data-ttu-id="71e68-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="71e68-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="71e68-380">Int64</span><span class="sxs-lookup"><span data-stu-id="71e68-380">Int64</span></span>|  
|<span data-ttu-id="71e68-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="71e68-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="71e68-382">Int32</span><span class="sxs-lookup"><span data-stu-id="71e68-382">Int32</span></span>|  
|<span data-ttu-id="71e68-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="71e68-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="71e68-384">Int16</span><span class="sxs-lookup"><span data-stu-id="71e68-384">Int16</span></span>|  
|<span data-ttu-id="71e68-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="71e68-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="71e68-386">Int64</span><span class="sxs-lookup"><span data-stu-id="71e68-386">Int64</span></span>|  
|<span data-ttu-id="71e68-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="71e68-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="71e68-388">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-388">String</span></span>|  
|<span data-ttu-id="71e68-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="71e68-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="71e68-390">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-390">String</span></span>|  
|<span data-ttu-id="71e68-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="71e68-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="71e68-392">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-392">String</span></span>|  
|<span data-ttu-id="71e68-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="71e68-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="71e68-394">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-394">String</span></span>|  
|<span data-ttu-id="71e68-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="71e68-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="71e68-396">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-396">String</span></span>|  
|<span data-ttu-id="71e68-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="71e68-397">COLLATION_NAME</span></span>|<span data-ttu-id="71e68-398">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-398">String</span></span>|  
|<span data-ttu-id="71e68-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="71e68-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="71e68-400">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-400">String</span></span>|  
|<span data-ttu-id="71e68-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="71e68-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="71e68-402">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-402">String</span></span>|  
|<span data-ttu-id="71e68-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="71e68-403">DOMAIN_NAME</span></span>|<span data-ttu-id="71e68-404">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-404">String</span></span>|  
|<span data-ttu-id="71e68-405">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="71e68-405">DESCRIPTION</span></span>|<span data-ttu-id="71e68-406">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="71e68-407">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="71e68-407">Procedures</span></span>  
  
|<span data-ttu-id="71e68-408">columnName</span><span class="sxs-lookup"><span data-stu-id="71e68-408">ColumnName</span></span>|<span data-ttu-id="71e68-409">Veri türü</span><span class="sxs-lookup"><span data-stu-id="71e68-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="71e68-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="71e68-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="71e68-411">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-411">String</span></span>|  
|<span data-ttu-id="71e68-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="71e68-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="71e68-413">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-413">String</span></span>|  
|<span data-ttu-id="71e68-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="71e68-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="71e68-415">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-415">String</span></span>|  
|<span data-ttu-id="71e68-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="71e68-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="71e68-417">Int16</span><span class="sxs-lookup"><span data-stu-id="71e68-417">Int16</span></span>|  
|<span data-ttu-id="71e68-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="71e68-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="71e68-419">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-419">String</span></span>|  
|<span data-ttu-id="71e68-420">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="71e68-420">DESCRIPTION</span></span>|<span data-ttu-id="71e68-421">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-421">String</span></span>|  
|<span data-ttu-id="71e68-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="71e68-422">DATE_CREATED</span></span>|<span data-ttu-id="71e68-423">DateTime</span><span class="sxs-lookup"><span data-stu-id="71e68-423">DateTime</span></span>|  
|<span data-ttu-id="71e68-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="71e68-424">DATE_MODIFIED</span></span>|<span data-ttu-id="71e68-425">DateTime</span><span class="sxs-lookup"><span data-stu-id="71e68-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="71e68-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="71e68-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="71e68-427">columnName</span><span class="sxs-lookup"><span data-stu-id="71e68-427">ColumnName</span></span>|<span data-ttu-id="71e68-428">Veri türü</span><span class="sxs-lookup"><span data-stu-id="71e68-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="71e68-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="71e68-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="71e68-430">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-430">String</span></span>|  
|<span data-ttu-id="71e68-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="71e68-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="71e68-432">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-432">String</span></span>|  
|<span data-ttu-id="71e68-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="71e68-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="71e68-434">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-434">String</span></span>|  
|<span data-ttu-id="71e68-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="71e68-435">COLUMN_NAME</span></span>|<span data-ttu-id="71e68-436">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-436">String</span></span>|  
|<span data-ttu-id="71e68-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="71e68-437">COLUMN_GUID</span></span>|<span data-ttu-id="71e68-438">Guid</span><span class="sxs-lookup"><span data-stu-id="71e68-438">Guid</span></span>|  
|<span data-ttu-id="71e68-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="71e68-439">COLUMN_PROPID</span></span>|<span data-ttu-id="71e68-440">Int64</span><span class="sxs-lookup"><span data-stu-id="71e68-440">Int64</span></span>|  
|<span data-ttu-id="71e68-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="71e68-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="71e68-442">Int64</span><span class="sxs-lookup"><span data-stu-id="71e68-442">Int64</span></span>|  
|<span data-ttu-id="71e68-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="71e68-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="71e68-444">Int64</span><span class="sxs-lookup"><span data-stu-id="71e68-444">Int64</span></span>|  
|<span data-ttu-id="71e68-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="71e68-445">IS_NULLABLE</span></span>|<span data-ttu-id="71e68-446">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="71e68-446">Boolean</span></span>|  
|<span data-ttu-id="71e68-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="71e68-447">DATA_TYPE</span></span>|<span data-ttu-id="71e68-448">Int32</span><span class="sxs-lookup"><span data-stu-id="71e68-448">Int32</span></span>|  
|<span data-ttu-id="71e68-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="71e68-449">TYPE_GUID</span></span>|<span data-ttu-id="71e68-450">Guid</span><span class="sxs-lookup"><span data-stu-id="71e68-450">Guid</span></span>|  
|<span data-ttu-id="71e68-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="71e68-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="71e68-452">Int64</span><span class="sxs-lookup"><span data-stu-id="71e68-452">Int64</span></span>|  
|<span data-ttu-id="71e68-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="71e68-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="71e68-454">Int64</span><span class="sxs-lookup"><span data-stu-id="71e68-454">Int64</span></span>|  
|<span data-ttu-id="71e68-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="71e68-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="71e68-456">Int32</span><span class="sxs-lookup"><span data-stu-id="71e68-456">Int32</span></span>|  
|<span data-ttu-id="71e68-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="71e68-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="71e68-458">Int16</span><span class="sxs-lookup"><span data-stu-id="71e68-458">Int16</span></span>|  
|<span data-ttu-id="71e68-459">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="71e68-459">DESCRIPTION</span></span>|<span data-ttu-id="71e68-460">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-460">String</span></span>|  
|<span data-ttu-id="71e68-461">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="71e68-461">OVERLOAD</span></span>|<span data-ttu-id="71e68-462">Int16</span><span class="sxs-lookup"><span data-stu-id="71e68-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="71e68-463">Görünümler</span><span class="sxs-lookup"><span data-stu-id="71e68-463">Views</span></span>  
  
|<span data-ttu-id="71e68-464">columnName</span><span class="sxs-lookup"><span data-stu-id="71e68-464">ColumnName</span></span>|<span data-ttu-id="71e68-465">Veri türü</span><span class="sxs-lookup"><span data-stu-id="71e68-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="71e68-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="71e68-466">TABLE_CATALOG</span></span>|<span data-ttu-id="71e68-467">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-467">String</span></span>|  
|<span data-ttu-id="71e68-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="71e68-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="71e68-469">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-469">String</span></span>|  
|<span data-ttu-id="71e68-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="71e68-470">TABLE_NAME</span></span>|<span data-ttu-id="71e68-471">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-471">String</span></span>|  
|<span data-ttu-id="71e68-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="71e68-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="71e68-473">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-473">String</span></span>|  
|<span data-ttu-id="71e68-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="71e68-474">CHECK_OPTION</span></span>|<span data-ttu-id="71e68-475">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="71e68-475">Boolean</span></span>|  
|<span data-ttu-id="71e68-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="71e68-476">IS_UPDATABLE</span></span>|<span data-ttu-id="71e68-477">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="71e68-477">Boolean</span></span>|  
|<span data-ttu-id="71e68-478">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="71e68-478">DESCRIPTION</span></span>|<span data-ttu-id="71e68-479">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-479">String</span></span>|  
|<span data-ttu-id="71e68-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="71e68-480">DATE_CREATED</span></span>|<span data-ttu-id="71e68-481">DateTime</span><span class="sxs-lookup"><span data-stu-id="71e68-481">DateTime</span></span>|  
|<span data-ttu-id="71e68-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="71e68-482">DATE_MODIFIED</span></span>|<span data-ttu-id="71e68-483">DateTime</span><span class="sxs-lookup"><span data-stu-id="71e68-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="71e68-484">Dizinler</span><span class="sxs-lookup"><span data-stu-id="71e68-484">Indexes</span></span>  
  
|<span data-ttu-id="71e68-485">columnName</span><span class="sxs-lookup"><span data-stu-id="71e68-485">ColumnName</span></span>|<span data-ttu-id="71e68-486">Veri türü</span><span class="sxs-lookup"><span data-stu-id="71e68-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="71e68-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="71e68-487">TABLE_CATALOG</span></span>|<span data-ttu-id="71e68-488">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-488">String</span></span>|  
|<span data-ttu-id="71e68-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="71e68-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="71e68-490">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-490">String</span></span>|  
|<span data-ttu-id="71e68-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="71e68-491">TABLE_NAME</span></span>|<span data-ttu-id="71e68-492">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-492">String</span></span>|  
|<span data-ttu-id="71e68-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="71e68-493">INDEX_CATALOG</span></span>|<span data-ttu-id="71e68-494">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-494">String</span></span>|  
|<span data-ttu-id="71e68-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="71e68-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="71e68-496">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-496">String</span></span>|  
|<span data-ttu-id="71e68-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="71e68-497">INDEX_NAME</span></span>|<span data-ttu-id="71e68-498">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-498">String</span></span>|  
|<span data-ttu-id="71e68-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="71e68-499">PRIMARY_KEY</span></span>|<span data-ttu-id="71e68-500">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="71e68-500">Boolean</span></span>|  
|<span data-ttu-id="71e68-501">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="71e68-501">UNIQUE</span></span>|<span data-ttu-id="71e68-502">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="71e68-502">Boolean</span></span>|  
|<span data-ttu-id="71e68-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="71e68-503">CLUSTERED</span></span>|<span data-ttu-id="71e68-504">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="71e68-504">Boolean</span></span>|  
|<span data-ttu-id="71e68-505">TÜRÜ</span><span class="sxs-lookup"><span data-stu-id="71e68-505">TYPE</span></span>|<span data-ttu-id="71e68-506">Int32</span><span class="sxs-lookup"><span data-stu-id="71e68-506">Int32</span></span>|  
|<span data-ttu-id="71e68-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="71e68-507">FILL_FACTOR</span></span>|<span data-ttu-id="71e68-508">Int32</span><span class="sxs-lookup"><span data-stu-id="71e68-508">Int32</span></span>|  
|<span data-ttu-id="71e68-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="71e68-509">INITIAL_SIZE</span></span>|<span data-ttu-id="71e68-510">Int32</span><span class="sxs-lookup"><span data-stu-id="71e68-510">Int32</span></span>|  
|<span data-ttu-id="71e68-511">NULLS</span><span class="sxs-lookup"><span data-stu-id="71e68-511">NULLS</span></span>|<span data-ttu-id="71e68-512">Int32</span><span class="sxs-lookup"><span data-stu-id="71e68-512">Int32</span></span>|  
|<span data-ttu-id="71e68-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="71e68-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="71e68-514">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="71e68-514">Boolean</span></span>|  
|<span data-ttu-id="71e68-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="71e68-515">AUTO_UPDATE</span></span>|<span data-ttu-id="71e68-516">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="71e68-516">Boolean</span></span>|  
|<span data-ttu-id="71e68-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="71e68-517">NULL_COLLATION</span></span>|<span data-ttu-id="71e68-518">Int32</span><span class="sxs-lookup"><span data-stu-id="71e68-518">Int32</span></span>|  
|<span data-ttu-id="71e68-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="71e68-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="71e68-520">Int64</span><span class="sxs-lookup"><span data-stu-id="71e68-520">Int64</span></span>|  
|<span data-ttu-id="71e68-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="71e68-521">COLUMN_NAME</span></span>|<span data-ttu-id="71e68-522">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-522">String</span></span>|  
|<span data-ttu-id="71e68-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="71e68-523">COLUMN_GUID</span></span>|<span data-ttu-id="71e68-524">Guid</span><span class="sxs-lookup"><span data-stu-id="71e68-524">Guid</span></span>|  
|<span data-ttu-id="71e68-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="71e68-525">COLUMN_PROPID</span></span>|<span data-ttu-id="71e68-526">Int64</span><span class="sxs-lookup"><span data-stu-id="71e68-526">Int64</span></span>|  
|<span data-ttu-id="71e68-527">HARMANLAMA</span><span class="sxs-lookup"><span data-stu-id="71e68-527">COLLATION</span></span>|<span data-ttu-id="71e68-528">Int16</span><span class="sxs-lookup"><span data-stu-id="71e68-528">Int16</span></span>|  
|<span data-ttu-id="71e68-529">ÖNEM DÜZEYİ</span><span class="sxs-lookup"><span data-stu-id="71e68-529">CARDINALITY</span></span>|<span data-ttu-id="71e68-530">Ondalık</span><span class="sxs-lookup"><span data-stu-id="71e68-530">Decimal</span></span>|  
|<span data-ttu-id="71e68-531">SAYFALARI</span><span class="sxs-lookup"><span data-stu-id="71e68-531">PAGES</span></span>|<span data-ttu-id="71e68-532">Int32</span><span class="sxs-lookup"><span data-stu-id="71e68-532">Int32</span></span>|  
|<span data-ttu-id="71e68-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="71e68-533">FILTER_CONDITION</span></span>|<span data-ttu-id="71e68-534">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-534">String</span></span>|  
|<span data-ttu-id="71e68-535">TÜMLEŞİK</span><span class="sxs-lookup"><span data-stu-id="71e68-535">INTEGRATED</span></span>|<span data-ttu-id="71e68-536">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="71e68-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="71e68-537">Microsoft Jet OLE DB sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="71e68-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="71e68-538">Microsoft Jet OLE DB sürücü ortak şeması koleksiyonları ek olarak aşağıdaki belirli şeması koleksiyonları destekler:</span><span class="sxs-lookup"><span data-stu-id="71e68-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="71e68-539">tabloları</span><span class="sxs-lookup"><span data-stu-id="71e68-539">Tables</span></span>  
  
-   <span data-ttu-id="71e68-540">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="71e68-540">Columns</span></span>  
  
-   <span data-ttu-id="71e68-541">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="71e68-541">Procedures</span></span>  
  
-   <span data-ttu-id="71e68-542">Görünümler</span><span class="sxs-lookup"><span data-stu-id="71e68-542">Views</span></span>  
  
-   <span data-ttu-id="71e68-543">Dizinler</span><span class="sxs-lookup"><span data-stu-id="71e68-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="71e68-544">tabloları</span><span class="sxs-lookup"><span data-stu-id="71e68-544">Tables</span></span>  
  
|<span data-ttu-id="71e68-545">columnName</span><span class="sxs-lookup"><span data-stu-id="71e68-545">ColumnName</span></span>|<span data-ttu-id="71e68-546">Veri türü</span><span class="sxs-lookup"><span data-stu-id="71e68-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="71e68-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="71e68-547">TABLE_CATALOG</span></span>|<span data-ttu-id="71e68-548">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-548">String</span></span>|  
|<span data-ttu-id="71e68-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="71e68-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="71e68-550">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-550">String</span></span>|  
|<span data-ttu-id="71e68-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="71e68-551">TABLE_NAME</span></span>|<span data-ttu-id="71e68-552">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-552">String</span></span>|  
|<span data-ttu-id="71e68-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="71e68-553">TABLE_TYPE</span></span>|<span data-ttu-id="71e68-554">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-554">String</span></span>|  
|<span data-ttu-id="71e68-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="71e68-555">TABLE_GUID</span></span>|<span data-ttu-id="71e68-556">Guid</span><span class="sxs-lookup"><span data-stu-id="71e68-556">Guid</span></span>|  
|<span data-ttu-id="71e68-557">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="71e68-557">DESCRIPTION</span></span>|<span data-ttu-id="71e68-558">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-558">String</span></span>|  
|<span data-ttu-id="71e68-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="71e68-559">TABLE_PROPID</span></span>|<span data-ttu-id="71e68-560">Int64</span><span class="sxs-lookup"><span data-stu-id="71e68-560">Int64</span></span>|  
|<span data-ttu-id="71e68-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="71e68-561">DATE_CREATED</span></span>|<span data-ttu-id="71e68-562">DateTime</span><span class="sxs-lookup"><span data-stu-id="71e68-562">DateTime</span></span>|  
|<span data-ttu-id="71e68-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="71e68-563">DATE_MODIFIED</span></span>|<span data-ttu-id="71e68-564">DateTime</span><span class="sxs-lookup"><span data-stu-id="71e68-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="71e68-565">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="71e68-565">Columns</span></span>  
  
|<span data-ttu-id="71e68-566">columnName</span><span class="sxs-lookup"><span data-stu-id="71e68-566">ColumnName</span></span>|<span data-ttu-id="71e68-567">Veri türü</span><span class="sxs-lookup"><span data-stu-id="71e68-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="71e68-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="71e68-568">TABLE_CATALOG</span></span>|<span data-ttu-id="71e68-569">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-569">String</span></span>|  
|<span data-ttu-id="71e68-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="71e68-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="71e68-571">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-571">String</span></span>|  
|<span data-ttu-id="71e68-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="71e68-572">TABLE_NAME</span></span>|<span data-ttu-id="71e68-573">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-573">String</span></span>|  
|<span data-ttu-id="71e68-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="71e68-574">COLUMN_NAME</span></span>|<span data-ttu-id="71e68-575">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-575">String</span></span>|  
|<span data-ttu-id="71e68-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="71e68-576">COLUMN_GUID</span></span>|<span data-ttu-id="71e68-577">Guid</span><span class="sxs-lookup"><span data-stu-id="71e68-577">Guid</span></span>|  
|<span data-ttu-id="71e68-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="71e68-578">COLUMN_PROPID</span></span>|<span data-ttu-id="71e68-579">Int64</span><span class="sxs-lookup"><span data-stu-id="71e68-579">Int64</span></span>|  
|<span data-ttu-id="71e68-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="71e68-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="71e68-581">Int64</span><span class="sxs-lookup"><span data-stu-id="71e68-581">Int64</span></span>|  
|<span data-ttu-id="71e68-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="71e68-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="71e68-583">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="71e68-583">Boolean</span></span>|  
|<span data-ttu-id="71e68-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="71e68-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="71e68-585">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-585">String</span></span>|  
|<span data-ttu-id="71e68-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="71e68-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="71e68-587">Int64</span><span class="sxs-lookup"><span data-stu-id="71e68-587">Int64</span></span>|  
|<span data-ttu-id="71e68-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="71e68-588">IS_NULLABLE</span></span>|<span data-ttu-id="71e68-589">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="71e68-589">Boolean</span></span>|  
|<span data-ttu-id="71e68-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="71e68-590">DATA_TYPE</span></span>|<span data-ttu-id="71e68-591">Int32</span><span class="sxs-lookup"><span data-stu-id="71e68-591">Int32</span></span>|  
|<span data-ttu-id="71e68-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="71e68-592">TYPE_GUID</span></span>|<span data-ttu-id="71e68-593">Guid</span><span class="sxs-lookup"><span data-stu-id="71e68-593">Guid</span></span>|  
|<span data-ttu-id="71e68-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="71e68-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="71e68-595">Int64</span><span class="sxs-lookup"><span data-stu-id="71e68-595">Int64</span></span>|  
|<span data-ttu-id="71e68-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="71e68-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="71e68-597">Int64</span><span class="sxs-lookup"><span data-stu-id="71e68-597">Int64</span></span>|  
|<span data-ttu-id="71e68-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="71e68-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="71e68-599">Int32</span><span class="sxs-lookup"><span data-stu-id="71e68-599">Int32</span></span>|  
|<span data-ttu-id="71e68-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="71e68-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="71e68-601">Int16</span><span class="sxs-lookup"><span data-stu-id="71e68-601">Int16</span></span>|  
|<span data-ttu-id="71e68-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="71e68-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="71e68-603">Int64</span><span class="sxs-lookup"><span data-stu-id="71e68-603">Int64</span></span>|  
|<span data-ttu-id="71e68-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="71e68-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="71e68-605">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-605">String</span></span>|  
|<span data-ttu-id="71e68-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="71e68-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="71e68-607">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-607">String</span></span>|  
|<span data-ttu-id="71e68-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="71e68-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="71e68-609">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-609">String</span></span>|  
|<span data-ttu-id="71e68-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="71e68-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="71e68-611">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-611">String</span></span>|  
|<span data-ttu-id="71e68-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="71e68-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="71e68-613">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-613">String</span></span>|  
|<span data-ttu-id="71e68-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="71e68-614">COLLATION_NAME</span></span>|<span data-ttu-id="71e68-615">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-615">String</span></span>|  
|<span data-ttu-id="71e68-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="71e68-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="71e68-617">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-617">String</span></span>|  
|<span data-ttu-id="71e68-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="71e68-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="71e68-619">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-619">String</span></span>|  
|<span data-ttu-id="71e68-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="71e68-620">DOMAIN_NAME</span></span>|<span data-ttu-id="71e68-621">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-621">String</span></span>|  
|<span data-ttu-id="71e68-622">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="71e68-622">DESCRIPTION</span></span>|<span data-ttu-id="71e68-623">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="71e68-624">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="71e68-624">Procedures</span></span>  
  
|<span data-ttu-id="71e68-625">columnName</span><span class="sxs-lookup"><span data-stu-id="71e68-625">ColumnName</span></span>|<span data-ttu-id="71e68-626">Veri türü</span><span class="sxs-lookup"><span data-stu-id="71e68-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="71e68-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="71e68-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="71e68-628">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-628">String</span></span>|  
|<span data-ttu-id="71e68-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="71e68-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="71e68-630">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-630">String</span></span>|  
|<span data-ttu-id="71e68-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="71e68-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="71e68-632">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-632">String</span></span>|  
|<span data-ttu-id="71e68-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="71e68-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="71e68-634">Int16</span><span class="sxs-lookup"><span data-stu-id="71e68-634">Int16</span></span>|  
|<span data-ttu-id="71e68-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="71e68-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="71e68-636">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-636">String</span></span>|  
|<span data-ttu-id="71e68-637">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="71e68-637">DESCRIPTION</span></span>|<span data-ttu-id="71e68-638">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-638">String</span></span>|  
|<span data-ttu-id="71e68-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="71e68-639">DATE_CREATED</span></span>|<span data-ttu-id="71e68-640">DateTime</span><span class="sxs-lookup"><span data-stu-id="71e68-640">DateTime</span></span>|  
|<span data-ttu-id="71e68-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="71e68-641">DATE_MODIFIED</span></span>|<span data-ttu-id="71e68-642">DateTime</span><span class="sxs-lookup"><span data-stu-id="71e68-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="71e68-643">Görünümler</span><span class="sxs-lookup"><span data-stu-id="71e68-643">Views</span></span>  
  
|<span data-ttu-id="71e68-644">columnName</span><span class="sxs-lookup"><span data-stu-id="71e68-644">ColumnName</span></span>|<span data-ttu-id="71e68-645">Veri türü</span><span class="sxs-lookup"><span data-stu-id="71e68-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="71e68-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="71e68-646">TABLE_CATALOG</span></span>|<span data-ttu-id="71e68-647">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-647">String</span></span>|  
|<span data-ttu-id="71e68-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="71e68-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="71e68-649">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-649">String</span></span>|  
|<span data-ttu-id="71e68-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="71e68-650">TABLE_NAME</span></span>|<span data-ttu-id="71e68-651">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-651">String</span></span>|  
|<span data-ttu-id="71e68-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="71e68-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="71e68-653">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-653">String</span></span>|  
|<span data-ttu-id="71e68-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="71e68-654">CHECK_OPTION</span></span>|<span data-ttu-id="71e68-655">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="71e68-655">Boolean</span></span>|  
|<span data-ttu-id="71e68-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="71e68-656">IS_UPDATABLE</span></span>|<span data-ttu-id="71e68-657">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="71e68-657">Boolean</span></span>|  
|<span data-ttu-id="71e68-658">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="71e68-658">DESCRIPTION</span></span>|<span data-ttu-id="71e68-659">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-659">String</span></span>|  
|<span data-ttu-id="71e68-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="71e68-660">DATE_CREATED</span></span>|<span data-ttu-id="71e68-661">DateTime</span><span class="sxs-lookup"><span data-stu-id="71e68-661">DateTime</span></span>|  
|<span data-ttu-id="71e68-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="71e68-662">DATE_MODIFIED</span></span>|<span data-ttu-id="71e68-663">DateTime</span><span class="sxs-lookup"><span data-stu-id="71e68-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="71e68-664">Dizinler</span><span class="sxs-lookup"><span data-stu-id="71e68-664">Indexes</span></span>  
  
|<span data-ttu-id="71e68-665">columnName</span><span class="sxs-lookup"><span data-stu-id="71e68-665">ColumnName</span></span>|<span data-ttu-id="71e68-666">Veri türü</span><span class="sxs-lookup"><span data-stu-id="71e68-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="71e68-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="71e68-667">TABLE_CATALOG</span></span>|<span data-ttu-id="71e68-668">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-668">String</span></span>|  
|<span data-ttu-id="71e68-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="71e68-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="71e68-670">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-670">String</span></span>|  
|<span data-ttu-id="71e68-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="71e68-671">TABLE_NAME</span></span>|<span data-ttu-id="71e68-672">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-672">String</span></span>|  
|<span data-ttu-id="71e68-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="71e68-673">INDEX_CATALOG</span></span>|<span data-ttu-id="71e68-674">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-674">String</span></span>|  
|<span data-ttu-id="71e68-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="71e68-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="71e68-676">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-676">String</span></span>|  
|<span data-ttu-id="71e68-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="71e68-677">INDEX_NAME</span></span>|<span data-ttu-id="71e68-678">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-678">String</span></span>|  
|<span data-ttu-id="71e68-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="71e68-679">PRIMARY_KEY</span></span>|<span data-ttu-id="71e68-680">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="71e68-680">Boolean</span></span>|  
|<span data-ttu-id="71e68-681">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="71e68-681">UNIQUE</span></span>|<span data-ttu-id="71e68-682">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="71e68-682">Boolean</span></span>|  
|<span data-ttu-id="71e68-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="71e68-683">CLUSTERED</span></span>|<span data-ttu-id="71e68-684">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="71e68-684">Boolean</span></span>|  
|<span data-ttu-id="71e68-685">TÜRÜ</span><span class="sxs-lookup"><span data-stu-id="71e68-685">TYPE</span></span>|<span data-ttu-id="71e68-686">Int32</span><span class="sxs-lookup"><span data-stu-id="71e68-686">Int32</span></span>|  
|<span data-ttu-id="71e68-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="71e68-687">FILL_FACTOR</span></span>|<span data-ttu-id="71e68-688">Int32</span><span class="sxs-lookup"><span data-stu-id="71e68-688">Int32</span></span>|  
|<span data-ttu-id="71e68-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="71e68-689">INITIAL_SIZE</span></span>|<span data-ttu-id="71e68-690">Int32</span><span class="sxs-lookup"><span data-stu-id="71e68-690">Int32</span></span>|  
|<span data-ttu-id="71e68-691">NULLS</span><span class="sxs-lookup"><span data-stu-id="71e68-691">NULLS</span></span>|<span data-ttu-id="71e68-692">Int32</span><span class="sxs-lookup"><span data-stu-id="71e68-692">Int32</span></span>|  
|<span data-ttu-id="71e68-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="71e68-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="71e68-694">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="71e68-694">Boolean</span></span>|  
|<span data-ttu-id="71e68-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="71e68-695">AUTO_UPDATE</span></span>|<span data-ttu-id="71e68-696">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="71e68-696">Boolean</span></span>|  
|<span data-ttu-id="71e68-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="71e68-697">NULL_COLLATION</span></span>|<span data-ttu-id="71e68-698">Int32</span><span class="sxs-lookup"><span data-stu-id="71e68-698">Int32</span></span>|  
|<span data-ttu-id="71e68-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="71e68-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="71e68-700">Int64</span><span class="sxs-lookup"><span data-stu-id="71e68-700">Int64</span></span>|  
|<span data-ttu-id="71e68-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="71e68-701">COLUMN_NAME</span></span>|<span data-ttu-id="71e68-702">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-702">String</span></span>|  
|<span data-ttu-id="71e68-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="71e68-703">COLUMN_GUID</span></span>|<span data-ttu-id="71e68-704">Guid</span><span class="sxs-lookup"><span data-stu-id="71e68-704">Guid</span></span>|  
|<span data-ttu-id="71e68-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="71e68-705">COLUMN_PROPID</span></span>|<span data-ttu-id="71e68-706">Int64</span><span class="sxs-lookup"><span data-stu-id="71e68-706">Int64</span></span>|  
|<span data-ttu-id="71e68-707">HARMANLAMA</span><span class="sxs-lookup"><span data-stu-id="71e68-707">COLLATION</span></span>|<span data-ttu-id="71e68-708">Int16</span><span class="sxs-lookup"><span data-stu-id="71e68-708">Int16</span></span>|  
|<span data-ttu-id="71e68-709">ÖNEM DÜZEYİ</span><span class="sxs-lookup"><span data-stu-id="71e68-709">CARDINALITY</span></span>|<span data-ttu-id="71e68-710">Ondalık</span><span class="sxs-lookup"><span data-stu-id="71e68-710">Decimal</span></span>|  
|<span data-ttu-id="71e68-711">SAYFALARI</span><span class="sxs-lookup"><span data-stu-id="71e68-711">PAGES</span></span>|<span data-ttu-id="71e68-712">Int32</span><span class="sxs-lookup"><span data-stu-id="71e68-712">Int32</span></span>|  
|<span data-ttu-id="71e68-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="71e68-713">FILTER_CONDITION</span></span>|<span data-ttu-id="71e68-714">Dize</span><span class="sxs-lookup"><span data-stu-id="71e68-714">String</span></span>|  
|<span data-ttu-id="71e68-715">TÜMLEŞİK</span><span class="sxs-lookup"><span data-stu-id="71e68-715">INTEGRATED</span></span>|<span data-ttu-id="71e68-716">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="71e68-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="71e68-717">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="71e68-717">See Also</span></span>  
 [<span data-ttu-id="71e68-718">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="71e68-718">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
