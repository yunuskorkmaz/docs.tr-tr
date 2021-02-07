---
description: 'Daha fazla bilgi edinin: OLE DB şema koleksiyonları'
title: OLE DB Şema Koleksiyonları
ms.date: 03/30/2017
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
ms.openlocfilehash: d4d4bae5387575bdaeaf013ed690e95aa3259068
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99672627"
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="b31f5-103">OLE DB Şema Koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="b31f5-103">OLE DB Schema Collections</span></span>

<span data-ttu-id="b31f5-104">Bu bölümde Microsoft SQL Server, Oracle ve Microsoft Jet için OLE DB sağlayıcıları için şema koleksiyonu desteği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b31f5-104">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="b31f5-105">Microsoft SQL Server OLE DB sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="b31f5-105">Microsoft SQL Server OLE DB Provider</span></span>  

 <span data-ttu-id="b31f5-106">Microsoft SQL Server OLE DB sürücü, ortak şema koleksiyonlarına ek olarak aşağıdaki belirli şema koleksiyonlarını destekler:</span><span class="sxs-lookup"><span data-stu-id="b31f5-106">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="b31f5-107">Tablolar</span><span class="sxs-lookup"><span data-stu-id="b31f5-107">Tables</span></span>  
  
- <span data-ttu-id="b31f5-108">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="b31f5-108">Columns</span></span>  
  
- <span data-ttu-id="b31f5-109">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="b31f5-109">Procedures</span></span>  
  
- <span data-ttu-id="b31f5-110">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="b31f5-110">ProcedureParameters</span></span>  
  
- <span data-ttu-id="b31f5-111">Katalog</span><span class="sxs-lookup"><span data-stu-id="b31f5-111">Catalog</span></span>  
  
- <span data-ttu-id="b31f5-112">Dizinler</span><span class="sxs-lookup"><span data-stu-id="b31f5-112">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="b31f5-113">Tablolar</span><span class="sxs-lookup"><span data-stu-id="b31f5-113">Tables</span></span>  
  
|<span data-ttu-id="b31f5-114">ColumnName</span><span class="sxs-lookup"><span data-stu-id="b31f5-114">ColumnName</span></span>|<span data-ttu-id="b31f5-115">DataType</span><span class="sxs-lookup"><span data-stu-id="b31f5-115">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b31f5-116">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b31f5-116">TABLE_CATALOG</span></span>|<span data-ttu-id="b31f5-117">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-117">String</span></span>|  
|<span data-ttu-id="b31f5-118">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b31f5-118">TABLE_SCHEMA</span></span>|<span data-ttu-id="b31f5-119">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-119">String</span></span>|  
|<span data-ttu-id="b31f5-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b31f5-120">TABLE_NAME</span></span>|<span data-ttu-id="b31f5-121">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-121">String</span></span>|  
|<span data-ttu-id="b31f5-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b31f5-122">TABLE_TYPE</span></span>|<span data-ttu-id="b31f5-123">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-123">String</span></span>|  
|<span data-ttu-id="b31f5-124">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="b31f5-124">TABLE_GUID</span></span>|<span data-ttu-id="b31f5-125">Guid</span><span class="sxs-lookup"><span data-stu-id="b31f5-125">Guid</span></span>|  
|<span data-ttu-id="b31f5-126">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="b31f5-126">DESCRIPTION</span></span>|<span data-ttu-id="b31f5-127">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-127">String</span></span>|  
|<span data-ttu-id="b31f5-128">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="b31f5-128">TABLE_PROPID</span></span>|<span data-ttu-id="b31f5-129">Int64</span><span class="sxs-lookup"><span data-stu-id="b31f5-129">Int64</span></span>|  
|<span data-ttu-id="b31f5-130">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="b31f5-130">DATE_CREATED</span></span>|<span data-ttu-id="b31f5-131">DateTime</span><span class="sxs-lookup"><span data-stu-id="b31f5-131">DateTime</span></span>|  
|<span data-ttu-id="b31f5-132">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="b31f5-132">DATE_MODIFIED</span></span>|<span data-ttu-id="b31f5-133">DateTime</span><span class="sxs-lookup"><span data-stu-id="b31f5-133">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="b31f5-134">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="b31f5-134">Columns</span></span>  
  
|<span data-ttu-id="b31f5-135">ColumnName</span><span class="sxs-lookup"><span data-stu-id="b31f5-135">ColumnName</span></span>|<span data-ttu-id="b31f5-136">DataType</span><span class="sxs-lookup"><span data-stu-id="b31f5-136">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b31f5-137">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b31f5-137">TABLE_CATALOG</span></span>|<span data-ttu-id="b31f5-138">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-138">String</span></span>|  
|<span data-ttu-id="b31f5-139">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b31f5-139">TABLE_SCHEMA</span></span>|<span data-ttu-id="b31f5-140">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-140">String</span></span>|  
|<span data-ttu-id="b31f5-141">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b31f5-141">TABLE_NAME</span></span>|<span data-ttu-id="b31f5-142">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-142">String</span></span>|  
|<span data-ttu-id="b31f5-143">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b31f5-143">COLUMN_NAME</span></span>|<span data-ttu-id="b31f5-144">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-144">String</span></span>|  
|<span data-ttu-id="b31f5-145">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="b31f5-145">COLUMN_GUID</span></span>|<span data-ttu-id="b31f5-146">Guid</span><span class="sxs-lookup"><span data-stu-id="b31f5-146">Guid</span></span>|  
|<span data-ttu-id="b31f5-147">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="b31f5-147">COLUMN_PROPID</span></span>|<span data-ttu-id="b31f5-148">Int64</span><span class="sxs-lookup"><span data-stu-id="b31f5-148">Int64</span></span>|  
|<span data-ttu-id="b31f5-149">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b31f5-149">ORDINAL_POSITION</span></span>|<span data-ttu-id="b31f5-150">Int64</span><span class="sxs-lookup"><span data-stu-id="b31f5-150">Int64</span></span>|  
|<span data-ttu-id="b31f5-151">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="b31f5-151">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="b31f5-152">Boole</span><span class="sxs-lookup"><span data-stu-id="b31f5-152">Boolean</span></span>|  
|<span data-ttu-id="b31f5-153">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="b31f5-153">COLUMN_DEFAULT</span></span>|<span data-ttu-id="b31f5-154">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-154">String</span></span>|  
|<span data-ttu-id="b31f5-155">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="b31f5-155">COLUMN_FLAGS</span></span>|<span data-ttu-id="b31f5-156">Int64</span><span class="sxs-lookup"><span data-stu-id="b31f5-156">Int64</span></span>|  
|<span data-ttu-id="b31f5-157">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b31f5-157">IS_NULLABLE</span></span>|<span data-ttu-id="b31f5-158">Boole</span><span class="sxs-lookup"><span data-stu-id="b31f5-158">Boolean</span></span>|  
|<span data-ttu-id="b31f5-159">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b31f5-159">DATA_TYPE</span></span>|<span data-ttu-id="b31f5-160">Int32</span><span class="sxs-lookup"><span data-stu-id="b31f5-160">Int32</span></span>|  
|<span data-ttu-id="b31f5-161">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="b31f5-161">TYPE_GUID</span></span>|<span data-ttu-id="b31f5-162">Guid</span><span class="sxs-lookup"><span data-stu-id="b31f5-162">Guid</span></span>|  
|<span data-ttu-id="b31f5-163">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b31f5-163">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="b31f5-164">Int64</span><span class="sxs-lookup"><span data-stu-id="b31f5-164">Int64</span></span>|  
|<span data-ttu-id="b31f5-165">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b31f5-165">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="b31f5-166">Int64</span><span class="sxs-lookup"><span data-stu-id="b31f5-166">Int64</span></span>|  
|<span data-ttu-id="b31f5-167">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="b31f5-167">NUMERIC_PRECISION</span></span>|<span data-ttu-id="b31f5-168">Int32</span><span class="sxs-lookup"><span data-stu-id="b31f5-168">Int32</span></span>|  
|<span data-ttu-id="b31f5-169">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="b31f5-169">NUMERIC_SCALE</span></span>|<span data-ttu-id="b31f5-170">Int16</span><span class="sxs-lookup"><span data-stu-id="b31f5-170">Int16</span></span>|  
|<span data-ttu-id="b31f5-171">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="b31f5-171">DATETIME_PRECISION</span></span>|<span data-ttu-id="b31f5-172">Int64</span><span class="sxs-lookup"><span data-stu-id="b31f5-172">Int64</span></span>|  
|<span data-ttu-id="b31f5-173">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b31f5-173">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="b31f5-174">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-174">String</span></span>|  
|<span data-ttu-id="b31f5-175">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b31f5-175">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="b31f5-176">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-176">String</span></span>|  
|<span data-ttu-id="b31f5-177">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="b31f5-177">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="b31f5-178">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-178">String</span></span>|  
|<span data-ttu-id="b31f5-179">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b31f5-179">COLLATION_CATALOG</span></span>|<span data-ttu-id="b31f5-180">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-180">String</span></span>|  
|<span data-ttu-id="b31f5-181">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b31f5-181">COLLATION_SCHEMA</span></span>|<span data-ttu-id="b31f5-182">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-182">String</span></span>|  
|<span data-ttu-id="b31f5-183">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="b31f5-183">COLLATION_NAME</span></span>|<span data-ttu-id="b31f5-184">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-184">String</span></span>|  
|<span data-ttu-id="b31f5-185">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b31f5-185">DOMAIN_CATALOG</span></span>|<span data-ttu-id="b31f5-186">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-186">String</span></span>|  
|<span data-ttu-id="b31f5-187">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b31f5-187">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="b31f5-188">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-188">String</span></span>|  
|<span data-ttu-id="b31f5-189">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="b31f5-189">DOMAIN_NAME</span></span>|<span data-ttu-id="b31f5-190">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-190">String</span></span>|  
|<span data-ttu-id="b31f5-191">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="b31f5-191">DESCRIPTION</span></span>|<span data-ttu-id="b31f5-192">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-192">String</span></span>|  
|<span data-ttu-id="b31f5-193">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="b31f5-193">COLUMN_LCID</span></span>|<span data-ttu-id="b31f5-194">Int32</span><span class="sxs-lookup"><span data-stu-id="b31f5-194">Int32</span></span>|  
|<span data-ttu-id="b31f5-195">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="b31f5-195">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="b31f5-196">Int32</span><span class="sxs-lookup"><span data-stu-id="b31f5-196">Int32</span></span>|  
|<span data-ttu-id="b31f5-197">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="b31f5-197">COLUMN_SORTID</span></span>|<span data-ttu-id="b31f5-198">Int32</span><span class="sxs-lookup"><span data-stu-id="b31f5-198">Int32</span></span>|  
|<span data-ttu-id="b31f5-199">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="b31f5-199">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="b31f5-200">Byte []</span><span class="sxs-lookup"><span data-stu-id="b31f5-200">Byte[]</span></span>|  
|<span data-ttu-id="b31f5-201">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="b31f5-201">IS_COMPUTED</span></span>|<span data-ttu-id="b31f5-202">Boole</span><span class="sxs-lookup"><span data-stu-id="b31f5-202">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="b31f5-203">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="b31f5-203">Procedures</span></span>  
  
