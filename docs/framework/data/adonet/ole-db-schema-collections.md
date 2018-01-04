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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: e120ea532b6da455e31ce7345b6c4b2be1ec975f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="0b762-102">OLE DB şeması koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="0b762-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="0b762-103">Bu bölümde, Microsoft SQL Server, Oracle ve Microsoft Jet için OLE DB sağlayıcıları şema koleksiyonu desteği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0b762-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="0b762-104">Microsoft SQL Server OLE DB sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="0b762-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="0b762-105">Microsoft SQL Server OLE DB sürücüsü ortak şeması koleksiyonları ek olarak aşağıdaki belirli şeması koleksiyonları destekler:</span><span class="sxs-lookup"><span data-stu-id="0b762-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="0b762-106">tabloları</span><span class="sxs-lookup"><span data-stu-id="0b762-106">Tables</span></span>  
  
-   <span data-ttu-id="0b762-107">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="0b762-107">Columns</span></span>  
  
-   <span data-ttu-id="0b762-108">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="0b762-108">Procedures</span></span>  
  
-   <span data-ttu-id="0b762-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="0b762-109">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="0b762-110">Katalog</span><span class="sxs-lookup"><span data-stu-id="0b762-110">Catalog</span></span>  
  
-   <span data-ttu-id="0b762-111">Dizinler</span><span class="sxs-lookup"><span data-stu-id="0b762-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="0b762-112">tabloları</span><span class="sxs-lookup"><span data-stu-id="0b762-112">Tables</span></span>  
  
|<span data-ttu-id="0b762-113">columnName</span><span class="sxs-lookup"><span data-stu-id="0b762-113">ColumnName</span></span>|<span data-ttu-id="0b762-114">Veri türü</span><span class="sxs-lookup"><span data-stu-id="0b762-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0b762-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b762-115">TABLE_CATALOG</span></span>|<span data-ttu-id="0b762-116">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-116">String</span></span>|  
|<span data-ttu-id="0b762-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b762-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="0b762-118">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-118">String</span></span>|  
|<span data-ttu-id="0b762-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0b762-119">TABLE_NAME</span></span>|<span data-ttu-id="0b762-120">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-120">String</span></span>|  
|<span data-ttu-id="0b762-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0b762-121">TABLE_TYPE</span></span>|<span data-ttu-id="0b762-122">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-122">String</span></span>|  
|<span data-ttu-id="0b762-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="0b762-123">TABLE_GUID</span></span>|<span data-ttu-id="0b762-124">Guid</span><span class="sxs-lookup"><span data-stu-id="0b762-124">Guid</span></span>|  
|<span data-ttu-id="0b762-125">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="0b762-125">DESCRIPTION</span></span>|<span data-ttu-id="0b762-126">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-126">String</span></span>|  
|<span data-ttu-id="0b762-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="0b762-127">TABLE_PROPID</span></span>|<span data-ttu-id="0b762-128">Int64</span><span class="sxs-lookup"><span data-stu-id="0b762-128">Int64</span></span>|  
|<span data-ttu-id="0b762-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="0b762-129">DATE_CREATED</span></span>|<span data-ttu-id="0b762-130">DateTime</span><span class="sxs-lookup"><span data-stu-id="0b762-130">DateTime</span></span>|  
|<span data-ttu-id="0b762-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="0b762-131">DATE_MODIFIED</span></span>|<span data-ttu-id="0b762-132">DateTime</span><span class="sxs-lookup"><span data-stu-id="0b762-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="0b762-133">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="0b762-133">Columns</span></span>  
  
|<span data-ttu-id="0b762-134">columnName</span><span class="sxs-lookup"><span data-stu-id="0b762-134">ColumnName</span></span>|<span data-ttu-id="0b762-135">Veri türü</span><span class="sxs-lookup"><span data-stu-id="0b762-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0b762-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b762-136">TABLE_CATALOG</span></span>|<span data-ttu-id="0b762-137">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-137">String</span></span>|  
|<span data-ttu-id="0b762-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b762-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="0b762-139">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-139">String</span></span>|  
|<span data-ttu-id="0b762-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0b762-140">TABLE_NAME</span></span>|<span data-ttu-id="0b762-141">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-141">String</span></span>|  
|<span data-ttu-id="0b762-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0b762-142">COLUMN_NAME</span></span>|<span data-ttu-id="0b762-143">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-143">String</span></span>|  
|<span data-ttu-id="0b762-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="0b762-144">COLUMN_GUID</span></span>|<span data-ttu-id="0b762-145">Guid</span><span class="sxs-lookup"><span data-stu-id="0b762-145">Guid</span></span>|  
|<span data-ttu-id="0b762-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="0b762-146">COLUMN_PROPID</span></span>|<span data-ttu-id="0b762-147">Int64</span><span class="sxs-lookup"><span data-stu-id="0b762-147">Int64</span></span>|  
|<span data-ttu-id="0b762-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0b762-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="0b762-149">Int64</span><span class="sxs-lookup"><span data-stu-id="0b762-149">Int64</span></span>|  
|<span data-ttu-id="0b762-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="0b762-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="0b762-151">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="0b762-151">Boolean</span></span>|  
|<span data-ttu-id="0b762-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="0b762-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="0b762-153">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-153">String</span></span>|  
|<span data-ttu-id="0b762-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="0b762-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="0b762-155">Int64</span><span class="sxs-lookup"><span data-stu-id="0b762-155">Int64</span></span>|  
|<span data-ttu-id="0b762-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0b762-156">IS_NULLABLE</span></span>|<span data-ttu-id="0b762-157">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="0b762-157">Boolean</span></span>|  
|<span data-ttu-id="0b762-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0b762-158">DATA_TYPE</span></span>|<span data-ttu-id="0b762-159">Int32</span><span class="sxs-lookup"><span data-stu-id="0b762-159">Int32</span></span>|  
|<span data-ttu-id="0b762-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="0b762-160">TYPE_GUID</span></span>|<span data-ttu-id="0b762-161">Guid</span><span class="sxs-lookup"><span data-stu-id="0b762-161">Guid</span></span>|  
|<span data-ttu-id="0b762-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0b762-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="0b762-163">Int64</span><span class="sxs-lookup"><span data-stu-id="0b762-163">Int64</span></span>|  
|<span data-ttu-id="0b762-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0b762-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="0b762-165">Int64</span><span class="sxs-lookup"><span data-stu-id="0b762-165">Int64</span></span>|  
|<span data-ttu-id="0b762-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="0b762-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="0b762-167">Int32</span><span class="sxs-lookup"><span data-stu-id="0b762-167">Int32</span></span>|  
|<span data-ttu-id="0b762-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="0b762-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="0b762-169">Int16</span><span class="sxs-lookup"><span data-stu-id="0b762-169">Int16</span></span>|  
|<span data-ttu-id="0b762-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="0b762-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="0b762-171">Int64</span><span class="sxs-lookup"><span data-stu-id="0b762-171">Int64</span></span>|  
|<span data-ttu-id="0b762-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b762-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="0b762-173">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-173">String</span></span>|  
|<span data-ttu-id="0b762-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b762-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="0b762-175">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-175">String</span></span>|  
|<span data-ttu-id="0b762-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="0b762-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="0b762-177">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-177">String</span></span>|  
|<span data-ttu-id="0b762-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b762-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="0b762-179">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-179">String</span></span>|  
|<span data-ttu-id="0b762-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b762-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="0b762-181">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-181">String</span></span>|  
|<span data-ttu-id="0b762-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="0b762-182">COLLATION_NAME</span></span>|<span data-ttu-id="0b762-183">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-183">String</span></span>|  
|<span data-ttu-id="0b762-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b762-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="0b762-185">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-185">String</span></span>|  
|<span data-ttu-id="0b762-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b762-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="0b762-187">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-187">String</span></span>|  
|<span data-ttu-id="0b762-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="0b762-188">DOMAIN_NAME</span></span>|<span data-ttu-id="0b762-189">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-189">String</span></span>|  
|<span data-ttu-id="0b762-190">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="0b762-190">DESCRIPTION</span></span>|<span data-ttu-id="0b762-191">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-191">String</span></span>|  
|<span data-ttu-id="0b762-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="0b762-192">COLUMN_LCID</span></span>|<span data-ttu-id="0b762-193">Int32</span><span class="sxs-lookup"><span data-stu-id="0b762-193">Int32</span></span>|  
|<span data-ttu-id="0b762-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="0b762-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="0b762-195">Int32</span><span class="sxs-lookup"><span data-stu-id="0b762-195">Int32</span></span>|  
|<span data-ttu-id="0b762-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="0b762-196">COLUMN_SORTID</span></span>|<span data-ttu-id="0b762-197">Int32</span><span class="sxs-lookup"><span data-stu-id="0b762-197">Int32</span></span>|  
|<span data-ttu-id="0b762-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="0b762-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="0b762-199">Byte]</span><span class="sxs-lookup"><span data-stu-id="0b762-199">Byte[]</span></span>|  
|<span data-ttu-id="0b762-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="0b762-200">IS_COMPUTED</span></span>|<span data-ttu-id="0b762-201">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="0b762-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="0b762-202">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="0b762-202">Procedures</span></span>  
  
