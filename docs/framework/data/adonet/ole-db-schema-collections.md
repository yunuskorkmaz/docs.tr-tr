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
ms.openlocfilehash: 9b88308c5dad69ed1ba6f48f525931e94f13ef1a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="8aa3b-102">OLE DB şeması koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="8aa3b-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="8aa3b-103">Bu bölümde, Microsoft SQL Server, Oracle ve Microsoft Jet için OLE DB sağlayıcıları şema koleksiyonu desteği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8aa3b-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="8aa3b-104">Microsoft SQL Server OLE DB sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="8aa3b-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="8aa3b-105">Microsoft SQL Server OLE DB sürücüsü ortak şeması koleksiyonları ek olarak aşağıdaki belirli şeması koleksiyonları destekler:</span><span class="sxs-lookup"><span data-stu-id="8aa3b-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="8aa3b-106">tabloları</span><span class="sxs-lookup"><span data-stu-id="8aa3b-106">Tables</span></span>  
  
-   <span data-ttu-id="8aa3b-107">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="8aa3b-107">Columns</span></span>  
  
-   <span data-ttu-id="8aa3b-108">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="8aa3b-108">Procedures</span></span>  
  
-   <span data-ttu-id="8aa3b-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="8aa3b-109">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="8aa3b-110">Katalog</span><span class="sxs-lookup"><span data-stu-id="8aa3b-110">Catalog</span></span>  
  
-   <span data-ttu-id="8aa3b-111">Dizinler</span><span class="sxs-lookup"><span data-stu-id="8aa3b-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="8aa3b-112">tabloları</span><span class="sxs-lookup"><span data-stu-id="8aa3b-112">Tables</span></span>  
  
|<span data-ttu-id="8aa3b-113">columnName</span><span class="sxs-lookup"><span data-stu-id="8aa3b-113">ColumnName</span></span>|<span data-ttu-id="8aa3b-114">Veri türü</span><span class="sxs-lookup"><span data-stu-id="8aa3b-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8aa3b-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8aa3b-115">TABLE_CATALOG</span></span>|<span data-ttu-id="8aa3b-116">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-116">String</span></span>|  
|<span data-ttu-id="8aa3b-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8aa3b-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="8aa3b-118">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-118">String</span></span>|  
|<span data-ttu-id="8aa3b-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8aa3b-119">TABLE_NAME</span></span>|<span data-ttu-id="8aa3b-120">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-120">String</span></span>|  
|<span data-ttu-id="8aa3b-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="8aa3b-121">TABLE_TYPE</span></span>|<span data-ttu-id="8aa3b-122">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-122">String</span></span>|  
|<span data-ttu-id="8aa3b-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="8aa3b-123">TABLE_GUID</span></span>|<span data-ttu-id="8aa3b-124">Guid</span><span class="sxs-lookup"><span data-stu-id="8aa3b-124">Guid</span></span>|  
|<span data-ttu-id="8aa3b-125">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="8aa3b-125">DESCRIPTION</span></span>|<span data-ttu-id="8aa3b-126">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-126">String</span></span>|  
|<span data-ttu-id="8aa3b-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="8aa3b-127">TABLE_PROPID</span></span>|<span data-ttu-id="8aa3b-128">Int64</span><span class="sxs-lookup"><span data-stu-id="8aa3b-128">Int64</span></span>|  
|<span data-ttu-id="8aa3b-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="8aa3b-129">DATE_CREATED</span></span>|<span data-ttu-id="8aa3b-130">DateTime</span><span class="sxs-lookup"><span data-stu-id="8aa3b-130">DateTime</span></span>|  
|<span data-ttu-id="8aa3b-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="8aa3b-131">DATE_MODIFIED</span></span>|<span data-ttu-id="8aa3b-132">DateTime</span><span class="sxs-lookup"><span data-stu-id="8aa3b-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="8aa3b-133">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="8aa3b-133">Columns</span></span>  
  
|<span data-ttu-id="8aa3b-134">columnName</span><span class="sxs-lookup"><span data-stu-id="8aa3b-134">ColumnName</span></span>|<span data-ttu-id="8aa3b-135">Veri türü</span><span class="sxs-lookup"><span data-stu-id="8aa3b-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8aa3b-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8aa3b-136">TABLE_CATALOG</span></span>|<span data-ttu-id="8aa3b-137">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-137">String</span></span>|  
|<span data-ttu-id="8aa3b-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8aa3b-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="8aa3b-139">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-139">String</span></span>|  
|<span data-ttu-id="8aa3b-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8aa3b-140">TABLE_NAME</span></span>|<span data-ttu-id="8aa3b-141">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-141">String</span></span>|  
|<span data-ttu-id="8aa3b-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="8aa3b-142">COLUMN_NAME</span></span>|<span data-ttu-id="8aa3b-143">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-143">String</span></span>|  
|<span data-ttu-id="8aa3b-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="8aa3b-144">COLUMN_GUID</span></span>|<span data-ttu-id="8aa3b-145">Guid</span><span class="sxs-lookup"><span data-stu-id="8aa3b-145">Guid</span></span>|  
|<span data-ttu-id="8aa3b-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="8aa3b-146">COLUMN_PROPID</span></span>|<span data-ttu-id="8aa3b-147">Int64</span><span class="sxs-lookup"><span data-stu-id="8aa3b-147">Int64</span></span>|  
|<span data-ttu-id="8aa3b-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="8aa3b-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="8aa3b-149">Int64</span><span class="sxs-lookup"><span data-stu-id="8aa3b-149">Int64</span></span>|  
|<span data-ttu-id="8aa3b-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="8aa3b-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="8aa3b-151">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="8aa3b-151">Boolean</span></span>|  
|<span data-ttu-id="8aa3b-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="8aa3b-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="8aa3b-153">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-153">String</span></span>|  
|<span data-ttu-id="8aa3b-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="8aa3b-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="8aa3b-155">Int64</span><span class="sxs-lookup"><span data-stu-id="8aa3b-155">Int64</span></span>|  
|<span data-ttu-id="8aa3b-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="8aa3b-156">IS_NULLABLE</span></span>|<span data-ttu-id="8aa3b-157">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="8aa3b-157">Boolean</span></span>|  
|<span data-ttu-id="8aa3b-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="8aa3b-158">DATA_TYPE</span></span>|<span data-ttu-id="8aa3b-159">Int32</span><span class="sxs-lookup"><span data-stu-id="8aa3b-159">Int32</span></span>|  
|<span data-ttu-id="8aa3b-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="8aa3b-160">TYPE_GUID</span></span>|<span data-ttu-id="8aa3b-161">Guid</span><span class="sxs-lookup"><span data-stu-id="8aa3b-161">Guid</span></span>|  
|<span data-ttu-id="8aa3b-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="8aa3b-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="8aa3b-163">Int64</span><span class="sxs-lookup"><span data-stu-id="8aa3b-163">Int64</span></span>|  
|<span data-ttu-id="8aa3b-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="8aa3b-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="8aa3b-165">Int64</span><span class="sxs-lookup"><span data-stu-id="8aa3b-165">Int64</span></span>|  
|<span data-ttu-id="8aa3b-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="8aa3b-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="8aa3b-167">Int32</span><span class="sxs-lookup"><span data-stu-id="8aa3b-167">Int32</span></span>|  
|<span data-ttu-id="8aa3b-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="8aa3b-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="8aa3b-169">Int16</span><span class="sxs-lookup"><span data-stu-id="8aa3b-169">Int16</span></span>|  
|<span data-ttu-id="8aa3b-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="8aa3b-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="8aa3b-171">Int64</span><span class="sxs-lookup"><span data-stu-id="8aa3b-171">Int64</span></span>|  
|<span data-ttu-id="8aa3b-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8aa3b-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="8aa3b-173">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-173">String</span></span>|  
|<span data-ttu-id="8aa3b-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8aa3b-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="8aa3b-175">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-175">String</span></span>|  
|<span data-ttu-id="8aa3b-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="8aa3b-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="8aa3b-177">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-177">String</span></span>|  
|<span data-ttu-id="8aa3b-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8aa3b-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="8aa3b-179">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-179">String</span></span>|  
|<span data-ttu-id="8aa3b-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8aa3b-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="8aa3b-181">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-181">String</span></span>|  
|<span data-ttu-id="8aa3b-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="8aa3b-182">COLLATION_NAME</span></span>|<span data-ttu-id="8aa3b-183">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-183">String</span></span>|  
|<span data-ttu-id="8aa3b-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8aa3b-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="8aa3b-185">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-185">String</span></span>|  
|<span data-ttu-id="8aa3b-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8aa3b-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="8aa3b-187">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-187">String</span></span>|  
|<span data-ttu-id="8aa3b-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="8aa3b-188">DOMAIN_NAME</span></span>|<span data-ttu-id="8aa3b-189">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-189">String</span></span>|  
|<span data-ttu-id="8aa3b-190">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="8aa3b-190">DESCRIPTION</span></span>|<span data-ttu-id="8aa3b-191">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-191">String</span></span>|  
|<span data-ttu-id="8aa3b-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="8aa3b-192">COLUMN_LCID</span></span>|<span data-ttu-id="8aa3b-193">Int32</span><span class="sxs-lookup"><span data-stu-id="8aa3b-193">Int32</span></span>|  
|<span data-ttu-id="8aa3b-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="8aa3b-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="8aa3b-195">Int32</span><span class="sxs-lookup"><span data-stu-id="8aa3b-195">Int32</span></span>|  
|<span data-ttu-id="8aa3b-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="8aa3b-196">COLUMN_SORTID</span></span>|<span data-ttu-id="8aa3b-197">Int32</span><span class="sxs-lookup"><span data-stu-id="8aa3b-197">Int32</span></span>|  
|<span data-ttu-id="8aa3b-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="8aa3b-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="8aa3b-199">Byte]</span><span class="sxs-lookup"><span data-stu-id="8aa3b-199">Byte[]</span></span>|  
|<span data-ttu-id="8aa3b-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="8aa3b-200">IS_COMPUTED</span></span>|<span data-ttu-id="8aa3b-201">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="8aa3b-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="8aa3b-202">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="8aa3b-202">Procedures</span></span>  
  