|<span data-ttu-id="b31f5-204">ColumnName</span><span class="sxs-lookup"><span data-stu-id="b31f5-204">ColumnName</span></span>|<span data-ttu-id="b31f5-205">DataType</span><span class="sxs-lookup"><span data-stu-id="b31f5-205">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b31f5-206">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b31f5-206">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="b31f5-207">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-207">String</span></span>|  
|<span data-ttu-id="b31f5-208">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b31f5-208">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="b31f5-209">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-209">String</span></span>|  
|<span data-ttu-id="b31f5-210">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b31f5-210">PROCEDURE_NAME</span></span>|<span data-ttu-id="b31f5-211">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-211">String</span></span>|  
|<span data-ttu-id="b31f5-212">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b31f5-212">PROCEDURE_TYPE</span></span>|<span data-ttu-id="b31f5-213">Int16</span><span class="sxs-lookup"><span data-stu-id="b31f5-213">Int16</span></span>|  
|<span data-ttu-id="b31f5-214">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="b31f5-214">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="b31f5-215">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-215">String</span></span>|  
|<span data-ttu-id="b31f5-216">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="b31f5-216">DESCRIPTION</span></span>|<span data-ttu-id="b31f5-217">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-217">String</span></span>|  
|<span data-ttu-id="b31f5-218">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="b31f5-218">DATE_CREATED</span></span>|<span data-ttu-id="b31f5-219">DateTime</span><span class="sxs-lookup"><span data-stu-id="b31f5-219">DateTime</span></span>|  
|<span data-ttu-id="b31f5-220">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="b31f5-220">DATE_MODIFIED</span></span>|<span data-ttu-id="b31f5-221">DateTime</span><span class="sxs-lookup"><span data-stu-id="b31f5-221">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="b31f5-222">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="b31f5-222">ProcedureParameters</span></span>  
  
|<span data-ttu-id="b31f5-223">ColumnName</span><span class="sxs-lookup"><span data-stu-id="b31f5-223">ColumnName</span></span>|<span data-ttu-id="b31f5-224">DataType</span><span class="sxs-lookup"><span data-stu-id="b31f5-224">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b31f5-225">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b31f5-225">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="b31f5-226">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-226">String</span></span>|  
|<span data-ttu-id="b31f5-227">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b31f5-227">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="b31f5-228">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-228">String</span></span>|  
|<span data-ttu-id="b31f5-229">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b31f5-229">PROCEDURE_NAME</span></span>|<span data-ttu-id="b31f5-230">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-230">String</span></span>|  
|<span data-ttu-id="b31f5-231">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="b31f5-231">PARAMETER_NAME</span></span>|<span data-ttu-id="b31f5-232">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-232">String</span></span>|  
|<span data-ttu-id="b31f5-233">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b31f5-233">ORDINAL_POSITION</span></span>|<span data-ttu-id="b31f5-234">Int32</span><span class="sxs-lookup"><span data-stu-id="b31f5-234">Int32</span></span>|  
|<span data-ttu-id="b31f5-235">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="b31f5-235">PARAMETER_TYPE</span></span>|<span data-ttu-id="b31f5-236">Int32</span><span class="sxs-lookup"><span data-stu-id="b31f5-236">Int32</span></span>|  
|<span data-ttu-id="b31f5-237">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="b31f5-237">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="b31f5-238">Boole</span><span class="sxs-lookup"><span data-stu-id="b31f5-238">Boolean</span></span>|  
|<span data-ttu-id="b31f5-239">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="b31f5-239">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="b31f5-240">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-240">String</span></span>|  
|<span data-ttu-id="b31f5-241">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b31f5-241">IS_NULLABLE</span></span>|<span data-ttu-id="b31f5-242">Boole</span><span class="sxs-lookup"><span data-stu-id="b31f5-242">Boolean</span></span>|  
|<span data-ttu-id="b31f5-243">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b31f5-243">DATA_TYPE</span></span>|<span data-ttu-id="b31f5-244">Int32</span><span class="sxs-lookup"><span data-stu-id="b31f5-244">Int32</span></span>|  
|<span data-ttu-id="b31f5-245">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b31f5-245">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="b31f5-246">Int64</span><span class="sxs-lookup"><span data-stu-id="b31f5-246">Int64</span></span>|  
|<span data-ttu-id="b31f5-247">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b31f5-247">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="b31f5-248">Int64</span><span class="sxs-lookup"><span data-stu-id="b31f5-248">Int64</span></span>|  
|<span data-ttu-id="b31f5-249">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="b31f5-249">NUMERIC_PRECISION</span></span>|<span data-ttu-id="b31f5-250">Int32</span><span class="sxs-lookup"><span data-stu-id="b31f5-250">Int32</span></span>|  
|<span data-ttu-id="b31f5-251">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="b31f5-251">NUMERIC_SCALE</span></span>|<span data-ttu-id="b31f5-252">Int16</span><span class="sxs-lookup"><span data-stu-id="b31f5-252">Int16</span></span>|  
|<span data-ttu-id="b31f5-253">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="b31f5-253">DESCRIPTION</span></span>|<span data-ttu-id="b31f5-254">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-254">String</span></span>|  
|<span data-ttu-id="b31f5-255">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="b31f5-255">TYPE_NAME</span></span>|<span data-ttu-id="b31f5-256">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-256">String</span></span>|  
|<span data-ttu-id="b31f5-257">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="b31f5-257">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="b31f5-258">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-258">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="b31f5-259">Katalog</span><span class="sxs-lookup"><span data-stu-id="b31f5-259">Catalog</span></span>  
  