|<span data-ttu-id="0b762-203">columnName</span><span class="sxs-lookup"><span data-stu-id="0b762-203">ColumnName</span></span>|<span data-ttu-id="0b762-204">Veri türü</span><span class="sxs-lookup"><span data-stu-id="0b762-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0b762-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b762-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="0b762-206">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-206">String</span></span>|  
|<span data-ttu-id="0b762-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b762-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="0b762-208">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-208">String</span></span>|  
|<span data-ttu-id="0b762-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0b762-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="0b762-210">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-210">String</span></span>|  
|<span data-ttu-id="0b762-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0b762-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="0b762-212">Int16</span><span class="sxs-lookup"><span data-stu-id="0b762-212">Int16</span></span>|  
|<span data-ttu-id="0b762-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="0b762-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="0b762-214">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-214">String</span></span>|  
|<span data-ttu-id="0b762-215">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="0b762-215">DESCRIPTION</span></span>|<span data-ttu-id="0b762-216">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-216">String</span></span>|  
|<span data-ttu-id="0b762-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="0b762-217">DATE_CREATED</span></span>|<span data-ttu-id="0b762-218">DateTime</span><span class="sxs-lookup"><span data-stu-id="0b762-218">DateTime</span></span>|  
|<span data-ttu-id="0b762-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="0b762-219">DATE_MODIFIED</span></span>|<span data-ttu-id="0b762-220">DateTime</span><span class="sxs-lookup"><span data-stu-id="0b762-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="0b762-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="0b762-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="0b762-222">columnName</span><span class="sxs-lookup"><span data-stu-id="0b762-222">ColumnName</span></span>|<span data-ttu-id="0b762-223">Veri türü</span><span class="sxs-lookup"><span data-stu-id="0b762-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0b762-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b762-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="0b762-225">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-225">String</span></span>|  
|<span data-ttu-id="0b762-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b762-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="0b762-227">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-227">String</span></span>|  
|<span data-ttu-id="0b762-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0b762-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="0b762-229">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-229">String</span></span>|  
|<span data-ttu-id="0b762-230">PARAMETRE_ADÝ</span><span class="sxs-lookup"><span data-stu-id="0b762-230">PARAMETER_NAME</span></span>|<span data-ttu-id="0b762-231">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-231">String</span></span>|  
|<span data-ttu-id="0b762-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0b762-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="0b762-233">Int32</span><span class="sxs-lookup"><span data-stu-id="0b762-233">Int32</span></span>|  
|<span data-ttu-id="0b762-234">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="0b762-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="0b762-235">Int32</span><span class="sxs-lookup"><span data-stu-id="0b762-235">Int32</span></span>|  
|<span data-ttu-id="0b762-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="0b762-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="0b762-237">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="0b762-237">Boolean</span></span>|  
|<span data-ttu-id="0b762-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="0b762-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="0b762-239">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-239">String</span></span>|  
|<span data-ttu-id="0b762-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0b762-240">IS_NULLABLE</span></span>|<span data-ttu-id="0b762-241">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="0b762-241">Boolean</span></span>|  
|<span data-ttu-id="0b762-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0b762-242">DATA_TYPE</span></span>|<span data-ttu-id="0b762-243">Int32</span><span class="sxs-lookup"><span data-stu-id="0b762-243">Int32</span></span>|  
|<span data-ttu-id="0b762-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0b762-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="0b762-245">Int64</span><span class="sxs-lookup"><span data-stu-id="0b762-245">Int64</span></span>|  
|<span data-ttu-id="0b762-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0b762-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="0b762-247">Int64</span><span class="sxs-lookup"><span data-stu-id="0b762-247">Int64</span></span>|  
|<span data-ttu-id="0b762-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="0b762-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="0b762-249">Int32</span><span class="sxs-lookup"><span data-stu-id="0b762-249">Int32</span></span>|  
|<span data-ttu-id="0b762-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="0b762-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="0b762-251">Int16</span><span class="sxs-lookup"><span data-stu-id="0b762-251">Int16</span></span>|  
|<span data-ttu-id="0b762-252">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="0b762-252">DESCRIPTION</span></span>|<span data-ttu-id="0b762-253">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-253">String</span></span>|  
|<span data-ttu-id="0b762-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="0b762-254">TYPE_NAME</span></span>|<span data-ttu-id="0b762-255">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-255">String</span></span>|  
|<span data-ttu-id="0b762-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="0b762-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="0b762-257">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="0b762-258">Katalog</span><span class="sxs-lookup"><span data-stu-id="0b762-258">Catalog</span></span>  
  
|<span data-ttu-id="0b762-259">columnName</span><span class="sxs-lookup"><span data-stu-id="0b762-259">ColumnName</span></span>|<span data-ttu-id="0b762-260">Veri türü</span><span class="sxs-lookup"><span data-stu-id="0b762-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0b762-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="0b762-261">CATALOG_NAME</span></span>|<span data-ttu-id="0b762-262">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-262">String</span></span>|  
|<span data-ttu-id="0b762-263">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="0b762-263">DESCRIPTION</span></span>|<span data-ttu-id="0b762-264">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="0b762-265">Dizinler</span><span class="sxs-lookup"><span data-stu-id="0b762-265">Indexes</span></span>  
  