|<span data-ttu-id="8aa3b-203">columnName</span><span class="sxs-lookup"><span data-stu-id="8aa3b-203">ColumnName</span></span>|<span data-ttu-id="8aa3b-204">Veri türü</span><span class="sxs-lookup"><span data-stu-id="8aa3b-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8aa3b-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8aa3b-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="8aa3b-206">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-206">String</span></span>|  
|<span data-ttu-id="8aa3b-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8aa3b-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="8aa3b-208">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-208">String</span></span>|  
|<span data-ttu-id="8aa3b-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="8aa3b-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="8aa3b-210">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-210">String</span></span>|  
|<span data-ttu-id="8aa3b-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="8aa3b-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="8aa3b-212">Int16</span><span class="sxs-lookup"><span data-stu-id="8aa3b-212">Int16</span></span>|  
|<span data-ttu-id="8aa3b-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="8aa3b-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="8aa3b-214">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-214">String</span></span>|  
|<span data-ttu-id="8aa3b-215">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="8aa3b-215">DESCRIPTION</span></span>|<span data-ttu-id="8aa3b-216">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-216">String</span></span>|  
|<span data-ttu-id="8aa3b-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="8aa3b-217">DATE_CREATED</span></span>|<span data-ttu-id="8aa3b-218">DateTime</span><span class="sxs-lookup"><span data-stu-id="8aa3b-218">DateTime</span></span>|  
|<span data-ttu-id="8aa3b-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="8aa3b-219">DATE_MODIFIED</span></span>|<span data-ttu-id="8aa3b-220">DateTime</span><span class="sxs-lookup"><span data-stu-id="8aa3b-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="8aa3b-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="8aa3b-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="8aa3b-222">columnName</span><span class="sxs-lookup"><span data-stu-id="8aa3b-222">ColumnName</span></span>|<span data-ttu-id="8aa3b-223">Veri türü</span><span class="sxs-lookup"><span data-stu-id="8aa3b-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8aa3b-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8aa3b-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="8aa3b-225">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-225">String</span></span>|  
|<span data-ttu-id="8aa3b-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8aa3b-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="8aa3b-227">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-227">String</span></span>|  
|<span data-ttu-id="8aa3b-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="8aa3b-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="8aa3b-229">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-229">String</span></span>|  
|<span data-ttu-id="8aa3b-230">PARAMETRE_ADÝ</span><span class="sxs-lookup"><span data-stu-id="8aa3b-230">PARAMETER_NAME</span></span>|<span data-ttu-id="8aa3b-231">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-231">String</span></span>|  
|<span data-ttu-id="8aa3b-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="8aa3b-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="8aa3b-233">Int32</span><span class="sxs-lookup"><span data-stu-id="8aa3b-233">Int32</span></span>|  
|<span data-ttu-id="8aa3b-234">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="8aa3b-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="8aa3b-235">Int32</span><span class="sxs-lookup"><span data-stu-id="8aa3b-235">Int32</span></span>|  
|<span data-ttu-id="8aa3b-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="8aa3b-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="8aa3b-237">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="8aa3b-237">Boolean</span></span>|  
|<span data-ttu-id="8aa3b-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="8aa3b-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="8aa3b-239">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-239">String</span></span>|  
|<span data-ttu-id="8aa3b-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="8aa3b-240">IS_NULLABLE</span></span>|<span data-ttu-id="8aa3b-241">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="8aa3b-241">Boolean</span></span>|  
|<span data-ttu-id="8aa3b-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="8aa3b-242">DATA_TYPE</span></span>|<span data-ttu-id="8aa3b-243">Int32</span><span class="sxs-lookup"><span data-stu-id="8aa3b-243">Int32</span></span>|  
|<span data-ttu-id="8aa3b-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="8aa3b-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="8aa3b-245">Int64</span><span class="sxs-lookup"><span data-stu-id="8aa3b-245">Int64</span></span>|  
|<span data-ttu-id="8aa3b-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="8aa3b-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="8aa3b-247">Int64</span><span class="sxs-lookup"><span data-stu-id="8aa3b-247">Int64</span></span>|  
|<span data-ttu-id="8aa3b-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="8aa3b-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="8aa3b-249">Int32</span><span class="sxs-lookup"><span data-stu-id="8aa3b-249">Int32</span></span>|  
|<span data-ttu-id="8aa3b-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="8aa3b-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="8aa3b-251">Int16</span><span class="sxs-lookup"><span data-stu-id="8aa3b-251">Int16</span></span>|  
|<span data-ttu-id="8aa3b-252">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="8aa3b-252">DESCRIPTION</span></span>|<span data-ttu-id="8aa3b-253">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-253">String</span></span>|  
|<span data-ttu-id="8aa3b-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="8aa3b-254">TYPE_NAME</span></span>|<span data-ttu-id="8aa3b-255">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-255">String</span></span>|  
|<span data-ttu-id="8aa3b-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="8aa3b-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="8aa3b-257">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="8aa3b-258">Katalog</span><span class="sxs-lookup"><span data-stu-id="8aa3b-258">Catalog</span></span>  
  
|<span data-ttu-id="8aa3b-259">columnName</span><span class="sxs-lookup"><span data-stu-id="8aa3b-259">ColumnName</span></span>|<span data-ttu-id="8aa3b-260">Veri türü</span><span class="sxs-lookup"><span data-stu-id="8aa3b-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8aa3b-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="8aa3b-261">CATALOG_NAME</span></span>|<span data-ttu-id="8aa3b-262">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-262">String</span></span>|  
|<span data-ttu-id="8aa3b-263">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="8aa3b-263">DESCRIPTION</span></span>|<span data-ttu-id="8aa3b-264">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="8aa3b-265">Dizinler</span><span class="sxs-lookup"><span data-stu-id="8aa3b-265">Indexes</span></span>  
  