|<span data-ttu-id="b31f5-260">ColumnName</span><span class="sxs-lookup"><span data-stu-id="b31f5-260">ColumnName</span></span>|<span data-ttu-id="b31f5-261">DataType</span><span class="sxs-lookup"><span data-stu-id="b31f5-261">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b31f5-262">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="b31f5-262">CATALOG_NAME</span></span>|<span data-ttu-id="b31f5-263">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-263">String</span></span>|  
|<span data-ttu-id="b31f5-264">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="b31f5-264">DESCRIPTION</span></span>|<span data-ttu-id="b31f5-265">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-265">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="b31f5-266">Dizinler</span><span class="sxs-lookup"><span data-stu-id="b31f5-266">Indexes</span></span>  
  
|<span data-ttu-id="b31f5-267">ColumnName</span><span class="sxs-lookup"><span data-stu-id="b31f5-267">ColumnName</span></span>|<span data-ttu-id="b31f5-268">DataType</span><span class="sxs-lookup"><span data-stu-id="b31f5-268">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b31f5-269">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b31f5-269">TABLE_CATALOG</span></span>|<span data-ttu-id="b31f5-270">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-270">String</span></span>|  
|<span data-ttu-id="b31f5-271">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b31f5-271">TABLE_SCHEMA</span></span>|<span data-ttu-id="b31f5-272">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-272">String</span></span>|  
|<span data-ttu-id="b31f5-273">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b31f5-273">TABLE_NAME</span></span>|<span data-ttu-id="b31f5-274">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-274">String</span></span>|  
|<span data-ttu-id="b31f5-275">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b31f5-275">INDEX_CATALOG</span></span>|<span data-ttu-id="b31f5-276">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-276">String</span></span>|  
|<span data-ttu-id="b31f5-277">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b31f5-277">INDEX_SCHEMA</span></span>|<span data-ttu-id="b31f5-278">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-278">String</span></span>|  
|<span data-ttu-id="b31f5-279">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="b31f5-279">INDEX_NAME</span></span>|<span data-ttu-id="b31f5-280">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-280">String</span></span>|  
|<span data-ttu-id="b31f5-281">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="b31f5-281">PRIMARY_KEY</span></span>|<span data-ttu-id="b31f5-282">Boole</span><span class="sxs-lookup"><span data-stu-id="b31f5-282">Boolean</span></span>|  
|<span data-ttu-id="b31f5-283">EŞI</span><span class="sxs-lookup"><span data-stu-id="b31f5-283">UNIQUE</span></span>|<span data-ttu-id="b31f5-284">Boole</span><span class="sxs-lookup"><span data-stu-id="b31f5-284">Boolean</span></span>|  
|<span data-ttu-id="b31f5-285">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="b31f5-285">CLUSTERED</span></span>|<span data-ttu-id="b31f5-286">Boole</span><span class="sxs-lookup"><span data-stu-id="b31f5-286">Boolean</span></span>|  
|<span data-ttu-id="b31f5-287">TÜR</span><span class="sxs-lookup"><span data-stu-id="b31f5-287">TYPE</span></span>|<span data-ttu-id="b31f5-288">Int32</span><span class="sxs-lookup"><span data-stu-id="b31f5-288">Int32</span></span>|  
|<span data-ttu-id="b31f5-289">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="b31f5-289">FILL_FACTOR</span></span>|<span data-ttu-id="b31f5-290">Int32</span><span class="sxs-lookup"><span data-stu-id="b31f5-290">Int32</span></span>|  
|<span data-ttu-id="b31f5-291">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="b31f5-291">INITIAL_SIZE</span></span>|<span data-ttu-id="b31f5-292">Int32</span><span class="sxs-lookup"><span data-stu-id="b31f5-292">Int32</span></span>|  
|<span data-ttu-id="b31f5-293">NULLS</span><span class="sxs-lookup"><span data-stu-id="b31f5-293">NULLS</span></span>|<span data-ttu-id="b31f5-294">Int32</span><span class="sxs-lookup"><span data-stu-id="b31f5-294">Int32</span></span>|  
|<span data-ttu-id="b31f5-295">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="b31f5-295">SORT_BOOKMARKS</span></span>|<span data-ttu-id="b31f5-296">Boole</span><span class="sxs-lookup"><span data-stu-id="b31f5-296">Boolean</span></span>|  
|<span data-ttu-id="b31f5-297">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="b31f5-297">AUTO_UPDATE</span></span>|<span data-ttu-id="b31f5-298">Boole</span><span class="sxs-lookup"><span data-stu-id="b31f5-298">Boolean</span></span>|  
|<span data-ttu-id="b31f5-299">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="b31f5-299">NULL_COLLATION</span></span>|<span data-ttu-id="b31f5-300">Int32</span><span class="sxs-lookup"><span data-stu-id="b31f5-300">Int32</span></span>|  
|<span data-ttu-id="b31f5-301">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b31f5-301">ORDINAL_POSITION</span></span>|<span data-ttu-id="b31f5-302">Int64</span><span class="sxs-lookup"><span data-stu-id="b31f5-302">Int64</span></span>|  
|<span data-ttu-id="b31f5-303">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b31f5-303">COLUMN_NAME</span></span>|<span data-ttu-id="b31f5-304">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-304">String</span></span>|  
|<span data-ttu-id="b31f5-305">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="b31f5-305">COLUMN_GUID</span></span>|<span data-ttu-id="b31f5-306">Guid</span><span class="sxs-lookup"><span data-stu-id="b31f5-306">Guid</span></span>|  
|<span data-ttu-id="b31f5-307">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="b31f5-307">COLUMN_PROPID</span></span>|<span data-ttu-id="b31f5-308">Int64</span><span class="sxs-lookup"><span data-stu-id="b31f5-308">Int64</span></span>|  
|<span data-ttu-id="b31f5-309">MEDIĞINDEN</span><span class="sxs-lookup"><span data-stu-id="b31f5-309">COLLATION</span></span>|<span data-ttu-id="b31f5-310">Int16</span><span class="sxs-lookup"><span data-stu-id="b31f5-310">Int16</span></span>|  
|<span data-ttu-id="b31f5-311">ITE</span><span class="sxs-lookup"><span data-stu-id="b31f5-311">CARDINALITY</span></span>|<span data-ttu-id="b31f5-312">Ondalık</span><span class="sxs-lookup"><span data-stu-id="b31f5-312">Decimal</span></span>|  
|<span data-ttu-id="b31f5-313">SAYFALARı</span><span class="sxs-lookup"><span data-stu-id="b31f5-313">PAGES</span></span>|<span data-ttu-id="b31f5-314">Int32</span><span class="sxs-lookup"><span data-stu-id="b31f5-314">Int32</span></span>|  
|<span data-ttu-id="b31f5-315">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="b31f5-315">FILTER_CONDITION</span></span>|<span data-ttu-id="b31f5-316">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-316">String</span></span>|  
|<span data-ttu-id="b31f5-317">ILMIŞTIR</span><span class="sxs-lookup"><span data-stu-id="b31f5-317">INTEGRATED</span></span>|<span data-ttu-id="b31f5-318">Boole</span><span class="sxs-lookup"><span data-stu-id="b31f5-318">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="b31f5-319">Microsoft Oracle OLE DB sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="b31f5-319">Microsoft Oracle OLE DB Provider</span></span>  

 <span data-ttu-id="b31f5-320">Microsoft Oracle OLE DB sürücüsü, ortak şema koleksiyonlarına ek olarak aşağıdaki belirli şema koleksiyonlarını destekler:</span><span class="sxs-lookup"><span data-stu-id="b31f5-320">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="b31f5-321">Tablolar</span><span class="sxs-lookup"><span data-stu-id="b31f5-321">Tables</span></span>  
  
- <span data-ttu-id="b31f5-322">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="b31f5-322">Columns</span></span>  
  
- <span data-ttu-id="b31f5-323">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="b31f5-323">Procedures</span></span>  
  
- <span data-ttu-id="b31f5-324">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="b31f5-324">ProcedureColumns</span></span>  
  
- <span data-ttu-id="b31f5-325">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="b31f5-325">ProcedureParameters</span></span>  
  
- <span data-ttu-id="b31f5-326">Görünümler</span><span class="sxs-lookup"><span data-stu-id="b31f5-326">Views</span></span>  
  
- <span data-ttu-id="b31f5-327">Dizinler</span><span class="sxs-lookup"><span data-stu-id="b31f5-327">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="b31f5-328">Tablolar</span><span class="sxs-lookup"><span data-stu-id="b31f5-328">Tables</span></span>  
  