|<span data-ttu-id="0b762-266">columnName</span><span class="sxs-lookup"><span data-stu-id="0b762-266">ColumnName</span></span>|<span data-ttu-id="0b762-267">Veri türü</span><span class="sxs-lookup"><span data-stu-id="0b762-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0b762-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b762-268">TABLE_CATALOG</span></span>|<span data-ttu-id="0b762-269">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-269">String</span></span>|  
|<span data-ttu-id="0b762-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b762-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="0b762-271">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-271">String</span></span>|  
|<span data-ttu-id="0b762-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0b762-272">TABLE_NAME</span></span>|<span data-ttu-id="0b762-273">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-273">String</span></span>|  
|<span data-ttu-id="0b762-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b762-274">INDEX_CATALOG</span></span>|<span data-ttu-id="0b762-275">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-275">String</span></span>|  
|<span data-ttu-id="0b762-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b762-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="0b762-277">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-277">String</span></span>|  
|<span data-ttu-id="0b762-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="0b762-278">INDEX_NAME</span></span>|<span data-ttu-id="0b762-279">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-279">String</span></span>|  
|<span data-ttu-id="0b762-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="0b762-280">PRIMARY_KEY</span></span>|<span data-ttu-id="0b762-281">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="0b762-281">Boolean</span></span>|  
|<span data-ttu-id="0b762-282">BENZERSİZ</span><span class="sxs-lookup"><span data-stu-id="0b762-282">UNIQUE</span></span>|<span data-ttu-id="0b762-283">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="0b762-283">Boolean</span></span>|  
|<span data-ttu-id="0b762-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="0b762-284">CLUSTERED</span></span>|<span data-ttu-id="0b762-285">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="0b762-285">Boolean</span></span>|  
|<span data-ttu-id="0b762-286">TÜRÜ</span><span class="sxs-lookup"><span data-stu-id="0b762-286">TYPE</span></span>|<span data-ttu-id="0b762-287">Int32</span><span class="sxs-lookup"><span data-stu-id="0b762-287">Int32</span></span>|  
|<span data-ttu-id="0b762-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="0b762-288">FILL_FACTOR</span></span>|<span data-ttu-id="0b762-289">Int32</span><span class="sxs-lookup"><span data-stu-id="0b762-289">Int32</span></span>|  
|<span data-ttu-id="0b762-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="0b762-290">INITIAL_SIZE</span></span>|<span data-ttu-id="0b762-291">Int32</span><span class="sxs-lookup"><span data-stu-id="0b762-291">Int32</span></span>|  
|<span data-ttu-id="0b762-292">NULLS</span><span class="sxs-lookup"><span data-stu-id="0b762-292">NULLS</span></span>|<span data-ttu-id="0b762-293">Int32</span><span class="sxs-lookup"><span data-stu-id="0b762-293">Int32</span></span>|  
|<span data-ttu-id="0b762-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="0b762-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="0b762-295">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="0b762-295">Boolean</span></span>|  
|<span data-ttu-id="0b762-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="0b762-296">AUTO_UPDATE</span></span>|<span data-ttu-id="0b762-297">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="0b762-297">Boolean</span></span>|  
|<span data-ttu-id="0b762-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="0b762-298">NULL_COLLATION</span></span>|<span data-ttu-id="0b762-299">Int32</span><span class="sxs-lookup"><span data-stu-id="0b762-299">Int32</span></span>|  
|<span data-ttu-id="0b762-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0b762-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="0b762-301">Int64</span><span class="sxs-lookup"><span data-stu-id="0b762-301">Int64</span></span>|  
|<span data-ttu-id="0b762-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0b762-302">COLUMN_NAME</span></span>|<span data-ttu-id="0b762-303">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-303">String</span></span>|  
|<span data-ttu-id="0b762-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="0b762-304">COLUMN_GUID</span></span>|<span data-ttu-id="0b762-305">Guid</span><span class="sxs-lookup"><span data-stu-id="0b762-305">Guid</span></span>|  
|<span data-ttu-id="0b762-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="0b762-306">COLUMN_PROPID</span></span>|<span data-ttu-id="0b762-307">Int64</span><span class="sxs-lookup"><span data-stu-id="0b762-307">Int64</span></span>|  
|<span data-ttu-id="0b762-308">HARMANLAMA</span><span class="sxs-lookup"><span data-stu-id="0b762-308">COLLATION</span></span>|<span data-ttu-id="0b762-309">Int16</span><span class="sxs-lookup"><span data-stu-id="0b762-309">Int16</span></span>|  
|<span data-ttu-id="0b762-310">ÖNEM DÜZEYİ</span><span class="sxs-lookup"><span data-stu-id="0b762-310">CARDINALITY</span></span>|<span data-ttu-id="0b762-311">Ondalık</span><span class="sxs-lookup"><span data-stu-id="0b762-311">Decimal</span></span>|  
|<span data-ttu-id="0b762-312">SAYFALARI</span><span class="sxs-lookup"><span data-stu-id="0b762-312">PAGES</span></span>|<span data-ttu-id="0b762-313">Int32</span><span class="sxs-lookup"><span data-stu-id="0b762-313">Int32</span></span>|  
|<span data-ttu-id="0b762-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="0b762-314">FILTER_CONDITION</span></span>|<span data-ttu-id="0b762-315">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-315">String</span></span>|  
|<span data-ttu-id="0b762-316">TÜMLEŞİK</span><span class="sxs-lookup"><span data-stu-id="0b762-316">INTEGRATED</span></span>|<span data-ttu-id="0b762-317">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="0b762-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="0b762-318">Microsoft Oracle OLE DB sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="0b762-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="0b762-319">Microsoft Oracle OLE DB sürücü ortak şeması koleksiyonları ek olarak aşağıdaki belirli şeması koleksiyonları destekler:</span><span class="sxs-lookup"><span data-stu-id="0b762-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="0b762-320">tabloları</span><span class="sxs-lookup"><span data-stu-id="0b762-320">Tables</span></span>  
  
-   <span data-ttu-id="0b762-321">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="0b762-321">Columns</span></span>  
  
-   <span data-ttu-id="0b762-322">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="0b762-322">Procedures</span></span>  
  
-   <span data-ttu-id="0b762-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="0b762-323">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="0b762-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="0b762-324">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="0b762-325">Görünümler</span><span class="sxs-lookup"><span data-stu-id="0b762-325">Views</span></span>  
  
-   <span data-ttu-id="0b762-326">Dizinler</span><span class="sxs-lookup"><span data-stu-id="0b762-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="0b762-327">tabloları</span><span class="sxs-lookup"><span data-stu-id="0b762-327">Tables</span></span>  
  