|<span data-ttu-id="8aa3b-266">columnName</span><span class="sxs-lookup"><span data-stu-id="8aa3b-266">ColumnName</span></span>|<span data-ttu-id="8aa3b-267">Veri türü</span><span class="sxs-lookup"><span data-stu-id="8aa3b-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8aa3b-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8aa3b-268">TABLE_CATALOG</span></span>|<span data-ttu-id="8aa3b-269">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-269">String</span></span>|  
|<span data-ttu-id="8aa3b-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8aa3b-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="8aa3b-271">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-271">String</span></span>|  
|<span data-ttu-id="8aa3b-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8aa3b-272">TABLE_NAME</span></span>|<span data-ttu-id="8aa3b-273">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-273">String</span></span>|  
|<span data-ttu-id="8aa3b-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8aa3b-274">INDEX_CATALOG</span></span>|<span data-ttu-id="8aa3b-275">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-275">String</span></span>|  
|<span data-ttu-id="8aa3b-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8aa3b-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="8aa3b-277">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-277">String</span></span>|  
|<span data-ttu-id="8aa3b-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="8aa3b-278">INDEX_NAME</span></span>|<span data-ttu-id="8aa3b-279">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-279">String</span></span>|  
|<span data-ttu-id="8aa3b-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="8aa3b-280">PRIMARY_KEY</span></span>|<span data-ttu-id="8aa3b-281">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="8aa3b-281">Boolean</span></span>|  
|<span data-ttu-id="8aa3b-282">BENZERSİZ</span><span class="sxs-lookup"><span data-stu-id="8aa3b-282">UNIQUE</span></span>|<span data-ttu-id="8aa3b-283">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="8aa3b-283">Boolean</span></span>|  
|<span data-ttu-id="8aa3b-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="8aa3b-284">CLUSTERED</span></span>|<span data-ttu-id="8aa3b-285">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="8aa3b-285">Boolean</span></span>|  
|<span data-ttu-id="8aa3b-286">TÜRÜ</span><span class="sxs-lookup"><span data-stu-id="8aa3b-286">TYPE</span></span>|<span data-ttu-id="8aa3b-287">Int32</span><span class="sxs-lookup"><span data-stu-id="8aa3b-287">Int32</span></span>|  
|<span data-ttu-id="8aa3b-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="8aa3b-288">FILL_FACTOR</span></span>|<span data-ttu-id="8aa3b-289">Int32</span><span class="sxs-lookup"><span data-stu-id="8aa3b-289">Int32</span></span>|  
|<span data-ttu-id="8aa3b-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="8aa3b-290">INITIAL_SIZE</span></span>|<span data-ttu-id="8aa3b-291">Int32</span><span class="sxs-lookup"><span data-stu-id="8aa3b-291">Int32</span></span>|  
|<span data-ttu-id="8aa3b-292">NULLS</span><span class="sxs-lookup"><span data-stu-id="8aa3b-292">NULLS</span></span>|<span data-ttu-id="8aa3b-293">Int32</span><span class="sxs-lookup"><span data-stu-id="8aa3b-293">Int32</span></span>|  
|<span data-ttu-id="8aa3b-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="8aa3b-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="8aa3b-295">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="8aa3b-295">Boolean</span></span>|  
|<span data-ttu-id="8aa3b-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="8aa3b-296">AUTO_UPDATE</span></span>|<span data-ttu-id="8aa3b-297">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="8aa3b-297">Boolean</span></span>|  
|<span data-ttu-id="8aa3b-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="8aa3b-298">NULL_COLLATION</span></span>|<span data-ttu-id="8aa3b-299">Int32</span><span class="sxs-lookup"><span data-stu-id="8aa3b-299">Int32</span></span>|  
|<span data-ttu-id="8aa3b-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="8aa3b-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="8aa3b-301">Int64</span><span class="sxs-lookup"><span data-stu-id="8aa3b-301">Int64</span></span>|  
|<span data-ttu-id="8aa3b-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="8aa3b-302">COLUMN_NAME</span></span>|<span data-ttu-id="8aa3b-303">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-303">String</span></span>|  
|<span data-ttu-id="8aa3b-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="8aa3b-304">COLUMN_GUID</span></span>|<span data-ttu-id="8aa3b-305">Guid</span><span class="sxs-lookup"><span data-stu-id="8aa3b-305">Guid</span></span>|  
|<span data-ttu-id="8aa3b-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="8aa3b-306">COLUMN_PROPID</span></span>|<span data-ttu-id="8aa3b-307">Int64</span><span class="sxs-lookup"><span data-stu-id="8aa3b-307">Int64</span></span>|  
|<span data-ttu-id="8aa3b-308">HARMANLAMA</span><span class="sxs-lookup"><span data-stu-id="8aa3b-308">COLLATION</span></span>|<span data-ttu-id="8aa3b-309">Int16</span><span class="sxs-lookup"><span data-stu-id="8aa3b-309">Int16</span></span>|  
|<span data-ttu-id="8aa3b-310">ÖNEM DÜZEYİ</span><span class="sxs-lookup"><span data-stu-id="8aa3b-310">CARDINALITY</span></span>|<span data-ttu-id="8aa3b-311">Ondalık</span><span class="sxs-lookup"><span data-stu-id="8aa3b-311">Decimal</span></span>|  
|<span data-ttu-id="8aa3b-312">SAYFALARI</span><span class="sxs-lookup"><span data-stu-id="8aa3b-312">PAGES</span></span>|<span data-ttu-id="8aa3b-313">Int32</span><span class="sxs-lookup"><span data-stu-id="8aa3b-313">Int32</span></span>|  
|<span data-ttu-id="8aa3b-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="8aa3b-314">FILTER_CONDITION</span></span>|<span data-ttu-id="8aa3b-315">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-315">String</span></span>|  
|<span data-ttu-id="8aa3b-316">TÜMLEŞİK</span><span class="sxs-lookup"><span data-stu-id="8aa3b-316">INTEGRATED</span></span>|<span data-ttu-id="8aa3b-317">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="8aa3b-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="8aa3b-318">Microsoft Oracle OLE DB sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="8aa3b-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="8aa3b-319">Microsoft Oracle OLE DB sürücü ortak şeması koleksiyonları ek olarak aşağıdaki belirli şeması koleksiyonları destekler:</span><span class="sxs-lookup"><span data-stu-id="8aa3b-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="8aa3b-320">tabloları</span><span class="sxs-lookup"><span data-stu-id="8aa3b-320">Tables</span></span>  
  
-   <span data-ttu-id="8aa3b-321">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="8aa3b-321">Columns</span></span>  
  
-   <span data-ttu-id="8aa3b-322">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="8aa3b-322">Procedures</span></span>  
  
-   <span data-ttu-id="8aa3b-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="8aa3b-323">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="8aa3b-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="8aa3b-324">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="8aa3b-325">Görünümler</span><span class="sxs-lookup"><span data-stu-id="8aa3b-325">Views</span></span>  
  
-   <span data-ttu-id="8aa3b-326">Dizinler</span><span class="sxs-lookup"><span data-stu-id="8aa3b-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="8aa3b-327">tabloları</span><span class="sxs-lookup"><span data-stu-id="8aa3b-327">Tables</span></span>  
  