|<span data-ttu-id="b31f5-329">ColumnName</span><span class="sxs-lookup"><span data-stu-id="b31f5-329">ColumnName</span></span>|<span data-ttu-id="b31f5-330">DataType</span><span class="sxs-lookup"><span data-stu-id="b31f5-330">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b31f5-331">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b31f5-331">TABLE_CATALOG</span></span>|<span data-ttu-id="b31f5-332">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-332">String</span></span>|  
|<span data-ttu-id="b31f5-333">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b31f5-333">TABLE_SCHEMA</span></span>|<span data-ttu-id="b31f5-334">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-334">String</span></span>|  
|<span data-ttu-id="b31f5-335">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b31f5-335">TABLE_NAME</span></span>|<span data-ttu-id="b31f5-336">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-336">String</span></span>|  
|<span data-ttu-id="b31f5-337">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b31f5-337">TABLE_TYPE</span></span>|<span data-ttu-id="b31f5-338">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-338">String</span></span>|  
|<span data-ttu-id="b31f5-339">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="b31f5-339">TABLE_GUID</span></span>|<span data-ttu-id="b31f5-340">Guid</span><span class="sxs-lookup"><span data-stu-id="b31f5-340">Guid</span></span>|  
|<span data-ttu-id="b31f5-341">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="b31f5-341">DESCRIPTION</span></span>|<span data-ttu-id="b31f5-342">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-342">String</span></span>|  
|<span data-ttu-id="b31f5-343">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="b31f5-343">TABLE_PROPID</span></span>|<span data-ttu-id="b31f5-344">Int64</span><span class="sxs-lookup"><span data-stu-id="b31f5-344">Int64</span></span>|  
|<span data-ttu-id="b31f5-345">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="b31f5-345">DATE_CREATED</span></span>|<span data-ttu-id="b31f5-346">DateTime</span><span class="sxs-lookup"><span data-stu-id="b31f5-346">DateTime</span></span>|  
|<span data-ttu-id="b31f5-347">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="b31f5-347">DATE_MODIFIED</span></span>|<span data-ttu-id="b31f5-348">DateTime</span><span class="sxs-lookup"><span data-stu-id="b31f5-348">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="b31f5-349">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="b31f5-349">Columns</span></span>  
  
|<span data-ttu-id="b31f5-350">ColumnName</span><span class="sxs-lookup"><span data-stu-id="b31f5-350">ColumnName</span></span>|<span data-ttu-id="b31f5-351">DataType</span><span class="sxs-lookup"><span data-stu-id="b31f5-351">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b31f5-352">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b31f5-352">TABLE_CATALOG</span></span>|<span data-ttu-id="b31f5-353">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-353">String</span></span>|  
|<span data-ttu-id="b31f5-354">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b31f5-354">TABLE_SCHEMA</span></span>|<span data-ttu-id="b31f5-355">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-355">String</span></span>|  
|<span data-ttu-id="b31f5-356">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b31f5-356">TABLE_NAME</span></span>|<span data-ttu-id="b31f5-357">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-357">String</span></span>|  
|<span data-ttu-id="b31f5-358">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b31f5-358">COLUMN_NAME</span></span>|<span data-ttu-id="b31f5-359">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-359">String</span></span>|  
|<span data-ttu-id="b31f5-360">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="b31f5-360">COLUMN_GUID</span></span>|<span data-ttu-id="b31f5-361">Guid</span><span class="sxs-lookup"><span data-stu-id="b31f5-361">Guid</span></span>|  
|<span data-ttu-id="b31f5-362">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="b31f5-362">COLUMN_PROPID</span></span>|<span data-ttu-id="b31f5-363">Int64</span><span class="sxs-lookup"><span data-stu-id="b31f5-363">Int64</span></span>|  
|<span data-ttu-id="b31f5-364">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b31f5-364">ORDINAL_POSITION</span></span>|<span data-ttu-id="b31f5-365">Int64</span><span class="sxs-lookup"><span data-stu-id="b31f5-365">Int64</span></span>|  
|<span data-ttu-id="b31f5-366">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="b31f5-366">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="b31f5-367">Boole</span><span class="sxs-lookup"><span data-stu-id="b31f5-367">Boolean</span></span>|  
|<span data-ttu-id="b31f5-368">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="b31f5-368">COLUMN_DEFAULT</span></span>|<span data-ttu-id="b31f5-369">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-369">String</span></span>|  
|<span data-ttu-id="b31f5-370">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="b31f5-370">COLUMN_FLAGS</span></span>|<span data-ttu-id="b31f5-371">Int64</span><span class="sxs-lookup"><span data-stu-id="b31f5-371">Int64</span></span>|  
|<span data-ttu-id="b31f5-372">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b31f5-372">IS_NULLABLE</span></span>|<span data-ttu-id="b31f5-373">Boole</span><span class="sxs-lookup"><span data-stu-id="b31f5-373">Boolean</span></span>|  
|<span data-ttu-id="b31f5-374">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b31f5-374">DATA_TYPE</span></span>|<span data-ttu-id="b31f5-375">Int32</span><span class="sxs-lookup"><span data-stu-id="b31f5-375">Int32</span></span>|  
|<span data-ttu-id="b31f5-376">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="b31f5-376">TYPE_GUID</span></span>|<span data-ttu-id="b31f5-377">Guid</span><span class="sxs-lookup"><span data-stu-id="b31f5-377">Guid</span></span>|  
|<span data-ttu-id="b31f5-378">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b31f5-378">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="b31f5-379">Int64</span><span class="sxs-lookup"><span data-stu-id="b31f5-379">Int64</span></span>|  
|<span data-ttu-id="b31f5-380">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b31f5-380">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="b31f5-381">Int64</span><span class="sxs-lookup"><span data-stu-id="b31f5-381">Int64</span></span>|  
|<span data-ttu-id="b31f5-382">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="b31f5-382">NUMERIC_PRECISION</span></span>|<span data-ttu-id="b31f5-383">Int32</span><span class="sxs-lookup"><span data-stu-id="b31f5-383">Int32</span></span>|  
|<span data-ttu-id="b31f5-384">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="b31f5-384">NUMERIC_SCALE</span></span>|<span data-ttu-id="b31f5-385">Int16</span><span class="sxs-lookup"><span data-stu-id="b31f5-385">Int16</span></span>|  
|<span data-ttu-id="b31f5-386">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="b31f5-386">DATETIME_PRECISION</span></span>|<span data-ttu-id="b31f5-387">Int64</span><span class="sxs-lookup"><span data-stu-id="b31f5-387">Int64</span></span>|  
|<span data-ttu-id="b31f5-388">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b31f5-388">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="b31f5-389">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-389">String</span></span>|  
|<span data-ttu-id="b31f5-390">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b31f5-390">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="b31f5-391">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-391">String</span></span>|  
|<span data-ttu-id="b31f5-392">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="b31f5-392">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="b31f5-393">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-393">String</span></span>|  
|<span data-ttu-id="b31f5-394">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b31f5-394">COLLATION_CATALOG</span></span>|<span data-ttu-id="b31f5-395">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-395">String</span></span>|  
|<span data-ttu-id="b31f5-396">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b31f5-396">COLLATION_SCHEMA</span></span>|<span data-ttu-id="b31f5-397">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-397">String</span></span>|  
|<span data-ttu-id="b31f5-398">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="b31f5-398">COLLATION_NAME</span></span>|<span data-ttu-id="b31f5-399">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-399">String</span></span>|  
|<span data-ttu-id="b31f5-400">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b31f5-400">DOMAIN_CATALOG</span></span>|<span data-ttu-id="b31f5-401">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-401">String</span></span>|  
|<span data-ttu-id="b31f5-402">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b31f5-402">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="b31f5-403">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-403">String</span></span>|  
|<span data-ttu-id="b31f5-404">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="b31f5-404">DOMAIN_NAME</span></span>|<span data-ttu-id="b31f5-405">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-405">String</span></span>|  
|<span data-ttu-id="b31f5-406">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="b31f5-406">DESCRIPTION</span></span>|<span data-ttu-id="b31f5-407">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-407">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="b31f5-408">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="b31f5-408">Procedures</span></span>  
  