|<span data-ttu-id="0b762-328">columnName</span><span class="sxs-lookup"><span data-stu-id="0b762-328">ColumnName</span></span>|<span data-ttu-id="0b762-329">Veri türü</span><span class="sxs-lookup"><span data-stu-id="0b762-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0b762-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b762-330">TABLE_CATALOG</span></span>|<span data-ttu-id="0b762-331">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-331">String</span></span>|  
|<span data-ttu-id="0b762-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b762-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="0b762-333">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-333">String</span></span>|  
|<span data-ttu-id="0b762-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0b762-334">TABLE_NAME</span></span>|<span data-ttu-id="0b762-335">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-335">String</span></span>|  
|<span data-ttu-id="0b762-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0b762-336">TABLE_TYPE</span></span>|<span data-ttu-id="0b762-337">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-337">String</span></span>|  
|<span data-ttu-id="0b762-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="0b762-338">TABLE_GUID</span></span>|<span data-ttu-id="0b762-339">Guid</span><span class="sxs-lookup"><span data-stu-id="0b762-339">Guid</span></span>|  
|<span data-ttu-id="0b762-340">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="0b762-340">DESCRIPTION</span></span>|<span data-ttu-id="0b762-341">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-341">String</span></span>|  
|<span data-ttu-id="0b762-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="0b762-342">TABLE_PROPID</span></span>|<span data-ttu-id="0b762-343">Int64</span><span class="sxs-lookup"><span data-stu-id="0b762-343">Int64</span></span>|  
|<span data-ttu-id="0b762-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="0b762-344">DATE_CREATED</span></span>|<span data-ttu-id="0b762-345">DateTime</span><span class="sxs-lookup"><span data-stu-id="0b762-345">DateTime</span></span>|  
|<span data-ttu-id="0b762-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="0b762-346">DATE_MODIFIED</span></span>|<span data-ttu-id="0b762-347">DateTime</span><span class="sxs-lookup"><span data-stu-id="0b762-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="0b762-348">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="0b762-348">Columns</span></span>  
  
|<span data-ttu-id="0b762-349">columnName</span><span class="sxs-lookup"><span data-stu-id="0b762-349">ColumnName</span></span>|<span data-ttu-id="0b762-350">Veri türü</span><span class="sxs-lookup"><span data-stu-id="0b762-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0b762-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b762-351">TABLE_CATALOG</span></span>|<span data-ttu-id="0b762-352">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-352">String</span></span>|  
|<span data-ttu-id="0b762-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b762-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="0b762-354">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-354">String</span></span>|  
|<span data-ttu-id="0b762-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0b762-355">TABLE_NAME</span></span>|<span data-ttu-id="0b762-356">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-356">String</span></span>|  
|<span data-ttu-id="0b762-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0b762-357">COLUMN_NAME</span></span>|<span data-ttu-id="0b762-358">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-358">String</span></span>|  
|<span data-ttu-id="0b762-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="0b762-359">COLUMN_GUID</span></span>|<span data-ttu-id="0b762-360">Guid</span><span class="sxs-lookup"><span data-stu-id="0b762-360">Guid</span></span>|  
|<span data-ttu-id="0b762-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="0b762-361">COLUMN_PROPID</span></span>|<span data-ttu-id="0b762-362">Int64</span><span class="sxs-lookup"><span data-stu-id="0b762-362">Int64</span></span>|  
|<span data-ttu-id="0b762-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0b762-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="0b762-364">Int64</span><span class="sxs-lookup"><span data-stu-id="0b762-364">Int64</span></span>|  
|<span data-ttu-id="0b762-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="0b762-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="0b762-366">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="0b762-366">Boolean</span></span>|  
|<span data-ttu-id="0b762-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="0b762-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="0b762-368">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-368">String</span></span>|  
|<span data-ttu-id="0b762-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="0b762-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="0b762-370">Int64</span><span class="sxs-lookup"><span data-stu-id="0b762-370">Int64</span></span>|  
|<span data-ttu-id="0b762-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0b762-371">IS_NULLABLE</span></span>|<span data-ttu-id="0b762-372">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="0b762-372">Boolean</span></span>|  
|<span data-ttu-id="0b762-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0b762-373">DATA_TYPE</span></span>|<span data-ttu-id="0b762-374">Int32</span><span class="sxs-lookup"><span data-stu-id="0b762-374">Int32</span></span>|  
|<span data-ttu-id="0b762-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="0b762-375">TYPE_GUID</span></span>|<span data-ttu-id="0b762-376">Guid</span><span class="sxs-lookup"><span data-stu-id="0b762-376">Guid</span></span>|  
|<span data-ttu-id="0b762-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0b762-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="0b762-378">Int64</span><span class="sxs-lookup"><span data-stu-id="0b762-378">Int64</span></span>|  
|<span data-ttu-id="0b762-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0b762-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="0b762-380">Int64</span><span class="sxs-lookup"><span data-stu-id="0b762-380">Int64</span></span>|  
|<span data-ttu-id="0b762-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="0b762-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="0b762-382">Int32</span><span class="sxs-lookup"><span data-stu-id="0b762-382">Int32</span></span>|  
|<span data-ttu-id="0b762-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="0b762-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="0b762-384">Int16</span><span class="sxs-lookup"><span data-stu-id="0b762-384">Int16</span></span>|  
|<span data-ttu-id="0b762-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="0b762-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="0b762-386">Int64</span><span class="sxs-lookup"><span data-stu-id="0b762-386">Int64</span></span>|  
|<span data-ttu-id="0b762-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b762-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="0b762-388">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-388">String</span></span>|  
|<span data-ttu-id="0b762-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b762-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="0b762-390">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-390">String</span></span>|  
|<span data-ttu-id="0b762-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="0b762-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="0b762-392">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-392">String</span></span>|  
|<span data-ttu-id="0b762-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b762-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="0b762-394">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-394">String</span></span>|  
|<span data-ttu-id="0b762-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b762-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="0b762-396">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-396">String</span></span>|  
|<span data-ttu-id="0b762-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="0b762-397">COLLATION_NAME</span></span>|<span data-ttu-id="0b762-398">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-398">String</span></span>|  
|<span data-ttu-id="0b762-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b762-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="0b762-400">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-400">String</span></span>|  
|<span data-ttu-id="0b762-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b762-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="0b762-402">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-402">String</span></span>|  
|<span data-ttu-id="0b762-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="0b762-403">DOMAIN_NAME</span></span>|<span data-ttu-id="0b762-404">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-404">String</span></span>|  
|<span data-ttu-id="0b762-405">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="0b762-405">DESCRIPTION</span></span>|<span data-ttu-id="0b762-406">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="0b762-407">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="0b762-407">Procedures</span></span>  
  