|<span data-ttu-id="8aa3b-328">columnName</span><span class="sxs-lookup"><span data-stu-id="8aa3b-328">ColumnName</span></span>|<span data-ttu-id="8aa3b-329">Veri türü</span><span class="sxs-lookup"><span data-stu-id="8aa3b-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8aa3b-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8aa3b-330">TABLE_CATALOG</span></span>|<span data-ttu-id="8aa3b-331">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-331">String</span></span>|  
|<span data-ttu-id="8aa3b-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8aa3b-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="8aa3b-333">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-333">String</span></span>|  
|<span data-ttu-id="8aa3b-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8aa3b-334">TABLE_NAME</span></span>|<span data-ttu-id="8aa3b-335">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-335">String</span></span>|  
|<span data-ttu-id="8aa3b-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="8aa3b-336">TABLE_TYPE</span></span>|<span data-ttu-id="8aa3b-337">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-337">String</span></span>|  
|<span data-ttu-id="8aa3b-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="8aa3b-338">TABLE_GUID</span></span>|<span data-ttu-id="8aa3b-339">Guid</span><span class="sxs-lookup"><span data-stu-id="8aa3b-339">Guid</span></span>|  
|<span data-ttu-id="8aa3b-340">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="8aa3b-340">DESCRIPTION</span></span>|<span data-ttu-id="8aa3b-341">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-341">String</span></span>|  
|<span data-ttu-id="8aa3b-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="8aa3b-342">TABLE_PROPID</span></span>|<span data-ttu-id="8aa3b-343">Int64</span><span class="sxs-lookup"><span data-stu-id="8aa3b-343">Int64</span></span>|  
|<span data-ttu-id="8aa3b-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="8aa3b-344">DATE_CREATED</span></span>|<span data-ttu-id="8aa3b-345">DateTime</span><span class="sxs-lookup"><span data-stu-id="8aa3b-345">DateTime</span></span>|  
|<span data-ttu-id="8aa3b-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="8aa3b-346">DATE_MODIFIED</span></span>|<span data-ttu-id="8aa3b-347">DateTime</span><span class="sxs-lookup"><span data-stu-id="8aa3b-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="8aa3b-348">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="8aa3b-348">Columns</span></span>  
  
|<span data-ttu-id="8aa3b-349">columnName</span><span class="sxs-lookup"><span data-stu-id="8aa3b-349">ColumnName</span></span>|<span data-ttu-id="8aa3b-350">Veri türü</span><span class="sxs-lookup"><span data-stu-id="8aa3b-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8aa3b-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8aa3b-351">TABLE_CATALOG</span></span>|<span data-ttu-id="8aa3b-352">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-352">String</span></span>|  
|<span data-ttu-id="8aa3b-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8aa3b-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="8aa3b-354">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-354">String</span></span>|  
|<span data-ttu-id="8aa3b-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8aa3b-355">TABLE_NAME</span></span>|<span data-ttu-id="8aa3b-356">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-356">String</span></span>|  
|<span data-ttu-id="8aa3b-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="8aa3b-357">COLUMN_NAME</span></span>|<span data-ttu-id="8aa3b-358">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-358">String</span></span>|  
|<span data-ttu-id="8aa3b-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="8aa3b-359">COLUMN_GUID</span></span>|<span data-ttu-id="8aa3b-360">Guid</span><span class="sxs-lookup"><span data-stu-id="8aa3b-360">Guid</span></span>|  
|<span data-ttu-id="8aa3b-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="8aa3b-361">COLUMN_PROPID</span></span>|<span data-ttu-id="8aa3b-362">Int64</span><span class="sxs-lookup"><span data-stu-id="8aa3b-362">Int64</span></span>|  
|<span data-ttu-id="8aa3b-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="8aa3b-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="8aa3b-364">Int64</span><span class="sxs-lookup"><span data-stu-id="8aa3b-364">Int64</span></span>|  
|<span data-ttu-id="8aa3b-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="8aa3b-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="8aa3b-366">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="8aa3b-366">Boolean</span></span>|  
|<span data-ttu-id="8aa3b-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="8aa3b-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="8aa3b-368">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-368">String</span></span>|  
|<span data-ttu-id="8aa3b-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="8aa3b-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="8aa3b-370">Int64</span><span class="sxs-lookup"><span data-stu-id="8aa3b-370">Int64</span></span>|  
|<span data-ttu-id="8aa3b-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="8aa3b-371">IS_NULLABLE</span></span>|<span data-ttu-id="8aa3b-372">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="8aa3b-372">Boolean</span></span>|  
|<span data-ttu-id="8aa3b-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="8aa3b-373">DATA_TYPE</span></span>|<span data-ttu-id="8aa3b-374">Int32</span><span class="sxs-lookup"><span data-stu-id="8aa3b-374">Int32</span></span>|  
|<span data-ttu-id="8aa3b-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="8aa3b-375">TYPE_GUID</span></span>|<span data-ttu-id="8aa3b-376">Guid</span><span class="sxs-lookup"><span data-stu-id="8aa3b-376">Guid</span></span>|  
|<span data-ttu-id="8aa3b-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="8aa3b-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="8aa3b-378">Int64</span><span class="sxs-lookup"><span data-stu-id="8aa3b-378">Int64</span></span>|  
|<span data-ttu-id="8aa3b-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="8aa3b-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="8aa3b-380">Int64</span><span class="sxs-lookup"><span data-stu-id="8aa3b-380">Int64</span></span>|  
|<span data-ttu-id="8aa3b-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="8aa3b-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="8aa3b-382">Int32</span><span class="sxs-lookup"><span data-stu-id="8aa3b-382">Int32</span></span>|  
|<span data-ttu-id="8aa3b-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="8aa3b-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="8aa3b-384">Int16</span><span class="sxs-lookup"><span data-stu-id="8aa3b-384">Int16</span></span>|  
|<span data-ttu-id="8aa3b-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="8aa3b-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="8aa3b-386">Int64</span><span class="sxs-lookup"><span data-stu-id="8aa3b-386">Int64</span></span>|  
|<span data-ttu-id="8aa3b-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8aa3b-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="8aa3b-388">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-388">String</span></span>|  
|<span data-ttu-id="8aa3b-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8aa3b-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="8aa3b-390">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-390">String</span></span>|  
|<span data-ttu-id="8aa3b-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="8aa3b-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="8aa3b-392">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-392">String</span></span>|  
|<span data-ttu-id="8aa3b-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8aa3b-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="8aa3b-394">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-394">String</span></span>|  
|<span data-ttu-id="8aa3b-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8aa3b-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="8aa3b-396">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-396">String</span></span>|  
|<span data-ttu-id="8aa3b-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="8aa3b-397">COLLATION_NAME</span></span>|<span data-ttu-id="8aa3b-398">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-398">String</span></span>|  
|<span data-ttu-id="8aa3b-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8aa3b-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="8aa3b-400">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-400">String</span></span>|  
|<span data-ttu-id="8aa3b-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8aa3b-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="8aa3b-402">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-402">String</span></span>|  
|<span data-ttu-id="8aa3b-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="8aa3b-403">DOMAIN_NAME</span></span>|<span data-ttu-id="8aa3b-404">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-404">String</span></span>|  
|<span data-ttu-id="8aa3b-405">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="8aa3b-405">DESCRIPTION</span></span>|<span data-ttu-id="8aa3b-406">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="8aa3b-407">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="8aa3b-407">Procedures</span></span>  
  