|<span data-ttu-id="b31f5-409">ColumnName</span><span class="sxs-lookup"><span data-stu-id="b31f5-409">ColumnName</span></span>|<span data-ttu-id="b31f5-410">DataType</span><span class="sxs-lookup"><span data-stu-id="b31f5-410">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b31f5-411">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b31f5-411">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="b31f5-412">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-412">String</span></span>|  
|<span data-ttu-id="b31f5-413">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b31f5-413">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="b31f5-414">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-414">String</span></span>|  
|<span data-ttu-id="b31f5-415">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b31f5-415">PROCEDURE_NAME</span></span>|<span data-ttu-id="b31f5-416">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-416">String</span></span>|  
|<span data-ttu-id="b31f5-417">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b31f5-417">PROCEDURE_TYPE</span></span>|<span data-ttu-id="b31f5-418">Int16</span><span class="sxs-lookup"><span data-stu-id="b31f5-418">Int16</span></span>|  
|<span data-ttu-id="b31f5-419">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="b31f5-419">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="b31f5-420">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-420">String</span></span>|  
|<span data-ttu-id="b31f5-421">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="b31f5-421">DESCRIPTION</span></span>|<span data-ttu-id="b31f5-422">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-422">String</span></span>|  
|<span data-ttu-id="b31f5-423">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="b31f5-423">DATE_CREATED</span></span>|<span data-ttu-id="b31f5-424">DateTime</span><span class="sxs-lookup"><span data-stu-id="b31f5-424">DateTime</span></span>|  
|<span data-ttu-id="b31f5-425">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="b31f5-425">DATE_MODIFIED</span></span>|<span data-ttu-id="b31f5-426">DateTime</span><span class="sxs-lookup"><span data-stu-id="b31f5-426">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="b31f5-427">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="b31f5-427">ProcedureColumns</span></span>  
  
|<span data-ttu-id="b31f5-428">ColumnName</span><span class="sxs-lookup"><span data-stu-id="b31f5-428">ColumnName</span></span>|<span data-ttu-id="b31f5-429">DataType</span><span class="sxs-lookup"><span data-stu-id="b31f5-429">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b31f5-430">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b31f5-430">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="b31f5-431">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-431">String</span></span>|  
|<span data-ttu-id="b31f5-432">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b31f5-432">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="b31f5-433">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-433">String</span></span>|  
|<span data-ttu-id="b31f5-434">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b31f5-434">PROCEDURE_NAME</span></span>|<span data-ttu-id="b31f5-435">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-435">String</span></span>|  
|<span data-ttu-id="b31f5-436">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b31f5-436">COLUMN_NAME</span></span>|<span data-ttu-id="b31f5-437">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-437">String</span></span>|  
|<span data-ttu-id="b31f5-438">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="b31f5-438">COLUMN_GUID</span></span>|<span data-ttu-id="b31f5-439">Guid</span><span class="sxs-lookup"><span data-stu-id="b31f5-439">Guid</span></span>|  
|<span data-ttu-id="b31f5-440">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="b31f5-440">COLUMN_PROPID</span></span>|<span data-ttu-id="b31f5-441">Int64</span><span class="sxs-lookup"><span data-stu-id="b31f5-441">Int64</span></span>|  
|<span data-ttu-id="b31f5-442">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="b31f5-442">ROWSET_NUMBER</span></span>|<span data-ttu-id="b31f5-443">Int64</span><span class="sxs-lookup"><span data-stu-id="b31f5-443">Int64</span></span>|  
|<span data-ttu-id="b31f5-444">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b31f5-444">ORDINAL_POSITION</span></span>|<span data-ttu-id="b31f5-445">Int64</span><span class="sxs-lookup"><span data-stu-id="b31f5-445">Int64</span></span>|  
|<span data-ttu-id="b31f5-446">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b31f5-446">IS_NULLABLE</span></span>|<span data-ttu-id="b31f5-447">Boole</span><span class="sxs-lookup"><span data-stu-id="b31f5-447">Boolean</span></span>|  
|<span data-ttu-id="b31f5-448">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b31f5-448">DATA_TYPE</span></span>|<span data-ttu-id="b31f5-449">Int32</span><span class="sxs-lookup"><span data-stu-id="b31f5-449">Int32</span></span>|  
|<span data-ttu-id="b31f5-450">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="b31f5-450">TYPE_GUID</span></span>|<span data-ttu-id="b31f5-451">Guid</span><span class="sxs-lookup"><span data-stu-id="b31f5-451">Guid</span></span>|  
|<span data-ttu-id="b31f5-452">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b31f5-452">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="b31f5-453">Int64</span><span class="sxs-lookup"><span data-stu-id="b31f5-453">Int64</span></span>|  
|<span data-ttu-id="b31f5-454">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b31f5-454">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="b31f5-455">Int64</span><span class="sxs-lookup"><span data-stu-id="b31f5-455">Int64</span></span>|  
|<span data-ttu-id="b31f5-456">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="b31f5-456">NUMERIC_PRECISION</span></span>|<span data-ttu-id="b31f5-457">Int32</span><span class="sxs-lookup"><span data-stu-id="b31f5-457">Int32</span></span>|  
|<span data-ttu-id="b31f5-458">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="b31f5-458">NUMERIC_SCALE</span></span>|<span data-ttu-id="b31f5-459">Int16</span><span class="sxs-lookup"><span data-stu-id="b31f5-459">Int16</span></span>|  
|<span data-ttu-id="b31f5-460">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="b31f5-460">DESCRIPTION</span></span>|<span data-ttu-id="b31f5-461">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-461">String</span></span>|  
|<span data-ttu-id="b31f5-462">YÜKLEMEK</span><span class="sxs-lookup"><span data-stu-id="b31f5-462">OVERLOAD</span></span>|<span data-ttu-id="b31f5-463">Int16</span><span class="sxs-lookup"><span data-stu-id="b31f5-463">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="b31f5-464">Görünümler</span><span class="sxs-lookup"><span data-stu-id="b31f5-464">Views</span></span>  
  
|<span data-ttu-id="b31f5-465">ColumnName</span><span class="sxs-lookup"><span data-stu-id="b31f5-465">ColumnName</span></span>|<span data-ttu-id="b31f5-466">DataType</span><span class="sxs-lookup"><span data-stu-id="b31f5-466">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b31f5-467">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b31f5-467">TABLE_CATALOG</span></span>|<span data-ttu-id="b31f5-468">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-468">String</span></span>|  
|<span data-ttu-id="b31f5-469">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b31f5-469">TABLE_SCHEMA</span></span>|<span data-ttu-id="b31f5-470">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-470">String</span></span>|  
|<span data-ttu-id="b31f5-471">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b31f5-471">TABLE_NAME</span></span>|<span data-ttu-id="b31f5-472">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-472">String</span></span>|  
|<span data-ttu-id="b31f5-473">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="b31f5-473">VIEW_DEFINITION</span></span>|<span data-ttu-id="b31f5-474">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-474">String</span></span>|  
|<span data-ttu-id="b31f5-475">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="b31f5-475">CHECK_OPTION</span></span>|<span data-ttu-id="b31f5-476">Boole</span><span class="sxs-lookup"><span data-stu-id="b31f5-476">Boolean</span></span>|  
|<span data-ttu-id="b31f5-477">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="b31f5-477">IS_UPDATABLE</span></span>|<span data-ttu-id="b31f5-478">Boole</span><span class="sxs-lookup"><span data-stu-id="b31f5-478">Boolean</span></span>|  
|<span data-ttu-id="b31f5-479">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="b31f5-479">DESCRIPTION</span></span>|<span data-ttu-id="b31f5-480">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-480">String</span></span>|  
|<span data-ttu-id="b31f5-481">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="b31f5-481">DATE_CREATED</span></span>|<span data-ttu-id="b31f5-482">DateTime</span><span class="sxs-lookup"><span data-stu-id="b31f5-482">DateTime</span></span>|  
|<span data-ttu-id="b31f5-483">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="b31f5-483">DATE_MODIFIED</span></span>|<span data-ttu-id="b31f5-484">DateTime</span><span class="sxs-lookup"><span data-stu-id="b31f5-484">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="b31f5-485">Dizinler</span><span class="sxs-lookup"><span data-stu-id="b31f5-485">Indexes</span></span>  
  