|<span data-ttu-id="0b762-408">columnName</span><span class="sxs-lookup"><span data-stu-id="0b762-408">ColumnName</span></span>|<span data-ttu-id="0b762-409">Veri türü</span><span class="sxs-lookup"><span data-stu-id="0b762-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0b762-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b762-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="0b762-411">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-411">String</span></span>|  
|<span data-ttu-id="0b762-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b762-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="0b762-413">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-413">String</span></span>|  
|<span data-ttu-id="0b762-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0b762-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="0b762-415">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-415">String</span></span>|  
|<span data-ttu-id="0b762-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0b762-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="0b762-417">Int16</span><span class="sxs-lookup"><span data-stu-id="0b762-417">Int16</span></span>|  
|<span data-ttu-id="0b762-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="0b762-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="0b762-419">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-419">String</span></span>|  
|<span data-ttu-id="0b762-420">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="0b762-420">DESCRIPTION</span></span>|<span data-ttu-id="0b762-421">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-421">String</span></span>|  
|<span data-ttu-id="0b762-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="0b762-422">DATE_CREATED</span></span>|<span data-ttu-id="0b762-423">DateTime</span><span class="sxs-lookup"><span data-stu-id="0b762-423">DateTime</span></span>|  
|<span data-ttu-id="0b762-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="0b762-424">DATE_MODIFIED</span></span>|<span data-ttu-id="0b762-425">DateTime</span><span class="sxs-lookup"><span data-stu-id="0b762-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="0b762-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="0b762-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="0b762-427">columnName</span><span class="sxs-lookup"><span data-stu-id="0b762-427">ColumnName</span></span>|<span data-ttu-id="0b762-428">Veri türü</span><span class="sxs-lookup"><span data-stu-id="0b762-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0b762-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b762-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="0b762-430">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-430">String</span></span>|  
|<span data-ttu-id="0b762-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b762-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="0b762-432">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-432">String</span></span>|  
|<span data-ttu-id="0b762-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0b762-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="0b762-434">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-434">String</span></span>|  
|<span data-ttu-id="0b762-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0b762-435">COLUMN_NAME</span></span>|<span data-ttu-id="0b762-436">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-436">String</span></span>|  
|<span data-ttu-id="0b762-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="0b762-437">COLUMN_GUID</span></span>|<span data-ttu-id="0b762-438">Guid</span><span class="sxs-lookup"><span data-stu-id="0b762-438">Guid</span></span>|  
|<span data-ttu-id="0b762-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="0b762-439">COLUMN_PROPID</span></span>|<span data-ttu-id="0b762-440">Int64</span><span class="sxs-lookup"><span data-stu-id="0b762-440">Int64</span></span>|  
|<span data-ttu-id="0b762-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="0b762-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="0b762-442">Int64</span><span class="sxs-lookup"><span data-stu-id="0b762-442">Int64</span></span>|  
|<span data-ttu-id="0b762-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0b762-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="0b762-444">Int64</span><span class="sxs-lookup"><span data-stu-id="0b762-444">Int64</span></span>|  
|<span data-ttu-id="0b762-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0b762-445">IS_NULLABLE</span></span>|<span data-ttu-id="0b762-446">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="0b762-446">Boolean</span></span>|  
|<span data-ttu-id="0b762-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0b762-447">DATA_TYPE</span></span>|<span data-ttu-id="0b762-448">Int32</span><span class="sxs-lookup"><span data-stu-id="0b762-448">Int32</span></span>|  
|<span data-ttu-id="0b762-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="0b762-449">TYPE_GUID</span></span>|<span data-ttu-id="0b762-450">Guid</span><span class="sxs-lookup"><span data-stu-id="0b762-450">Guid</span></span>|  
|<span data-ttu-id="0b762-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0b762-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="0b762-452">Int64</span><span class="sxs-lookup"><span data-stu-id="0b762-452">Int64</span></span>|  
|<span data-ttu-id="0b762-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0b762-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="0b762-454">Int64</span><span class="sxs-lookup"><span data-stu-id="0b762-454">Int64</span></span>|  
|<span data-ttu-id="0b762-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="0b762-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="0b762-456">Int32</span><span class="sxs-lookup"><span data-stu-id="0b762-456">Int32</span></span>|  
|<span data-ttu-id="0b762-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="0b762-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="0b762-458">Int16</span><span class="sxs-lookup"><span data-stu-id="0b762-458">Int16</span></span>|  
|<span data-ttu-id="0b762-459">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="0b762-459">DESCRIPTION</span></span>|<span data-ttu-id="0b762-460">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-460">String</span></span>|  
|<span data-ttu-id="0b762-461">AŞIRI YÜKLEME</span><span class="sxs-lookup"><span data-stu-id="0b762-461">OVERLOAD</span></span>|<span data-ttu-id="0b762-462">Int16</span><span class="sxs-lookup"><span data-stu-id="0b762-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="0b762-463">Görünümler</span><span class="sxs-lookup"><span data-stu-id="0b762-463">Views</span></span>  
  
|<span data-ttu-id="0b762-464">columnName</span><span class="sxs-lookup"><span data-stu-id="0b762-464">ColumnName</span></span>|<span data-ttu-id="0b762-465">Veri türü</span><span class="sxs-lookup"><span data-stu-id="0b762-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0b762-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b762-466">TABLE_CATALOG</span></span>|<span data-ttu-id="0b762-467">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-467">String</span></span>|  
|<span data-ttu-id="0b762-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b762-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="0b762-469">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-469">String</span></span>|  
|<span data-ttu-id="0b762-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0b762-470">TABLE_NAME</span></span>|<span data-ttu-id="0b762-471">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-471">String</span></span>|  
|<span data-ttu-id="0b762-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="0b762-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="0b762-473">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-473">String</span></span>|  
|<span data-ttu-id="0b762-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="0b762-474">CHECK_OPTION</span></span>|<span data-ttu-id="0b762-475">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="0b762-475">Boolean</span></span>|  
|<span data-ttu-id="0b762-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="0b762-476">IS_UPDATABLE</span></span>|<span data-ttu-id="0b762-477">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="0b762-477">Boolean</span></span>|  
|<span data-ttu-id="0b762-478">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="0b762-478">DESCRIPTION</span></span>|<span data-ttu-id="0b762-479">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-479">String</span></span>|  
|<span data-ttu-id="0b762-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="0b762-480">DATE_CREATED</span></span>|<span data-ttu-id="0b762-481">DateTime</span><span class="sxs-lookup"><span data-stu-id="0b762-481">DateTime</span></span>|  
|<span data-ttu-id="0b762-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="0b762-482">DATE_MODIFIED</span></span>|<span data-ttu-id="0b762-483">DateTime</span><span class="sxs-lookup"><span data-stu-id="0b762-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="0b762-484">Dizinler</span><span class="sxs-lookup"><span data-stu-id="0b762-484">Indexes</span></span>  
  