|<span data-ttu-id="8aa3b-408">columnName</span><span class="sxs-lookup"><span data-stu-id="8aa3b-408">ColumnName</span></span>|<span data-ttu-id="8aa3b-409">Veri türü</span><span class="sxs-lookup"><span data-stu-id="8aa3b-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8aa3b-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8aa3b-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="8aa3b-411">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-411">String</span></span>|  
|<span data-ttu-id="8aa3b-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8aa3b-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="8aa3b-413">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-413">String</span></span>|  
|<span data-ttu-id="8aa3b-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="8aa3b-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="8aa3b-415">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-415">String</span></span>|  
|<span data-ttu-id="8aa3b-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="8aa3b-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="8aa3b-417">Int16</span><span class="sxs-lookup"><span data-stu-id="8aa3b-417">Int16</span></span>|  
|<span data-ttu-id="8aa3b-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="8aa3b-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="8aa3b-419">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-419">String</span></span>|  
|<span data-ttu-id="8aa3b-420">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="8aa3b-420">DESCRIPTION</span></span>|<span data-ttu-id="8aa3b-421">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-421">String</span></span>|  
|<span data-ttu-id="8aa3b-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="8aa3b-422">DATE_CREATED</span></span>|<span data-ttu-id="8aa3b-423">DateTime</span><span class="sxs-lookup"><span data-stu-id="8aa3b-423">DateTime</span></span>|  
|<span data-ttu-id="8aa3b-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="8aa3b-424">DATE_MODIFIED</span></span>|<span data-ttu-id="8aa3b-425">DateTime</span><span class="sxs-lookup"><span data-stu-id="8aa3b-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="8aa3b-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="8aa3b-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="8aa3b-427">columnName</span><span class="sxs-lookup"><span data-stu-id="8aa3b-427">ColumnName</span></span>|<span data-ttu-id="8aa3b-428">Veri türü</span><span class="sxs-lookup"><span data-stu-id="8aa3b-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8aa3b-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8aa3b-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="8aa3b-430">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-430">String</span></span>|  
|<span data-ttu-id="8aa3b-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8aa3b-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="8aa3b-432">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-432">String</span></span>|  
|<span data-ttu-id="8aa3b-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="8aa3b-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="8aa3b-434">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-434">String</span></span>|  
|<span data-ttu-id="8aa3b-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="8aa3b-435">COLUMN_NAME</span></span>|<span data-ttu-id="8aa3b-436">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-436">String</span></span>|  
|<span data-ttu-id="8aa3b-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="8aa3b-437">COLUMN_GUID</span></span>|<span data-ttu-id="8aa3b-438">Guid</span><span class="sxs-lookup"><span data-stu-id="8aa3b-438">Guid</span></span>|  
|<span data-ttu-id="8aa3b-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="8aa3b-439">COLUMN_PROPID</span></span>|<span data-ttu-id="8aa3b-440">Int64</span><span class="sxs-lookup"><span data-stu-id="8aa3b-440">Int64</span></span>|  
|<span data-ttu-id="8aa3b-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="8aa3b-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="8aa3b-442">Int64</span><span class="sxs-lookup"><span data-stu-id="8aa3b-442">Int64</span></span>|  
|<span data-ttu-id="8aa3b-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="8aa3b-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="8aa3b-444">Int64</span><span class="sxs-lookup"><span data-stu-id="8aa3b-444">Int64</span></span>|  
|<span data-ttu-id="8aa3b-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="8aa3b-445">IS_NULLABLE</span></span>|<span data-ttu-id="8aa3b-446">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="8aa3b-446">Boolean</span></span>|  
|<span data-ttu-id="8aa3b-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="8aa3b-447">DATA_TYPE</span></span>|<span data-ttu-id="8aa3b-448">Int32</span><span class="sxs-lookup"><span data-stu-id="8aa3b-448">Int32</span></span>|  
|<span data-ttu-id="8aa3b-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="8aa3b-449">TYPE_GUID</span></span>|<span data-ttu-id="8aa3b-450">Guid</span><span class="sxs-lookup"><span data-stu-id="8aa3b-450">Guid</span></span>|  
|<span data-ttu-id="8aa3b-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="8aa3b-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="8aa3b-452">Int64</span><span class="sxs-lookup"><span data-stu-id="8aa3b-452">Int64</span></span>|  
|<span data-ttu-id="8aa3b-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="8aa3b-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="8aa3b-454">Int64</span><span class="sxs-lookup"><span data-stu-id="8aa3b-454">Int64</span></span>|  
|<span data-ttu-id="8aa3b-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="8aa3b-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="8aa3b-456">Int32</span><span class="sxs-lookup"><span data-stu-id="8aa3b-456">Int32</span></span>|  
|<span data-ttu-id="8aa3b-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="8aa3b-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="8aa3b-458">Int16</span><span class="sxs-lookup"><span data-stu-id="8aa3b-458">Int16</span></span>|  
|<span data-ttu-id="8aa3b-459">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="8aa3b-459">DESCRIPTION</span></span>|<span data-ttu-id="8aa3b-460">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-460">String</span></span>|  
|<span data-ttu-id="8aa3b-461">AŞIRI YÜKLEME</span><span class="sxs-lookup"><span data-stu-id="8aa3b-461">OVERLOAD</span></span>|<span data-ttu-id="8aa3b-462">Int16</span><span class="sxs-lookup"><span data-stu-id="8aa3b-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="8aa3b-463">Görünümler</span><span class="sxs-lookup"><span data-stu-id="8aa3b-463">Views</span></span>  
  
|<span data-ttu-id="8aa3b-464">columnName</span><span class="sxs-lookup"><span data-stu-id="8aa3b-464">ColumnName</span></span>|<span data-ttu-id="8aa3b-465">Veri türü</span><span class="sxs-lookup"><span data-stu-id="8aa3b-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8aa3b-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8aa3b-466">TABLE_CATALOG</span></span>|<span data-ttu-id="8aa3b-467">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-467">String</span></span>|  
|<span data-ttu-id="8aa3b-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8aa3b-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="8aa3b-469">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-469">String</span></span>|  
|<span data-ttu-id="8aa3b-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8aa3b-470">TABLE_NAME</span></span>|<span data-ttu-id="8aa3b-471">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-471">String</span></span>|  
|<span data-ttu-id="8aa3b-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="8aa3b-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="8aa3b-473">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-473">String</span></span>|  
|<span data-ttu-id="8aa3b-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="8aa3b-474">CHECK_OPTION</span></span>|<span data-ttu-id="8aa3b-475">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="8aa3b-475">Boolean</span></span>|  
|<span data-ttu-id="8aa3b-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="8aa3b-476">IS_UPDATABLE</span></span>|<span data-ttu-id="8aa3b-477">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="8aa3b-477">Boolean</span></span>|  
|<span data-ttu-id="8aa3b-478">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="8aa3b-478">DESCRIPTION</span></span>|<span data-ttu-id="8aa3b-479">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-479">String</span></span>|  
|<span data-ttu-id="8aa3b-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="8aa3b-480">DATE_CREATED</span></span>|<span data-ttu-id="8aa3b-481">DateTime</span><span class="sxs-lookup"><span data-stu-id="8aa3b-481">DateTime</span></span>|  
|<span data-ttu-id="8aa3b-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="8aa3b-482">DATE_MODIFIED</span></span>|<span data-ttu-id="8aa3b-483">DateTime</span><span class="sxs-lookup"><span data-stu-id="8aa3b-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="8aa3b-484">Dizinler</span><span class="sxs-lookup"><span data-stu-id="8aa3b-484">Indexes</span></span>  
  