|<span data-ttu-id="b31f5-486">ColumnName</span><span class="sxs-lookup"><span data-stu-id="b31f5-486">ColumnName</span></span>|<span data-ttu-id="b31f5-487">DataType</span><span class="sxs-lookup"><span data-stu-id="b31f5-487">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b31f5-488">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b31f5-488">TABLE_CATALOG</span></span>|<span data-ttu-id="b31f5-489">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-489">String</span></span>|  
|<span data-ttu-id="b31f5-490">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b31f5-490">TABLE_SCHEMA</span></span>|<span data-ttu-id="b31f5-491">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-491">String</span></span>|  
|<span data-ttu-id="b31f5-492">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b31f5-492">TABLE_NAME</span></span>|<span data-ttu-id="b31f5-493">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-493">String</span></span>|  
|<span data-ttu-id="b31f5-494">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b31f5-494">INDEX_CATALOG</span></span>|<span data-ttu-id="b31f5-495">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-495">String</span></span>|  
|<span data-ttu-id="b31f5-496">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b31f5-496">INDEX_SCHEMA</span></span>|<span data-ttu-id="b31f5-497">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-497">String</span></span>|  
|<span data-ttu-id="b31f5-498">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="b31f5-498">INDEX_NAME</span></span>|<span data-ttu-id="b31f5-499">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-499">String</span></span>|  
|<span data-ttu-id="b31f5-500">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="b31f5-500">PRIMARY_KEY</span></span>|<span data-ttu-id="b31f5-501">Boole</span><span class="sxs-lookup"><span data-stu-id="b31f5-501">Boolean</span></span>|  
|<span data-ttu-id="b31f5-502">EŞI</span><span class="sxs-lookup"><span data-stu-id="b31f5-502">UNIQUE</span></span>|<span data-ttu-id="b31f5-503">Boole</span><span class="sxs-lookup"><span data-stu-id="b31f5-503">Boolean</span></span>|  
|<span data-ttu-id="b31f5-504">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="b31f5-504">CLUSTERED</span></span>|<span data-ttu-id="b31f5-505">Boole</span><span class="sxs-lookup"><span data-stu-id="b31f5-505">Boolean</span></span>|  
|<span data-ttu-id="b31f5-506">TÜR</span><span class="sxs-lookup"><span data-stu-id="b31f5-506">TYPE</span></span>|<span data-ttu-id="b31f5-507">Int32</span><span class="sxs-lookup"><span data-stu-id="b31f5-507">Int32</span></span>|  
|<span data-ttu-id="b31f5-508">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="b31f5-508">FILL_FACTOR</span></span>|<span data-ttu-id="b31f5-509">Int32</span><span class="sxs-lookup"><span data-stu-id="b31f5-509">Int32</span></span>|  
|<span data-ttu-id="b31f5-510">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="b31f5-510">INITIAL_SIZE</span></span>|<span data-ttu-id="b31f5-511">Int32</span><span class="sxs-lookup"><span data-stu-id="b31f5-511">Int32</span></span>|  
|<span data-ttu-id="b31f5-512">NULLS</span><span class="sxs-lookup"><span data-stu-id="b31f5-512">NULLS</span></span>|<span data-ttu-id="b31f5-513">Int32</span><span class="sxs-lookup"><span data-stu-id="b31f5-513">Int32</span></span>|  
|<span data-ttu-id="b31f5-514">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="b31f5-514">SORT_BOOKMARKS</span></span>|<span data-ttu-id="b31f5-515">Boole</span><span class="sxs-lookup"><span data-stu-id="b31f5-515">Boolean</span></span>|  
|<span data-ttu-id="b31f5-516">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="b31f5-516">AUTO_UPDATE</span></span>|<span data-ttu-id="b31f5-517">Boole</span><span class="sxs-lookup"><span data-stu-id="b31f5-517">Boolean</span></span>|  
|<span data-ttu-id="b31f5-518">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="b31f5-518">NULL_COLLATION</span></span>|<span data-ttu-id="b31f5-519">Int32</span><span class="sxs-lookup"><span data-stu-id="b31f5-519">Int32</span></span>|  
|<span data-ttu-id="b31f5-520">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b31f5-520">ORDINAL_POSITION</span></span>|<span data-ttu-id="b31f5-521">Int64</span><span class="sxs-lookup"><span data-stu-id="b31f5-521">Int64</span></span>|  
|<span data-ttu-id="b31f5-522">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b31f5-522">COLUMN_NAME</span></span>|<span data-ttu-id="b31f5-523">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-523">String</span></span>|  
|<span data-ttu-id="b31f5-524">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="b31f5-524">COLUMN_GUID</span></span>|<span data-ttu-id="b31f5-525">Guid</span><span class="sxs-lookup"><span data-stu-id="b31f5-525">Guid</span></span>|  
|<span data-ttu-id="b31f5-526">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="b31f5-526">COLUMN_PROPID</span></span>|<span data-ttu-id="b31f5-527">Int64</span><span class="sxs-lookup"><span data-stu-id="b31f5-527">Int64</span></span>|  
|<span data-ttu-id="b31f5-528">MEDIĞINDEN</span><span class="sxs-lookup"><span data-stu-id="b31f5-528">COLLATION</span></span>|<span data-ttu-id="b31f5-529">Int16</span><span class="sxs-lookup"><span data-stu-id="b31f5-529">Int16</span></span>|  
|<span data-ttu-id="b31f5-530">ITE</span><span class="sxs-lookup"><span data-stu-id="b31f5-530">CARDINALITY</span></span>|<span data-ttu-id="b31f5-531">Ondalık</span><span class="sxs-lookup"><span data-stu-id="b31f5-531">Decimal</span></span>|  
|<span data-ttu-id="b31f5-532">SAYFALARı</span><span class="sxs-lookup"><span data-stu-id="b31f5-532">PAGES</span></span>|<span data-ttu-id="b31f5-533">Int32</span><span class="sxs-lookup"><span data-stu-id="b31f5-533">Int32</span></span>|  
|<span data-ttu-id="b31f5-534">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="b31f5-534">FILTER_CONDITION</span></span>|<span data-ttu-id="b31f5-535">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-535">String</span></span>|  
|<span data-ttu-id="b31f5-536">ILMIŞTIR</span><span class="sxs-lookup"><span data-stu-id="b31f5-536">INTEGRATED</span></span>|<span data-ttu-id="b31f5-537">Boole</span><span class="sxs-lookup"><span data-stu-id="b31f5-537">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="b31f5-538">Microsoft Jet OLE DB sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="b31f5-538">Microsoft Jet OLE DB Provider</span></span>  

 <span data-ttu-id="b31f5-539">Microsoft Jet OLE DB sürücüsü, ortak şema koleksiyonlarına ek olarak aşağıdaki belirli şema koleksiyonlarını destekler:</span><span class="sxs-lookup"><span data-stu-id="b31f5-539">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="b31f5-540">Tablolar</span><span class="sxs-lookup"><span data-stu-id="b31f5-540">Tables</span></span>  
  
- <span data-ttu-id="b31f5-541">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="b31f5-541">Columns</span></span>  
  
- <span data-ttu-id="b31f5-542">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="b31f5-542">Procedures</span></span>  
  
- <span data-ttu-id="b31f5-543">Görünümler</span><span class="sxs-lookup"><span data-stu-id="b31f5-543">Views</span></span>  
  
- <span data-ttu-id="b31f5-544">Dizinler</span><span class="sxs-lookup"><span data-stu-id="b31f5-544">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="b31f5-545">Tablolar</span><span class="sxs-lookup"><span data-stu-id="b31f5-545">Tables</span></span>  
  
|<span data-ttu-id="b31f5-546">ColumnName</span><span class="sxs-lookup"><span data-stu-id="b31f5-546">ColumnName</span></span>|<span data-ttu-id="b31f5-547">DataType</span><span class="sxs-lookup"><span data-stu-id="b31f5-547">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b31f5-548">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b31f5-548">TABLE_CATALOG</span></span>|<span data-ttu-id="b31f5-549">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-549">String</span></span>|  
|<span data-ttu-id="b31f5-550">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b31f5-550">TABLE_SCHEMA</span></span>|<span data-ttu-id="b31f5-551">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-551">String</span></span>|  
|<span data-ttu-id="b31f5-552">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b31f5-552">TABLE_NAME</span></span>|<span data-ttu-id="b31f5-553">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-553">String</span></span>|  
|<span data-ttu-id="b31f5-554">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b31f5-554">TABLE_TYPE</span></span>|<span data-ttu-id="b31f5-555">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-555">String</span></span>|  
|<span data-ttu-id="b31f5-556">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="b31f5-556">TABLE_GUID</span></span>|<span data-ttu-id="b31f5-557">Guid</span><span class="sxs-lookup"><span data-stu-id="b31f5-557">Guid</span></span>|  
|<span data-ttu-id="b31f5-558">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="b31f5-558">DESCRIPTION</span></span>|<span data-ttu-id="b31f5-559">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-559">String</span></span>|  
|<span data-ttu-id="b31f5-560">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="b31f5-560">TABLE_PROPID</span></span>|<span data-ttu-id="b31f5-561">Int64</span><span class="sxs-lookup"><span data-stu-id="b31f5-561">Int64</span></span>|  
|<span data-ttu-id="b31f5-562">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="b31f5-562">DATE_CREATED</span></span>|<span data-ttu-id="b31f5-563">DateTime</span><span class="sxs-lookup"><span data-stu-id="b31f5-563">DateTime</span></span>|  
|<span data-ttu-id="b31f5-564">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="b31f5-564">DATE_MODIFIED</span></span>|<span data-ttu-id="b31f5-565">DateTime</span><span class="sxs-lookup"><span data-stu-id="b31f5-565">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="b31f5-566">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="b31f5-566">Columns</span></span>  
  