|<span data-ttu-id="0b762-485">columnName</span><span class="sxs-lookup"><span data-stu-id="0b762-485">ColumnName</span></span>|<span data-ttu-id="0b762-486">Veri türü</span><span class="sxs-lookup"><span data-stu-id="0b762-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0b762-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b762-487">TABLE_CATALOG</span></span>|<span data-ttu-id="0b762-488">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-488">String</span></span>|  
|<span data-ttu-id="0b762-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b762-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="0b762-490">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-490">String</span></span>|  
|<span data-ttu-id="0b762-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0b762-491">TABLE_NAME</span></span>|<span data-ttu-id="0b762-492">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-492">String</span></span>|  
|<span data-ttu-id="0b762-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b762-493">INDEX_CATALOG</span></span>|<span data-ttu-id="0b762-494">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-494">String</span></span>|  
|<span data-ttu-id="0b762-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b762-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="0b762-496">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-496">String</span></span>|  
|<span data-ttu-id="0b762-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="0b762-497">INDEX_NAME</span></span>|<span data-ttu-id="0b762-498">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-498">String</span></span>|  
|<span data-ttu-id="0b762-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="0b762-499">PRIMARY_KEY</span></span>|<span data-ttu-id="0b762-500">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="0b762-500">Boolean</span></span>|  
|<span data-ttu-id="0b762-501">BENZERSİZ</span><span class="sxs-lookup"><span data-stu-id="0b762-501">UNIQUE</span></span>|<span data-ttu-id="0b762-502">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="0b762-502">Boolean</span></span>|  
|<span data-ttu-id="0b762-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="0b762-503">CLUSTERED</span></span>|<span data-ttu-id="0b762-504">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="0b762-504">Boolean</span></span>|  
|<span data-ttu-id="0b762-505">TÜRÜ</span><span class="sxs-lookup"><span data-stu-id="0b762-505">TYPE</span></span>|<span data-ttu-id="0b762-506">Int32</span><span class="sxs-lookup"><span data-stu-id="0b762-506">Int32</span></span>|  
|<span data-ttu-id="0b762-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="0b762-507">FILL_FACTOR</span></span>|<span data-ttu-id="0b762-508">Int32</span><span class="sxs-lookup"><span data-stu-id="0b762-508">Int32</span></span>|  
|<span data-ttu-id="0b762-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="0b762-509">INITIAL_SIZE</span></span>|<span data-ttu-id="0b762-510">Int32</span><span class="sxs-lookup"><span data-stu-id="0b762-510">Int32</span></span>|  
|<span data-ttu-id="0b762-511">NULLS</span><span class="sxs-lookup"><span data-stu-id="0b762-511">NULLS</span></span>|<span data-ttu-id="0b762-512">Int32</span><span class="sxs-lookup"><span data-stu-id="0b762-512">Int32</span></span>|  
|<span data-ttu-id="0b762-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="0b762-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="0b762-514">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="0b762-514">Boolean</span></span>|  
|<span data-ttu-id="0b762-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="0b762-515">AUTO_UPDATE</span></span>|<span data-ttu-id="0b762-516">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="0b762-516">Boolean</span></span>|  
|<span data-ttu-id="0b762-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="0b762-517">NULL_COLLATION</span></span>|<span data-ttu-id="0b762-518">Int32</span><span class="sxs-lookup"><span data-stu-id="0b762-518">Int32</span></span>|  
|<span data-ttu-id="0b762-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0b762-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="0b762-520">Int64</span><span class="sxs-lookup"><span data-stu-id="0b762-520">Int64</span></span>|  
|<span data-ttu-id="0b762-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0b762-521">COLUMN_NAME</span></span>|<span data-ttu-id="0b762-522">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-522">String</span></span>|  
|<span data-ttu-id="0b762-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="0b762-523">COLUMN_GUID</span></span>|<span data-ttu-id="0b762-524">Guid</span><span class="sxs-lookup"><span data-stu-id="0b762-524">Guid</span></span>|  
|<span data-ttu-id="0b762-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="0b762-525">COLUMN_PROPID</span></span>|<span data-ttu-id="0b762-526">Int64</span><span class="sxs-lookup"><span data-stu-id="0b762-526">Int64</span></span>|  
|<span data-ttu-id="0b762-527">HARMANLAMA</span><span class="sxs-lookup"><span data-stu-id="0b762-527">COLLATION</span></span>|<span data-ttu-id="0b762-528">Int16</span><span class="sxs-lookup"><span data-stu-id="0b762-528">Int16</span></span>|  
|<span data-ttu-id="0b762-529">ÖNEM DÜZEYİ</span><span class="sxs-lookup"><span data-stu-id="0b762-529">CARDINALITY</span></span>|<span data-ttu-id="0b762-530">Ondalık</span><span class="sxs-lookup"><span data-stu-id="0b762-530">Decimal</span></span>|  
|<span data-ttu-id="0b762-531">SAYFALARI</span><span class="sxs-lookup"><span data-stu-id="0b762-531">PAGES</span></span>|<span data-ttu-id="0b762-532">Int32</span><span class="sxs-lookup"><span data-stu-id="0b762-532">Int32</span></span>|  
|<span data-ttu-id="0b762-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="0b762-533">FILTER_CONDITION</span></span>|<span data-ttu-id="0b762-534">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-534">String</span></span>|  
|<span data-ttu-id="0b762-535">TÜMLEŞİK</span><span class="sxs-lookup"><span data-stu-id="0b762-535">INTEGRATED</span></span>|<span data-ttu-id="0b762-536">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="0b762-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="0b762-537">Microsoft Jet OLE DB sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="0b762-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="0b762-538">Microsoft Jet OLE DB sürücü ortak şeması koleksiyonları ek olarak aşağıdaki belirli şeması koleksiyonları destekler:</span><span class="sxs-lookup"><span data-stu-id="0b762-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="0b762-539">tabloları</span><span class="sxs-lookup"><span data-stu-id="0b762-539">Tables</span></span>  
  
-   <span data-ttu-id="0b762-540">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="0b762-540">Columns</span></span>  
  
-   <span data-ttu-id="0b762-541">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="0b762-541">Procedures</span></span>  
  
-   <span data-ttu-id="0b762-542">Görünümler</span><span class="sxs-lookup"><span data-stu-id="0b762-542">Views</span></span>  
  
-   <span data-ttu-id="0b762-543">Dizinler</span><span class="sxs-lookup"><span data-stu-id="0b762-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="0b762-544">tabloları</span><span class="sxs-lookup"><span data-stu-id="0b762-544">Tables</span></span>  
  
|<span data-ttu-id="0b762-545">columnName</span><span class="sxs-lookup"><span data-stu-id="0b762-545">ColumnName</span></span>|<span data-ttu-id="0b762-546">Veri türü</span><span class="sxs-lookup"><span data-stu-id="0b762-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0b762-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b762-547">TABLE_CATALOG</span></span>|<span data-ttu-id="0b762-548">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-548">String</span></span>|  
|<span data-ttu-id="0b762-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b762-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="0b762-550">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-550">String</span></span>|  
|<span data-ttu-id="0b762-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0b762-551">TABLE_NAME</span></span>|<span data-ttu-id="0b762-552">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-552">String</span></span>|  
|<span data-ttu-id="0b762-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0b762-553">TABLE_TYPE</span></span>|<span data-ttu-id="0b762-554">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-554">String</span></span>|  
|<span data-ttu-id="0b762-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="0b762-555">TABLE_GUID</span></span>|<span data-ttu-id="0b762-556">Guid</span><span class="sxs-lookup"><span data-stu-id="0b762-556">Guid</span></span>|  
|<span data-ttu-id="0b762-557">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="0b762-557">DESCRIPTION</span></span>|<span data-ttu-id="0b762-558">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-558">String</span></span>|  
|<span data-ttu-id="0b762-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="0b762-559">TABLE_PROPID</span></span>|<span data-ttu-id="0b762-560">Int64</span><span class="sxs-lookup"><span data-stu-id="0b762-560">Int64</span></span>|  
|<span data-ttu-id="0b762-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="0b762-561">DATE_CREATED</span></span>|<span data-ttu-id="0b762-562">DateTime</span><span class="sxs-lookup"><span data-stu-id="0b762-562">DateTime</span></span>|  
|<span data-ttu-id="0b762-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="0b762-563">DATE_MODIFIED</span></span>|<span data-ttu-id="0b762-564">DateTime</span><span class="sxs-lookup"><span data-stu-id="0b762-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="0b762-565">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="0b762-565">Columns</span></span>  
  