|<span data-ttu-id="8aa3b-485">columnName</span><span class="sxs-lookup"><span data-stu-id="8aa3b-485">ColumnName</span></span>|<span data-ttu-id="8aa3b-486">Veri türü</span><span class="sxs-lookup"><span data-stu-id="8aa3b-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8aa3b-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8aa3b-487">TABLE_CATALOG</span></span>|<span data-ttu-id="8aa3b-488">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-488">String</span></span>|  
|<span data-ttu-id="8aa3b-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8aa3b-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="8aa3b-490">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-490">String</span></span>|  
|<span data-ttu-id="8aa3b-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8aa3b-491">TABLE_NAME</span></span>|<span data-ttu-id="8aa3b-492">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-492">String</span></span>|  
|<span data-ttu-id="8aa3b-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8aa3b-493">INDEX_CATALOG</span></span>|<span data-ttu-id="8aa3b-494">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-494">String</span></span>|  
|<span data-ttu-id="8aa3b-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8aa3b-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="8aa3b-496">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-496">String</span></span>|  
|<span data-ttu-id="8aa3b-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="8aa3b-497">INDEX_NAME</span></span>|<span data-ttu-id="8aa3b-498">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-498">String</span></span>|  
|<span data-ttu-id="8aa3b-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="8aa3b-499">PRIMARY_KEY</span></span>|<span data-ttu-id="8aa3b-500">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="8aa3b-500">Boolean</span></span>|  
|<span data-ttu-id="8aa3b-501">BENZERSİZ</span><span class="sxs-lookup"><span data-stu-id="8aa3b-501">UNIQUE</span></span>|<span data-ttu-id="8aa3b-502">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="8aa3b-502">Boolean</span></span>|  
|<span data-ttu-id="8aa3b-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="8aa3b-503">CLUSTERED</span></span>|<span data-ttu-id="8aa3b-504">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="8aa3b-504">Boolean</span></span>|  
|<span data-ttu-id="8aa3b-505">TÜRÜ</span><span class="sxs-lookup"><span data-stu-id="8aa3b-505">TYPE</span></span>|<span data-ttu-id="8aa3b-506">Int32</span><span class="sxs-lookup"><span data-stu-id="8aa3b-506">Int32</span></span>|  
|<span data-ttu-id="8aa3b-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="8aa3b-507">FILL_FACTOR</span></span>|<span data-ttu-id="8aa3b-508">Int32</span><span class="sxs-lookup"><span data-stu-id="8aa3b-508">Int32</span></span>|  
|<span data-ttu-id="8aa3b-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="8aa3b-509">INITIAL_SIZE</span></span>|<span data-ttu-id="8aa3b-510">Int32</span><span class="sxs-lookup"><span data-stu-id="8aa3b-510">Int32</span></span>|  
|<span data-ttu-id="8aa3b-511">NULLS</span><span class="sxs-lookup"><span data-stu-id="8aa3b-511">NULLS</span></span>|<span data-ttu-id="8aa3b-512">Int32</span><span class="sxs-lookup"><span data-stu-id="8aa3b-512">Int32</span></span>|  
|<span data-ttu-id="8aa3b-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="8aa3b-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="8aa3b-514">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="8aa3b-514">Boolean</span></span>|  
|<span data-ttu-id="8aa3b-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="8aa3b-515">AUTO_UPDATE</span></span>|<span data-ttu-id="8aa3b-516">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="8aa3b-516">Boolean</span></span>|  
|<span data-ttu-id="8aa3b-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="8aa3b-517">NULL_COLLATION</span></span>|<span data-ttu-id="8aa3b-518">Int32</span><span class="sxs-lookup"><span data-stu-id="8aa3b-518">Int32</span></span>|  
|<span data-ttu-id="8aa3b-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="8aa3b-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="8aa3b-520">Int64</span><span class="sxs-lookup"><span data-stu-id="8aa3b-520">Int64</span></span>|  
|<span data-ttu-id="8aa3b-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="8aa3b-521">COLUMN_NAME</span></span>|<span data-ttu-id="8aa3b-522">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-522">String</span></span>|  
|<span data-ttu-id="8aa3b-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="8aa3b-523">COLUMN_GUID</span></span>|<span data-ttu-id="8aa3b-524">Guid</span><span class="sxs-lookup"><span data-stu-id="8aa3b-524">Guid</span></span>|  
|<span data-ttu-id="8aa3b-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="8aa3b-525">COLUMN_PROPID</span></span>|<span data-ttu-id="8aa3b-526">Int64</span><span class="sxs-lookup"><span data-stu-id="8aa3b-526">Int64</span></span>|  
|<span data-ttu-id="8aa3b-527">HARMANLAMA</span><span class="sxs-lookup"><span data-stu-id="8aa3b-527">COLLATION</span></span>|<span data-ttu-id="8aa3b-528">Int16</span><span class="sxs-lookup"><span data-stu-id="8aa3b-528">Int16</span></span>|  
|<span data-ttu-id="8aa3b-529">ÖNEM DÜZEYİ</span><span class="sxs-lookup"><span data-stu-id="8aa3b-529">CARDINALITY</span></span>|<span data-ttu-id="8aa3b-530">Ondalık</span><span class="sxs-lookup"><span data-stu-id="8aa3b-530">Decimal</span></span>|  
|<span data-ttu-id="8aa3b-531">SAYFALARI</span><span class="sxs-lookup"><span data-stu-id="8aa3b-531">PAGES</span></span>|<span data-ttu-id="8aa3b-532">Int32</span><span class="sxs-lookup"><span data-stu-id="8aa3b-532">Int32</span></span>|  
|<span data-ttu-id="8aa3b-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="8aa3b-533">FILTER_CONDITION</span></span>|<span data-ttu-id="8aa3b-534">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-534">String</span></span>|  
|<span data-ttu-id="8aa3b-535">TÜMLEŞİK</span><span class="sxs-lookup"><span data-stu-id="8aa3b-535">INTEGRATED</span></span>|<span data-ttu-id="8aa3b-536">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="8aa3b-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="8aa3b-537">Microsoft Jet OLE DB sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="8aa3b-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="8aa3b-538">Microsoft Jet OLE DB sürücü ortak şeması koleksiyonları ek olarak aşağıdaki belirli şeması koleksiyonları destekler:</span><span class="sxs-lookup"><span data-stu-id="8aa3b-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="8aa3b-539">tabloları</span><span class="sxs-lookup"><span data-stu-id="8aa3b-539">Tables</span></span>  
  
-   <span data-ttu-id="8aa3b-540">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="8aa3b-540">Columns</span></span>  
  
-   <span data-ttu-id="8aa3b-541">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="8aa3b-541">Procedures</span></span>  
  
-   <span data-ttu-id="8aa3b-542">Görünümler</span><span class="sxs-lookup"><span data-stu-id="8aa3b-542">Views</span></span>  
  
-   <span data-ttu-id="8aa3b-543">Dizinler</span><span class="sxs-lookup"><span data-stu-id="8aa3b-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="8aa3b-544">tabloları</span><span class="sxs-lookup"><span data-stu-id="8aa3b-544">Tables</span></span>  
  
|<span data-ttu-id="8aa3b-545">columnName</span><span class="sxs-lookup"><span data-stu-id="8aa3b-545">ColumnName</span></span>|<span data-ttu-id="8aa3b-546">Veri türü</span><span class="sxs-lookup"><span data-stu-id="8aa3b-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8aa3b-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8aa3b-547">TABLE_CATALOG</span></span>|<span data-ttu-id="8aa3b-548">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-548">String</span></span>|  
|<span data-ttu-id="8aa3b-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8aa3b-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="8aa3b-550">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-550">String</span></span>|  
|<span data-ttu-id="8aa3b-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8aa3b-551">TABLE_NAME</span></span>|<span data-ttu-id="8aa3b-552">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-552">String</span></span>|  
|<span data-ttu-id="8aa3b-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="8aa3b-553">TABLE_TYPE</span></span>|<span data-ttu-id="8aa3b-554">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-554">String</span></span>|  
|<span data-ttu-id="8aa3b-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="8aa3b-555">TABLE_GUID</span></span>|<span data-ttu-id="8aa3b-556">Guid</span><span class="sxs-lookup"><span data-stu-id="8aa3b-556">Guid</span></span>|  
|<span data-ttu-id="8aa3b-557">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="8aa3b-557">DESCRIPTION</span></span>|<span data-ttu-id="8aa3b-558">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-558">String</span></span>|  
|<span data-ttu-id="8aa3b-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="8aa3b-559">TABLE_PROPID</span></span>|<span data-ttu-id="8aa3b-560">Int64</span><span class="sxs-lookup"><span data-stu-id="8aa3b-560">Int64</span></span>|  
|<span data-ttu-id="8aa3b-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="8aa3b-561">DATE_CREATED</span></span>|<span data-ttu-id="8aa3b-562">DateTime</span><span class="sxs-lookup"><span data-stu-id="8aa3b-562">DateTime</span></span>|  
|<span data-ttu-id="8aa3b-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="8aa3b-563">DATE_MODIFIED</span></span>|<span data-ttu-id="8aa3b-564">DateTime</span><span class="sxs-lookup"><span data-stu-id="8aa3b-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="8aa3b-565">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="8aa3b-565">Columns</span></span>  
  