|<span data-ttu-id="b31f5-567">ColumnName</span><span class="sxs-lookup"><span data-stu-id="b31f5-567">ColumnName</span></span>|<span data-ttu-id="b31f5-568">DataType</span><span class="sxs-lookup"><span data-stu-id="b31f5-568">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b31f5-569">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b31f5-569">TABLE_CATALOG</span></span>|<span data-ttu-id="b31f5-570">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-570">String</span></span>|  
|<span data-ttu-id="b31f5-571">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b31f5-571">TABLE_SCHEMA</span></span>|<span data-ttu-id="b31f5-572">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-572">String</span></span>|  
|<span data-ttu-id="b31f5-573">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b31f5-573">TABLE_NAME</span></span>|<span data-ttu-id="b31f5-574">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-574">String</span></span>|  
|<span data-ttu-id="b31f5-575">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b31f5-575">COLUMN_NAME</span></span>|<span data-ttu-id="b31f5-576">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-576">String</span></span>|  
|<span data-ttu-id="b31f5-577">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="b31f5-577">COLUMN_GUID</span></span>|<span data-ttu-id="b31f5-578">Guid</span><span class="sxs-lookup"><span data-stu-id="b31f5-578">Guid</span></span>|  
|<span data-ttu-id="b31f5-579">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="b31f5-579">COLUMN_PROPID</span></span>|<span data-ttu-id="b31f5-580">Int64</span><span class="sxs-lookup"><span data-stu-id="b31f5-580">Int64</span></span>|  
|<span data-ttu-id="b31f5-581">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b31f5-581">ORDINAL_POSITION</span></span>|<span data-ttu-id="b31f5-582">Int64</span><span class="sxs-lookup"><span data-stu-id="b31f5-582">Int64</span></span>|  
|<span data-ttu-id="b31f5-583">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="b31f5-583">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="b31f5-584">Boole</span><span class="sxs-lookup"><span data-stu-id="b31f5-584">Boolean</span></span>|  
|<span data-ttu-id="b31f5-585">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="b31f5-585">COLUMN_DEFAULT</span></span>|<span data-ttu-id="b31f5-586">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-586">String</span></span>|  
|<span data-ttu-id="b31f5-587">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="b31f5-587">COLUMN_FLAGS</span></span>|<span data-ttu-id="b31f5-588">Int64</span><span class="sxs-lookup"><span data-stu-id="b31f5-588">Int64</span></span>|  
|<span data-ttu-id="b31f5-589">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b31f5-589">IS_NULLABLE</span></span>|<span data-ttu-id="b31f5-590">Boole</span><span class="sxs-lookup"><span data-stu-id="b31f5-590">Boolean</span></span>|  
|<span data-ttu-id="b31f5-591">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b31f5-591">DATA_TYPE</span></span>|<span data-ttu-id="b31f5-592">Int32</span><span class="sxs-lookup"><span data-stu-id="b31f5-592">Int32</span></span>|  
|<span data-ttu-id="b31f5-593">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="b31f5-593">TYPE_GUID</span></span>|<span data-ttu-id="b31f5-594">Guid</span><span class="sxs-lookup"><span data-stu-id="b31f5-594">Guid</span></span>|  
|<span data-ttu-id="b31f5-595">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b31f5-595">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="b31f5-596">Int64</span><span class="sxs-lookup"><span data-stu-id="b31f5-596">Int64</span></span>|  
|<span data-ttu-id="b31f5-597">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b31f5-597">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="b31f5-598">Int64</span><span class="sxs-lookup"><span data-stu-id="b31f5-598">Int64</span></span>|  
|<span data-ttu-id="b31f5-599">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="b31f5-599">NUMERIC_PRECISION</span></span>|<span data-ttu-id="b31f5-600">Int32</span><span class="sxs-lookup"><span data-stu-id="b31f5-600">Int32</span></span>|  
|<span data-ttu-id="b31f5-601">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="b31f5-601">NUMERIC_SCALE</span></span>|<span data-ttu-id="b31f5-602">Int16</span><span class="sxs-lookup"><span data-stu-id="b31f5-602">Int16</span></span>|  
|<span data-ttu-id="b31f5-603">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="b31f5-603">DATETIME_PRECISION</span></span>|<span data-ttu-id="b31f5-604">Int64</span><span class="sxs-lookup"><span data-stu-id="b31f5-604">Int64</span></span>|  
|<span data-ttu-id="b31f5-605">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b31f5-605">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="b31f5-606">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-606">String</span></span>|  
|<span data-ttu-id="b31f5-607">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b31f5-607">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="b31f5-608">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-608">String</span></span>|  
|<span data-ttu-id="b31f5-609">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="b31f5-609">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="b31f5-610">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-610">String</span></span>|  
|<span data-ttu-id="b31f5-611">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b31f5-611">COLLATION_CATALOG</span></span>|<span data-ttu-id="b31f5-612">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-612">String</span></span>|  
|<span data-ttu-id="b31f5-613">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b31f5-613">COLLATION_SCHEMA</span></span>|<span data-ttu-id="b31f5-614">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-614">String</span></span>|  
|<span data-ttu-id="b31f5-615">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="b31f5-615">COLLATION_NAME</span></span>|<span data-ttu-id="b31f5-616">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-616">String</span></span>|  
|<span data-ttu-id="b31f5-617">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b31f5-617">DOMAIN_CATALOG</span></span>|<span data-ttu-id="b31f5-618">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-618">String</span></span>|  
|<span data-ttu-id="b31f5-619">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b31f5-619">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="b31f5-620">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-620">String</span></span>|  
|<span data-ttu-id="b31f5-621">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="b31f5-621">DOMAIN_NAME</span></span>|<span data-ttu-id="b31f5-622">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-622">String</span></span>|  
|<span data-ttu-id="b31f5-623">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="b31f5-623">DESCRIPTION</span></span>|<span data-ttu-id="b31f5-624">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-624">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="b31f5-625">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="b31f5-625">Procedures</span></span>  
  
|<span data-ttu-id="b31f5-626">ColumnName</span><span class="sxs-lookup"><span data-stu-id="b31f5-626">ColumnName</span></span>|<span data-ttu-id="b31f5-627">DataType</span><span class="sxs-lookup"><span data-stu-id="b31f5-627">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b31f5-628">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b31f5-628">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="b31f5-629">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-629">String</span></span>|  
|<span data-ttu-id="b31f5-630">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b31f5-630">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="b31f5-631">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-631">String</span></span>|  
|<span data-ttu-id="b31f5-632">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b31f5-632">PROCEDURE_NAME</span></span>|<span data-ttu-id="b31f5-633">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-633">String</span></span>|  
|<span data-ttu-id="b31f5-634">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b31f5-634">PROCEDURE_TYPE</span></span>|<span data-ttu-id="b31f5-635">Int16</span><span class="sxs-lookup"><span data-stu-id="b31f5-635">Int16</span></span>|  
|<span data-ttu-id="b31f5-636">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="b31f5-636">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="b31f5-637">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-637">String</span></span>|  
|<span data-ttu-id="b31f5-638">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="b31f5-638">DESCRIPTION</span></span>|<span data-ttu-id="b31f5-639">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-639">String</span></span>|  
|<span data-ttu-id="b31f5-640">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="b31f5-640">DATE_CREATED</span></span>|<span data-ttu-id="b31f5-641">DateTime</span><span class="sxs-lookup"><span data-stu-id="b31f5-641">DateTime</span></span>|  
|<span data-ttu-id="b31f5-642">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="b31f5-642">DATE_MODIFIED</span></span>|<span data-ttu-id="b31f5-643">DateTime</span><span class="sxs-lookup"><span data-stu-id="b31f5-643">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="b31f5-644">Görünümler</span><span class="sxs-lookup"><span data-stu-id="b31f5-644">Views</span></span>  
  