|<span data-ttu-id="0b762-566">columnName</span><span class="sxs-lookup"><span data-stu-id="0b762-566">ColumnName</span></span>|<span data-ttu-id="0b762-567">Veri türü</span><span class="sxs-lookup"><span data-stu-id="0b762-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0b762-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b762-568">TABLE_CATALOG</span></span>|<span data-ttu-id="0b762-569">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-569">String</span></span>|  
|<span data-ttu-id="0b762-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b762-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="0b762-571">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-571">String</span></span>|  
|<span data-ttu-id="0b762-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0b762-572">TABLE_NAME</span></span>|<span data-ttu-id="0b762-573">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-573">String</span></span>|  
|<span data-ttu-id="0b762-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0b762-574">COLUMN_NAME</span></span>|<span data-ttu-id="0b762-575">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-575">String</span></span>|  
|<span data-ttu-id="0b762-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="0b762-576">COLUMN_GUID</span></span>|<span data-ttu-id="0b762-577">Guid</span><span class="sxs-lookup"><span data-stu-id="0b762-577">Guid</span></span>|  
|<span data-ttu-id="0b762-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="0b762-578">COLUMN_PROPID</span></span>|<span data-ttu-id="0b762-579">Int64</span><span class="sxs-lookup"><span data-stu-id="0b762-579">Int64</span></span>|  
|<span data-ttu-id="0b762-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0b762-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="0b762-581">Int64</span><span class="sxs-lookup"><span data-stu-id="0b762-581">Int64</span></span>|  
|<span data-ttu-id="0b762-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="0b762-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="0b762-583">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="0b762-583">Boolean</span></span>|  
|<span data-ttu-id="0b762-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="0b762-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="0b762-585">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-585">String</span></span>|  
|<span data-ttu-id="0b762-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="0b762-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="0b762-587">Int64</span><span class="sxs-lookup"><span data-stu-id="0b762-587">Int64</span></span>|  
|<span data-ttu-id="0b762-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0b762-588">IS_NULLABLE</span></span>|<span data-ttu-id="0b762-589">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="0b762-589">Boolean</span></span>|  
|<span data-ttu-id="0b762-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0b762-590">DATA_TYPE</span></span>|<span data-ttu-id="0b762-591">Int32</span><span class="sxs-lookup"><span data-stu-id="0b762-591">Int32</span></span>|  
|<span data-ttu-id="0b762-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="0b762-592">TYPE_GUID</span></span>|<span data-ttu-id="0b762-593">Guid</span><span class="sxs-lookup"><span data-stu-id="0b762-593">Guid</span></span>|  
|<span data-ttu-id="0b762-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0b762-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="0b762-595">Int64</span><span class="sxs-lookup"><span data-stu-id="0b762-595">Int64</span></span>|  
|<span data-ttu-id="0b762-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0b762-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="0b762-597">Int64</span><span class="sxs-lookup"><span data-stu-id="0b762-597">Int64</span></span>|  
|<span data-ttu-id="0b762-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="0b762-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="0b762-599">Int32</span><span class="sxs-lookup"><span data-stu-id="0b762-599">Int32</span></span>|  
|<span data-ttu-id="0b762-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="0b762-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="0b762-601">Int16</span><span class="sxs-lookup"><span data-stu-id="0b762-601">Int16</span></span>|  
|<span data-ttu-id="0b762-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="0b762-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="0b762-603">Int64</span><span class="sxs-lookup"><span data-stu-id="0b762-603">Int64</span></span>|  
|<span data-ttu-id="0b762-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b762-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="0b762-605">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-605">String</span></span>|  
|<span data-ttu-id="0b762-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b762-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="0b762-607">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-607">String</span></span>|  
|<span data-ttu-id="0b762-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="0b762-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="0b762-609">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-609">String</span></span>|  
|<span data-ttu-id="0b762-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b762-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="0b762-611">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-611">String</span></span>|  
|<span data-ttu-id="0b762-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b762-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="0b762-613">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-613">String</span></span>|  
|<span data-ttu-id="0b762-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="0b762-614">COLLATION_NAME</span></span>|<span data-ttu-id="0b762-615">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-615">String</span></span>|  
|<span data-ttu-id="0b762-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b762-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="0b762-617">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-617">String</span></span>|  
|<span data-ttu-id="0b762-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b762-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="0b762-619">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-619">String</span></span>|  
|<span data-ttu-id="0b762-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="0b762-620">DOMAIN_NAME</span></span>|<span data-ttu-id="0b762-621">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-621">String</span></span>|  
|<span data-ttu-id="0b762-622">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="0b762-622">DESCRIPTION</span></span>|<span data-ttu-id="0b762-623">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="0b762-624">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="0b762-624">Procedures</span></span>  
  
|<span data-ttu-id="0b762-625">columnName</span><span class="sxs-lookup"><span data-stu-id="0b762-625">ColumnName</span></span>|<span data-ttu-id="0b762-626">Veri türü</span><span class="sxs-lookup"><span data-stu-id="0b762-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0b762-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b762-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="0b762-628">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-628">String</span></span>|  
|<span data-ttu-id="0b762-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b762-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="0b762-630">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-630">String</span></span>|  
|<span data-ttu-id="0b762-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0b762-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="0b762-632">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-632">String</span></span>|  
|<span data-ttu-id="0b762-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0b762-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="0b762-634">Int16</span><span class="sxs-lookup"><span data-stu-id="0b762-634">Int16</span></span>|  
|<span data-ttu-id="0b762-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="0b762-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="0b762-636">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-636">String</span></span>|  
|<span data-ttu-id="0b762-637">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="0b762-637">DESCRIPTION</span></span>|<span data-ttu-id="0b762-638">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-638">String</span></span>|  
|<span data-ttu-id="0b762-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="0b762-639">DATE_CREATED</span></span>|<span data-ttu-id="0b762-640">DateTime</span><span class="sxs-lookup"><span data-stu-id="0b762-640">DateTime</span></span>|  
|<span data-ttu-id="0b762-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="0b762-641">DATE_MODIFIED</span></span>|<span data-ttu-id="0b762-642">DateTime</span><span class="sxs-lookup"><span data-stu-id="0b762-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="0b762-643">Görünümler</span><span class="sxs-lookup"><span data-stu-id="0b762-643">Views</span></span>  
  