|<span data-ttu-id="8aa3b-566">columnName</span><span class="sxs-lookup"><span data-stu-id="8aa3b-566">ColumnName</span></span>|<span data-ttu-id="8aa3b-567">Veri türü</span><span class="sxs-lookup"><span data-stu-id="8aa3b-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8aa3b-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8aa3b-568">TABLE_CATALOG</span></span>|<span data-ttu-id="8aa3b-569">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-569">String</span></span>|  
|<span data-ttu-id="8aa3b-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8aa3b-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="8aa3b-571">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-571">String</span></span>|  
|<span data-ttu-id="8aa3b-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8aa3b-572">TABLE_NAME</span></span>|<span data-ttu-id="8aa3b-573">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-573">String</span></span>|  
|<span data-ttu-id="8aa3b-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="8aa3b-574">COLUMN_NAME</span></span>|<span data-ttu-id="8aa3b-575">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-575">String</span></span>|  
|<span data-ttu-id="8aa3b-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="8aa3b-576">COLUMN_GUID</span></span>|<span data-ttu-id="8aa3b-577">Guid</span><span class="sxs-lookup"><span data-stu-id="8aa3b-577">Guid</span></span>|  
|<span data-ttu-id="8aa3b-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="8aa3b-578">COLUMN_PROPID</span></span>|<span data-ttu-id="8aa3b-579">Int64</span><span class="sxs-lookup"><span data-stu-id="8aa3b-579">Int64</span></span>|  
|<span data-ttu-id="8aa3b-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="8aa3b-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="8aa3b-581">Int64</span><span class="sxs-lookup"><span data-stu-id="8aa3b-581">Int64</span></span>|  
|<span data-ttu-id="8aa3b-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="8aa3b-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="8aa3b-583">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="8aa3b-583">Boolean</span></span>|  
|<span data-ttu-id="8aa3b-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="8aa3b-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="8aa3b-585">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-585">String</span></span>|  
|<span data-ttu-id="8aa3b-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="8aa3b-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="8aa3b-587">Int64</span><span class="sxs-lookup"><span data-stu-id="8aa3b-587">Int64</span></span>|  
|<span data-ttu-id="8aa3b-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="8aa3b-588">IS_NULLABLE</span></span>|<span data-ttu-id="8aa3b-589">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="8aa3b-589">Boolean</span></span>|  
|<span data-ttu-id="8aa3b-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="8aa3b-590">DATA_TYPE</span></span>|<span data-ttu-id="8aa3b-591">Int32</span><span class="sxs-lookup"><span data-stu-id="8aa3b-591">Int32</span></span>|  
|<span data-ttu-id="8aa3b-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="8aa3b-592">TYPE_GUID</span></span>|<span data-ttu-id="8aa3b-593">Guid</span><span class="sxs-lookup"><span data-stu-id="8aa3b-593">Guid</span></span>|  
|<span data-ttu-id="8aa3b-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="8aa3b-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="8aa3b-595">Int64</span><span class="sxs-lookup"><span data-stu-id="8aa3b-595">Int64</span></span>|  
|<span data-ttu-id="8aa3b-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="8aa3b-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="8aa3b-597">Int64</span><span class="sxs-lookup"><span data-stu-id="8aa3b-597">Int64</span></span>|  
|<span data-ttu-id="8aa3b-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="8aa3b-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="8aa3b-599">Int32</span><span class="sxs-lookup"><span data-stu-id="8aa3b-599">Int32</span></span>|  
|<span data-ttu-id="8aa3b-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="8aa3b-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="8aa3b-601">Int16</span><span class="sxs-lookup"><span data-stu-id="8aa3b-601">Int16</span></span>|  
|<span data-ttu-id="8aa3b-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="8aa3b-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="8aa3b-603">Int64</span><span class="sxs-lookup"><span data-stu-id="8aa3b-603">Int64</span></span>|  
|<span data-ttu-id="8aa3b-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8aa3b-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="8aa3b-605">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-605">String</span></span>|  
|<span data-ttu-id="8aa3b-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8aa3b-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="8aa3b-607">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-607">String</span></span>|  
|<span data-ttu-id="8aa3b-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="8aa3b-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="8aa3b-609">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-609">String</span></span>|  
|<span data-ttu-id="8aa3b-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8aa3b-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="8aa3b-611">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-611">String</span></span>|  
|<span data-ttu-id="8aa3b-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8aa3b-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="8aa3b-613">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-613">String</span></span>|  
|<span data-ttu-id="8aa3b-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="8aa3b-614">COLLATION_NAME</span></span>|<span data-ttu-id="8aa3b-615">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-615">String</span></span>|  
|<span data-ttu-id="8aa3b-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8aa3b-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="8aa3b-617">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-617">String</span></span>|  
|<span data-ttu-id="8aa3b-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8aa3b-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="8aa3b-619">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-619">String</span></span>|  
|<span data-ttu-id="8aa3b-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="8aa3b-620">DOMAIN_NAME</span></span>|<span data-ttu-id="8aa3b-621">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-621">String</span></span>|  
|<span data-ttu-id="8aa3b-622">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="8aa3b-622">DESCRIPTION</span></span>|<span data-ttu-id="8aa3b-623">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="8aa3b-624">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="8aa3b-624">Procedures</span></span>  
  
|<span data-ttu-id="8aa3b-625">columnName</span><span class="sxs-lookup"><span data-stu-id="8aa3b-625">ColumnName</span></span>|<span data-ttu-id="8aa3b-626">Veri türü</span><span class="sxs-lookup"><span data-stu-id="8aa3b-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8aa3b-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8aa3b-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="8aa3b-628">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-628">String</span></span>|  
|<span data-ttu-id="8aa3b-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8aa3b-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="8aa3b-630">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-630">String</span></span>|  
|<span data-ttu-id="8aa3b-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="8aa3b-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="8aa3b-632">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-632">String</span></span>|  
|<span data-ttu-id="8aa3b-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="8aa3b-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="8aa3b-634">Int16</span><span class="sxs-lookup"><span data-stu-id="8aa3b-634">Int16</span></span>|  
|<span data-ttu-id="8aa3b-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="8aa3b-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="8aa3b-636">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-636">String</span></span>|  
|<span data-ttu-id="8aa3b-637">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="8aa3b-637">DESCRIPTION</span></span>|<span data-ttu-id="8aa3b-638">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-638">String</span></span>|  
|<span data-ttu-id="8aa3b-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="8aa3b-639">DATE_CREATED</span></span>|<span data-ttu-id="8aa3b-640">DateTime</span><span class="sxs-lookup"><span data-stu-id="8aa3b-640">DateTime</span></span>|  
|<span data-ttu-id="8aa3b-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="8aa3b-641">DATE_MODIFIED</span></span>|<span data-ttu-id="8aa3b-642">DateTime</span><span class="sxs-lookup"><span data-stu-id="8aa3b-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="8aa3b-643">Görünümler</span><span class="sxs-lookup"><span data-stu-id="8aa3b-643">Views</span></span>  
  