|<span data-ttu-id="b31f5-645">ColumnName</span><span class="sxs-lookup"><span data-stu-id="b31f5-645">ColumnName</span></span>|<span data-ttu-id="b31f5-646">DataType</span><span class="sxs-lookup"><span data-stu-id="b31f5-646">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b31f5-647">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b31f5-647">TABLE_CATALOG</span></span>|<span data-ttu-id="b31f5-648">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-648">String</span></span>|  
|<span data-ttu-id="b31f5-649">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b31f5-649">TABLE_SCHEMA</span></span>|<span data-ttu-id="b31f5-650">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-650">String</span></span>|  
|<span data-ttu-id="b31f5-651">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b31f5-651">TABLE_NAME</span></span>|<span data-ttu-id="b31f5-652">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-652">String</span></span>|  
|<span data-ttu-id="b31f5-653">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="b31f5-653">VIEW_DEFINITION</span></span>|<span data-ttu-id="b31f5-654">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-654">String</span></span>|  
|<span data-ttu-id="b31f5-655">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="b31f5-655">CHECK_OPTION</span></span>|<span data-ttu-id="b31f5-656">Boole</span><span class="sxs-lookup"><span data-stu-id="b31f5-656">Boolean</span></span>|  
|<span data-ttu-id="b31f5-657">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="b31f5-657">IS_UPDATABLE</span></span>|<span data-ttu-id="b31f5-658">Boole</span><span class="sxs-lookup"><span data-stu-id="b31f5-658">Boolean</span></span>|  
|<span data-ttu-id="b31f5-659">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="b31f5-659">DESCRIPTION</span></span>|<span data-ttu-id="b31f5-660">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-660">String</span></span>|  
|<span data-ttu-id="b31f5-661">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="b31f5-661">DATE_CREATED</span></span>|<span data-ttu-id="b31f5-662">DateTime</span><span class="sxs-lookup"><span data-stu-id="b31f5-662">DateTime</span></span>|  
|<span data-ttu-id="b31f5-663">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="b31f5-663">DATE_MODIFIED</span></span>|<span data-ttu-id="b31f5-664">DateTime</span><span class="sxs-lookup"><span data-stu-id="b31f5-664">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="b31f5-665">Dizinler</span><span class="sxs-lookup"><span data-stu-id="b31f5-665">Indexes</span></span>  
  
|<span data-ttu-id="b31f5-666">ColumnName</span><span class="sxs-lookup"><span data-stu-id="b31f5-666">ColumnName</span></span>|<span data-ttu-id="b31f5-667">DataType</span><span class="sxs-lookup"><span data-stu-id="b31f5-667">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b31f5-668">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b31f5-668">TABLE_CATALOG</span></span>|<span data-ttu-id="b31f5-669">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-669">String</span></span>|  
|<span data-ttu-id="b31f5-670">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b31f5-670">TABLE_SCHEMA</span></span>|<span data-ttu-id="b31f5-671">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-671">String</span></span>|  
|<span data-ttu-id="b31f5-672">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b31f5-672">TABLE_NAME</span></span>|<span data-ttu-id="b31f5-673">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-673">String</span></span>|  
|<span data-ttu-id="b31f5-674">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b31f5-674">INDEX_CATALOG</span></span>|<span data-ttu-id="b31f5-675">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-675">String</span></span>|  
|<span data-ttu-id="b31f5-676">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b31f5-676">INDEX_SCHEMA</span></span>|<span data-ttu-id="b31f5-677">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-677">String</span></span>|  
|<span data-ttu-id="b31f5-678">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="b31f5-678">INDEX_NAME</span></span>|<span data-ttu-id="b31f5-679">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-679">String</span></span>|  
|<span data-ttu-id="b31f5-680">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="b31f5-680">PRIMARY_KEY</span></span>|<span data-ttu-id="b31f5-681">Boole</span><span class="sxs-lookup"><span data-stu-id="b31f5-681">Boolean</span></span>|  
|<span data-ttu-id="b31f5-682">EŞI</span><span class="sxs-lookup"><span data-stu-id="b31f5-682">UNIQUE</span></span>|<span data-ttu-id="b31f5-683">Boole</span><span class="sxs-lookup"><span data-stu-id="b31f5-683">Boolean</span></span>|  
|<span data-ttu-id="b31f5-684">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="b31f5-684">CLUSTERED</span></span>|<span data-ttu-id="b31f5-685">Boole</span><span class="sxs-lookup"><span data-stu-id="b31f5-685">Boolean</span></span>|  
|<span data-ttu-id="b31f5-686">TÜR</span><span class="sxs-lookup"><span data-stu-id="b31f5-686">TYPE</span></span>|<span data-ttu-id="b31f5-687">Int32</span><span class="sxs-lookup"><span data-stu-id="b31f5-687">Int32</span></span>|  
|<span data-ttu-id="b31f5-688">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="b31f5-688">FILL_FACTOR</span></span>|<span data-ttu-id="b31f5-689">Int32</span><span class="sxs-lookup"><span data-stu-id="b31f5-689">Int32</span></span>|  
|<span data-ttu-id="b31f5-690">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="b31f5-690">INITIAL_SIZE</span></span>|<span data-ttu-id="b31f5-691">Int32</span><span class="sxs-lookup"><span data-stu-id="b31f5-691">Int32</span></span>|  
|<span data-ttu-id="b31f5-692">NULLS</span><span class="sxs-lookup"><span data-stu-id="b31f5-692">NULLS</span></span>|<span data-ttu-id="b31f5-693">Int32</span><span class="sxs-lookup"><span data-stu-id="b31f5-693">Int32</span></span>|  
|<span data-ttu-id="b31f5-694">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="b31f5-694">SORT_BOOKMARKS</span></span>|<span data-ttu-id="b31f5-695">Boole</span><span class="sxs-lookup"><span data-stu-id="b31f5-695">Boolean</span></span>|  
|<span data-ttu-id="b31f5-696">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="b31f5-696">AUTO_UPDATE</span></span>|<span data-ttu-id="b31f5-697">Boole</span><span class="sxs-lookup"><span data-stu-id="b31f5-697">Boolean</span></span>|  
|<span data-ttu-id="b31f5-698">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="b31f5-698">NULL_COLLATION</span></span>|<span data-ttu-id="b31f5-699">Int32</span><span class="sxs-lookup"><span data-stu-id="b31f5-699">Int32</span></span>|  
|<span data-ttu-id="b31f5-700">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b31f5-700">ORDINAL_POSITION</span></span>|<span data-ttu-id="b31f5-701">Int64</span><span class="sxs-lookup"><span data-stu-id="b31f5-701">Int64</span></span>|  
|<span data-ttu-id="b31f5-702">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b31f5-702">COLUMN_NAME</span></span>|<span data-ttu-id="b31f5-703">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-703">String</span></span>|  
|<span data-ttu-id="b31f5-704">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="b31f5-704">COLUMN_GUID</span></span>|<span data-ttu-id="b31f5-705">Guid</span><span class="sxs-lookup"><span data-stu-id="b31f5-705">Guid</span></span>|  
|<span data-ttu-id="b31f5-706">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="b31f5-706">COLUMN_PROPID</span></span>|<span data-ttu-id="b31f5-707">Int64</span><span class="sxs-lookup"><span data-stu-id="b31f5-707">Int64</span></span>|  
|<span data-ttu-id="b31f5-708">MEDIĞINDEN</span><span class="sxs-lookup"><span data-stu-id="b31f5-708">COLLATION</span></span>|<span data-ttu-id="b31f5-709">Int16</span><span class="sxs-lookup"><span data-stu-id="b31f5-709">Int16</span></span>|  
|<span data-ttu-id="b31f5-710">ITE</span><span class="sxs-lookup"><span data-stu-id="b31f5-710">CARDINALITY</span></span>|<span data-ttu-id="b31f5-711">Ondalık</span><span class="sxs-lookup"><span data-stu-id="b31f5-711">Decimal</span></span>|  
|<span data-ttu-id="b31f5-712">SAYFALARı</span><span class="sxs-lookup"><span data-stu-id="b31f5-712">PAGES</span></span>|<span data-ttu-id="b31f5-713">Int32</span><span class="sxs-lookup"><span data-stu-id="b31f5-713">Int32</span></span>|  
|<span data-ttu-id="b31f5-714">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="b31f5-714">FILTER_CONDITION</span></span>|<span data-ttu-id="b31f5-715">Dize</span><span class="sxs-lookup"><span data-stu-id="b31f5-715">String</span></span>|  
|<span data-ttu-id="b31f5-716">ILMIŞTIR</span><span class="sxs-lookup"><span data-stu-id="b31f5-716">INTEGRATED</span></span>|<span data-ttu-id="b31f5-717">Boole</span><span class="sxs-lookup"><span data-stu-id="b31f5-717">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b31f5-718">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b31f5-718">See also</span></span>

- [<span data-ttu-id="b31f5-719">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b31f5-719">ADO.NET Overview</span></span>](ado-net-overview.md)