|<span data-ttu-id="0b762-644">columnName</span><span class="sxs-lookup"><span data-stu-id="0b762-644">ColumnName</span></span>|<span data-ttu-id="0b762-645">Veri türü</span><span class="sxs-lookup"><span data-stu-id="0b762-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0b762-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b762-646">TABLE_CATALOG</span></span>|<span data-ttu-id="0b762-647">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-647">String</span></span>|  
|<span data-ttu-id="0b762-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b762-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="0b762-649">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-649">String</span></span>|  
|<span data-ttu-id="0b762-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0b762-650">TABLE_NAME</span></span>|<span data-ttu-id="0b762-651">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-651">String</span></span>|  
|<span data-ttu-id="0b762-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="0b762-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="0b762-653">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-653">String</span></span>|  
|<span data-ttu-id="0b762-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="0b762-654">CHECK_OPTION</span></span>|<span data-ttu-id="0b762-655">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="0b762-655">Boolean</span></span>|  
|<span data-ttu-id="0b762-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="0b762-656">IS_UPDATABLE</span></span>|<span data-ttu-id="0b762-657">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="0b762-657">Boolean</span></span>|  
|<span data-ttu-id="0b762-658">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="0b762-658">DESCRIPTION</span></span>|<span data-ttu-id="0b762-659">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-659">String</span></span>|  
|<span data-ttu-id="0b762-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="0b762-660">DATE_CREATED</span></span>|<span data-ttu-id="0b762-661">DateTime</span><span class="sxs-lookup"><span data-stu-id="0b762-661">DateTime</span></span>|  
|<span data-ttu-id="0b762-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="0b762-662">DATE_MODIFIED</span></span>|<span data-ttu-id="0b762-663">DateTime</span><span class="sxs-lookup"><span data-stu-id="0b762-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="0b762-664">Dizinler</span><span class="sxs-lookup"><span data-stu-id="0b762-664">Indexes</span></span>  
  
|<span data-ttu-id="0b762-665">columnName</span><span class="sxs-lookup"><span data-stu-id="0b762-665">ColumnName</span></span>|<span data-ttu-id="0b762-666">Veri türü</span><span class="sxs-lookup"><span data-stu-id="0b762-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0b762-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b762-667">TABLE_CATALOG</span></span>|<span data-ttu-id="0b762-668">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-668">String</span></span>|  
|<span data-ttu-id="0b762-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b762-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="0b762-670">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-670">String</span></span>|  
|<span data-ttu-id="0b762-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0b762-671">TABLE_NAME</span></span>|<span data-ttu-id="0b762-672">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-672">String</span></span>|  
|<span data-ttu-id="0b762-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b762-673">INDEX_CATALOG</span></span>|<span data-ttu-id="0b762-674">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-674">String</span></span>|  
|<span data-ttu-id="0b762-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b762-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="0b762-676">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-676">String</span></span>|  
|<span data-ttu-id="0b762-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="0b762-677">INDEX_NAME</span></span>|<span data-ttu-id="0b762-678">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-678">String</span></span>|  
|<span data-ttu-id="0b762-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="0b762-679">PRIMARY_KEY</span></span>|<span data-ttu-id="0b762-680">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="0b762-680">Boolean</span></span>|  
|<span data-ttu-id="0b762-681">BENZERSİZ</span><span class="sxs-lookup"><span data-stu-id="0b762-681">UNIQUE</span></span>|<span data-ttu-id="0b762-682">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="0b762-682">Boolean</span></span>|  
|<span data-ttu-id="0b762-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="0b762-683">CLUSTERED</span></span>|<span data-ttu-id="0b762-684">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="0b762-684">Boolean</span></span>|  
|<span data-ttu-id="0b762-685">TÜRÜ</span><span class="sxs-lookup"><span data-stu-id="0b762-685">TYPE</span></span>|<span data-ttu-id="0b762-686">Int32</span><span class="sxs-lookup"><span data-stu-id="0b762-686">Int32</span></span>|  
|<span data-ttu-id="0b762-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="0b762-687">FILL_FACTOR</span></span>|<span data-ttu-id="0b762-688">Int32</span><span class="sxs-lookup"><span data-stu-id="0b762-688">Int32</span></span>|  
|<span data-ttu-id="0b762-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="0b762-689">INITIAL_SIZE</span></span>|<span data-ttu-id="0b762-690">Int32</span><span class="sxs-lookup"><span data-stu-id="0b762-690">Int32</span></span>|  
|<span data-ttu-id="0b762-691">NULLS</span><span class="sxs-lookup"><span data-stu-id="0b762-691">NULLS</span></span>|<span data-ttu-id="0b762-692">Int32</span><span class="sxs-lookup"><span data-stu-id="0b762-692">Int32</span></span>|  
|<span data-ttu-id="0b762-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="0b762-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="0b762-694">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="0b762-694">Boolean</span></span>|  
|<span data-ttu-id="0b762-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="0b762-695">AUTO_UPDATE</span></span>|<span data-ttu-id="0b762-696">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="0b762-696">Boolean</span></span>|  
|<span data-ttu-id="0b762-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="0b762-697">NULL_COLLATION</span></span>|<span data-ttu-id="0b762-698">Int32</span><span class="sxs-lookup"><span data-stu-id="0b762-698">Int32</span></span>|  
|<span data-ttu-id="0b762-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0b762-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="0b762-700">Int64</span><span class="sxs-lookup"><span data-stu-id="0b762-700">Int64</span></span>|  
|<span data-ttu-id="0b762-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0b762-701">COLUMN_NAME</span></span>|<span data-ttu-id="0b762-702">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-702">String</span></span>|  
|<span data-ttu-id="0b762-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="0b762-703">COLUMN_GUID</span></span>|<span data-ttu-id="0b762-704">Guid</span><span class="sxs-lookup"><span data-stu-id="0b762-704">Guid</span></span>|  
|<span data-ttu-id="0b762-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="0b762-705">COLUMN_PROPID</span></span>|<span data-ttu-id="0b762-706">Int64</span><span class="sxs-lookup"><span data-stu-id="0b762-706">Int64</span></span>|  
|<span data-ttu-id="0b762-707">HARMANLAMA</span><span class="sxs-lookup"><span data-stu-id="0b762-707">COLLATION</span></span>|<span data-ttu-id="0b762-708">Int16</span><span class="sxs-lookup"><span data-stu-id="0b762-708">Int16</span></span>|  
|<span data-ttu-id="0b762-709">ÖNEM DÜZEYİ</span><span class="sxs-lookup"><span data-stu-id="0b762-709">CARDINALITY</span></span>|<span data-ttu-id="0b762-710">Ondalık</span><span class="sxs-lookup"><span data-stu-id="0b762-710">Decimal</span></span>|  
|<span data-ttu-id="0b762-711">SAYFALARI</span><span class="sxs-lookup"><span data-stu-id="0b762-711">PAGES</span></span>|<span data-ttu-id="0b762-712">Int32</span><span class="sxs-lookup"><span data-stu-id="0b762-712">Int32</span></span>|  
|<span data-ttu-id="0b762-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="0b762-713">FILTER_CONDITION</span></span>|<span data-ttu-id="0b762-714">Dize</span><span class="sxs-lookup"><span data-stu-id="0b762-714">String</span></span>|  
|<span data-ttu-id="0b762-715">TÜMLEŞİK</span><span class="sxs-lookup"><span data-stu-id="0b762-715">INTEGRATED</span></span>|<span data-ttu-id="0b762-716">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="0b762-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0b762-717">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0b762-717">See Also</span></span>  
 [<span data-ttu-id="0b762-718">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="0b762-718">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