|<span data-ttu-id="8aa3b-644">columnName</span><span class="sxs-lookup"><span data-stu-id="8aa3b-644">ColumnName</span></span>|<span data-ttu-id="8aa3b-645">Veri türü</span><span class="sxs-lookup"><span data-stu-id="8aa3b-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8aa3b-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8aa3b-646">TABLE_CATALOG</span></span>|<span data-ttu-id="8aa3b-647">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-647">String</span></span>|  
|<span data-ttu-id="8aa3b-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8aa3b-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="8aa3b-649">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-649">String</span></span>|  
|<span data-ttu-id="8aa3b-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8aa3b-650">TABLE_NAME</span></span>|<span data-ttu-id="8aa3b-651">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-651">String</span></span>|  
|<span data-ttu-id="8aa3b-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="8aa3b-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="8aa3b-653">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-653">String</span></span>|  
|<span data-ttu-id="8aa3b-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="8aa3b-654">CHECK_OPTION</span></span>|<span data-ttu-id="8aa3b-655">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="8aa3b-655">Boolean</span></span>|  
|<span data-ttu-id="8aa3b-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="8aa3b-656">IS_UPDATABLE</span></span>|<span data-ttu-id="8aa3b-657">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="8aa3b-657">Boolean</span></span>|  
|<span data-ttu-id="8aa3b-658">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="8aa3b-658">DESCRIPTION</span></span>|<span data-ttu-id="8aa3b-659">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-659">String</span></span>|  
|<span data-ttu-id="8aa3b-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="8aa3b-660">DATE_CREATED</span></span>|<span data-ttu-id="8aa3b-661">DateTime</span><span class="sxs-lookup"><span data-stu-id="8aa3b-661">DateTime</span></span>|  
|<span data-ttu-id="8aa3b-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="8aa3b-662">DATE_MODIFIED</span></span>|<span data-ttu-id="8aa3b-663">DateTime</span><span class="sxs-lookup"><span data-stu-id="8aa3b-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="8aa3b-664">Dizinler</span><span class="sxs-lookup"><span data-stu-id="8aa3b-664">Indexes</span></span>  
  
|<span data-ttu-id="8aa3b-665">columnName</span><span class="sxs-lookup"><span data-stu-id="8aa3b-665">ColumnName</span></span>|<span data-ttu-id="8aa3b-666">Veri türü</span><span class="sxs-lookup"><span data-stu-id="8aa3b-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8aa3b-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8aa3b-667">TABLE_CATALOG</span></span>|<span data-ttu-id="8aa3b-668">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-668">String</span></span>|  
|<span data-ttu-id="8aa3b-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8aa3b-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="8aa3b-670">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-670">String</span></span>|  
|<span data-ttu-id="8aa3b-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8aa3b-671">TABLE_NAME</span></span>|<span data-ttu-id="8aa3b-672">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-672">String</span></span>|  
|<span data-ttu-id="8aa3b-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8aa3b-673">INDEX_CATALOG</span></span>|<span data-ttu-id="8aa3b-674">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-674">String</span></span>|  
|<span data-ttu-id="8aa3b-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8aa3b-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="8aa3b-676">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-676">String</span></span>|  
|<span data-ttu-id="8aa3b-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="8aa3b-677">INDEX_NAME</span></span>|<span data-ttu-id="8aa3b-678">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-678">String</span></span>|  
|<span data-ttu-id="8aa3b-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="8aa3b-679">PRIMARY_KEY</span></span>|<span data-ttu-id="8aa3b-680">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="8aa3b-680">Boolean</span></span>|  
|<span data-ttu-id="8aa3b-681">BENZERSİZ</span><span class="sxs-lookup"><span data-stu-id="8aa3b-681">UNIQUE</span></span>|<span data-ttu-id="8aa3b-682">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="8aa3b-682">Boolean</span></span>|  
|<span data-ttu-id="8aa3b-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="8aa3b-683">CLUSTERED</span></span>|<span data-ttu-id="8aa3b-684">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="8aa3b-684">Boolean</span></span>|  
|<span data-ttu-id="8aa3b-685">TÜRÜ</span><span class="sxs-lookup"><span data-stu-id="8aa3b-685">TYPE</span></span>|<span data-ttu-id="8aa3b-686">Int32</span><span class="sxs-lookup"><span data-stu-id="8aa3b-686">Int32</span></span>|  
|<span data-ttu-id="8aa3b-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="8aa3b-687">FILL_FACTOR</span></span>|<span data-ttu-id="8aa3b-688">Int32</span><span class="sxs-lookup"><span data-stu-id="8aa3b-688">Int32</span></span>|  
|<span data-ttu-id="8aa3b-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="8aa3b-689">INITIAL_SIZE</span></span>|<span data-ttu-id="8aa3b-690">Int32</span><span class="sxs-lookup"><span data-stu-id="8aa3b-690">Int32</span></span>|  
|<span data-ttu-id="8aa3b-691">NULLS</span><span class="sxs-lookup"><span data-stu-id="8aa3b-691">NULLS</span></span>|<span data-ttu-id="8aa3b-692">Int32</span><span class="sxs-lookup"><span data-stu-id="8aa3b-692">Int32</span></span>|  
|<span data-ttu-id="8aa3b-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="8aa3b-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="8aa3b-694">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="8aa3b-694">Boolean</span></span>|  
|<span data-ttu-id="8aa3b-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="8aa3b-695">AUTO_UPDATE</span></span>|<span data-ttu-id="8aa3b-696">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="8aa3b-696">Boolean</span></span>|  
|<span data-ttu-id="8aa3b-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="8aa3b-697">NULL_COLLATION</span></span>|<span data-ttu-id="8aa3b-698">Int32</span><span class="sxs-lookup"><span data-stu-id="8aa3b-698">Int32</span></span>|  
|<span data-ttu-id="8aa3b-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="8aa3b-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="8aa3b-700">Int64</span><span class="sxs-lookup"><span data-stu-id="8aa3b-700">Int64</span></span>|  
|<span data-ttu-id="8aa3b-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="8aa3b-701">COLUMN_NAME</span></span>|<span data-ttu-id="8aa3b-702">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-702">String</span></span>|  
|<span data-ttu-id="8aa3b-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="8aa3b-703">COLUMN_GUID</span></span>|<span data-ttu-id="8aa3b-704">Guid</span><span class="sxs-lookup"><span data-stu-id="8aa3b-704">Guid</span></span>|  
|<span data-ttu-id="8aa3b-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="8aa3b-705">COLUMN_PROPID</span></span>|<span data-ttu-id="8aa3b-706">Int64</span><span class="sxs-lookup"><span data-stu-id="8aa3b-706">Int64</span></span>|  
|<span data-ttu-id="8aa3b-707">HARMANLAMA</span><span class="sxs-lookup"><span data-stu-id="8aa3b-707">COLLATION</span></span>|<span data-ttu-id="8aa3b-708">Int16</span><span class="sxs-lookup"><span data-stu-id="8aa3b-708">Int16</span></span>|  
|<span data-ttu-id="8aa3b-709">ÖNEM DÜZEYİ</span><span class="sxs-lookup"><span data-stu-id="8aa3b-709">CARDINALITY</span></span>|<span data-ttu-id="8aa3b-710">Ondalık</span><span class="sxs-lookup"><span data-stu-id="8aa3b-710">Decimal</span></span>|  
|<span data-ttu-id="8aa3b-711">SAYFALARI</span><span class="sxs-lookup"><span data-stu-id="8aa3b-711">PAGES</span></span>|<span data-ttu-id="8aa3b-712">Int32</span><span class="sxs-lookup"><span data-stu-id="8aa3b-712">Int32</span></span>|  
|<span data-ttu-id="8aa3b-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="8aa3b-713">FILTER_CONDITION</span></span>|<span data-ttu-id="8aa3b-714">Dize</span><span class="sxs-lookup"><span data-stu-id="8aa3b-714">String</span></span>|  
|<span data-ttu-id="8aa3b-715">TÜMLEŞİK</span><span class="sxs-lookup"><span data-stu-id="8aa3b-715">INTEGRATED</span></span>|<span data-ttu-id="8aa3b-716">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="8aa3b-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8aa3b-717">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8aa3b-717">See Also</span></span>  
 [<span data-ttu-id="8aa3b-718">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="8aa3b-718">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
