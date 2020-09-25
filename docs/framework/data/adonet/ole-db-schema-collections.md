---
title: OLE DB Şema Koleksiyonları
ms.date: 03/30/2017
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
ms.openlocfilehash: 90899a123b3dafcd47a50ef8f6eb003938b22a03
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186945"
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="a1316-102">OLE DB Şema Koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="a1316-102">OLE DB Schema Collections</span></span>

<span data-ttu-id="a1316-103">Bu bölümde Microsoft SQL Server, Oracle ve Microsoft Jet için OLE DB sağlayıcıları için şema koleksiyonu desteği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a1316-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="a1316-104">Microsoft SQL Server OLE DB sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="a1316-104">Microsoft SQL Server OLE DB Provider</span></span>  

 <span data-ttu-id="a1316-105">Microsoft SQL Server OLE DB sürücü, ortak şema koleksiyonlarına ek olarak aşağıdaki belirli şema koleksiyonlarını destekler:</span><span class="sxs-lookup"><span data-stu-id="a1316-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="a1316-106">Tablolar</span><span class="sxs-lookup"><span data-stu-id="a1316-106">Tables</span></span>  
  
- <span data-ttu-id="a1316-107">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="a1316-107">Columns</span></span>  
  
- <span data-ttu-id="a1316-108">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="a1316-108">Procedures</span></span>  
  
- <span data-ttu-id="a1316-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="a1316-109">ProcedureParameters</span></span>  
  
- <span data-ttu-id="a1316-110">Katalog</span><span class="sxs-lookup"><span data-stu-id="a1316-110">Catalog</span></span>  
  
- <span data-ttu-id="a1316-111">Dizinler</span><span class="sxs-lookup"><span data-stu-id="a1316-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="a1316-112">Tablolar</span><span class="sxs-lookup"><span data-stu-id="a1316-112">Tables</span></span>  
  
|<span data-ttu-id="a1316-113">ColumnName</span><span class="sxs-lookup"><span data-stu-id="a1316-113">ColumnName</span></span>|<span data-ttu-id="a1316-114">DataType</span><span class="sxs-lookup"><span data-stu-id="a1316-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="a1316-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a1316-115">TABLE_CATALOG</span></span>|<span data-ttu-id="a1316-116">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-116">String</span></span>|  
|<span data-ttu-id="a1316-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a1316-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="a1316-118">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-118">String</span></span>|  
|<span data-ttu-id="a1316-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="a1316-119">TABLE_NAME</span></span>|<span data-ttu-id="a1316-120">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-120">String</span></span>|  
|<span data-ttu-id="a1316-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="a1316-121">TABLE_TYPE</span></span>|<span data-ttu-id="a1316-122">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-122">String</span></span>|  
|<span data-ttu-id="a1316-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="a1316-123">TABLE_GUID</span></span>|<span data-ttu-id="a1316-124">Guid</span><span class="sxs-lookup"><span data-stu-id="a1316-124">Guid</span></span>|  
|<span data-ttu-id="a1316-125">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="a1316-125">DESCRIPTION</span></span>|<span data-ttu-id="a1316-126">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-126">String</span></span>|  
|<span data-ttu-id="a1316-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="a1316-127">TABLE_PROPID</span></span>|<span data-ttu-id="a1316-128">Int64</span><span class="sxs-lookup"><span data-stu-id="a1316-128">Int64</span></span>|  
|<span data-ttu-id="a1316-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="a1316-129">DATE_CREATED</span></span>|<span data-ttu-id="a1316-130">DateTime</span><span class="sxs-lookup"><span data-stu-id="a1316-130">DateTime</span></span>|  
|<span data-ttu-id="a1316-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="a1316-131">DATE_MODIFIED</span></span>|<span data-ttu-id="a1316-132">DateTime</span><span class="sxs-lookup"><span data-stu-id="a1316-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="a1316-133">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="a1316-133">Columns</span></span>  
  
|<span data-ttu-id="a1316-134">ColumnName</span><span class="sxs-lookup"><span data-stu-id="a1316-134">ColumnName</span></span>|<span data-ttu-id="a1316-135">DataType</span><span class="sxs-lookup"><span data-stu-id="a1316-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="a1316-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a1316-136">TABLE_CATALOG</span></span>|<span data-ttu-id="a1316-137">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-137">String</span></span>|  
|<span data-ttu-id="a1316-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a1316-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="a1316-139">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-139">String</span></span>|  
|<span data-ttu-id="a1316-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="a1316-140">TABLE_NAME</span></span>|<span data-ttu-id="a1316-141">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-141">String</span></span>|  
|<span data-ttu-id="a1316-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="a1316-142">COLUMN_NAME</span></span>|<span data-ttu-id="a1316-143">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-143">String</span></span>|  
|<span data-ttu-id="a1316-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="a1316-144">COLUMN_GUID</span></span>|<span data-ttu-id="a1316-145">Guid</span><span class="sxs-lookup"><span data-stu-id="a1316-145">Guid</span></span>|  
|<span data-ttu-id="a1316-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="a1316-146">COLUMN_PROPID</span></span>|<span data-ttu-id="a1316-147">Int64</span><span class="sxs-lookup"><span data-stu-id="a1316-147">Int64</span></span>|  
|<span data-ttu-id="a1316-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="a1316-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="a1316-149">Int64</span><span class="sxs-lookup"><span data-stu-id="a1316-149">Int64</span></span>|  
|<span data-ttu-id="a1316-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="a1316-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="a1316-151">Boole</span><span class="sxs-lookup"><span data-stu-id="a1316-151">Boolean</span></span>|  
|<span data-ttu-id="a1316-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="a1316-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="a1316-153">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-153">String</span></span>|  
|<span data-ttu-id="a1316-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="a1316-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="a1316-155">Int64</span><span class="sxs-lookup"><span data-stu-id="a1316-155">Int64</span></span>|  
|<span data-ttu-id="a1316-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="a1316-156">IS_NULLABLE</span></span>|<span data-ttu-id="a1316-157">Boole</span><span class="sxs-lookup"><span data-stu-id="a1316-157">Boolean</span></span>|  
|<span data-ttu-id="a1316-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="a1316-158">DATA_TYPE</span></span>|<span data-ttu-id="a1316-159">Int32</span><span class="sxs-lookup"><span data-stu-id="a1316-159">Int32</span></span>|  
|<span data-ttu-id="a1316-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="a1316-160">TYPE_GUID</span></span>|<span data-ttu-id="a1316-161">Guid</span><span class="sxs-lookup"><span data-stu-id="a1316-161">Guid</span></span>|  
|<span data-ttu-id="a1316-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="a1316-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="a1316-163">Int64</span><span class="sxs-lookup"><span data-stu-id="a1316-163">Int64</span></span>|  
|<span data-ttu-id="a1316-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="a1316-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="a1316-165">Int64</span><span class="sxs-lookup"><span data-stu-id="a1316-165">Int64</span></span>|  
|<span data-ttu-id="a1316-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="a1316-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="a1316-167">Int32</span><span class="sxs-lookup"><span data-stu-id="a1316-167">Int32</span></span>|  
|<span data-ttu-id="a1316-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="a1316-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="a1316-169">Int16</span><span class="sxs-lookup"><span data-stu-id="a1316-169">Int16</span></span>|  
|<span data-ttu-id="a1316-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="a1316-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="a1316-171">Int64</span><span class="sxs-lookup"><span data-stu-id="a1316-171">Int64</span></span>|  
|<span data-ttu-id="a1316-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a1316-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="a1316-173">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-173">String</span></span>|  
|<span data-ttu-id="a1316-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a1316-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="a1316-175">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-175">String</span></span>|  
|<span data-ttu-id="a1316-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="a1316-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="a1316-177">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-177">String</span></span>|  
|<span data-ttu-id="a1316-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a1316-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="a1316-179">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-179">String</span></span>|  
|<span data-ttu-id="a1316-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a1316-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="a1316-181">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-181">String</span></span>|  
|<span data-ttu-id="a1316-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="a1316-182">COLLATION_NAME</span></span>|<span data-ttu-id="a1316-183">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-183">String</span></span>|  
|<span data-ttu-id="a1316-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a1316-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="a1316-185">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-185">String</span></span>|  
|<span data-ttu-id="a1316-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a1316-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="a1316-187">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-187">String</span></span>|  
|<span data-ttu-id="a1316-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="a1316-188">DOMAIN_NAME</span></span>|<span data-ttu-id="a1316-189">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-189">String</span></span>|  
|<span data-ttu-id="a1316-190">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="a1316-190">DESCRIPTION</span></span>|<span data-ttu-id="a1316-191">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-191">String</span></span>|  
|<span data-ttu-id="a1316-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="a1316-192">COLUMN_LCID</span></span>|<span data-ttu-id="a1316-193">Int32</span><span class="sxs-lookup"><span data-stu-id="a1316-193">Int32</span></span>|  
|<span data-ttu-id="a1316-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="a1316-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="a1316-195">Int32</span><span class="sxs-lookup"><span data-stu-id="a1316-195">Int32</span></span>|  
|<span data-ttu-id="a1316-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="a1316-196">COLUMN_SORTID</span></span>|<span data-ttu-id="a1316-197">Int32</span><span class="sxs-lookup"><span data-stu-id="a1316-197">Int32</span></span>|  
|<span data-ttu-id="a1316-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="a1316-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="a1316-199">Byte []</span><span class="sxs-lookup"><span data-stu-id="a1316-199">Byte[]</span></span>|  
|<span data-ttu-id="a1316-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="a1316-200">IS_COMPUTED</span></span>|<span data-ttu-id="a1316-201">Boole</span><span class="sxs-lookup"><span data-stu-id="a1316-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="a1316-202">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="a1316-202">Procedures</span></span>  
  
|<span data-ttu-id="a1316-203">ColumnName</span><span class="sxs-lookup"><span data-stu-id="a1316-203">ColumnName</span></span>|<span data-ttu-id="a1316-204">DataType</span><span class="sxs-lookup"><span data-stu-id="a1316-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="a1316-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a1316-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="a1316-206">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-206">String</span></span>|  
|<span data-ttu-id="a1316-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a1316-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="a1316-208">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-208">String</span></span>|  
|<span data-ttu-id="a1316-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="a1316-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="a1316-210">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-210">String</span></span>|  
|<span data-ttu-id="a1316-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="a1316-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="a1316-212">Int16</span><span class="sxs-lookup"><span data-stu-id="a1316-212">Int16</span></span>|  
|<span data-ttu-id="a1316-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="a1316-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="a1316-214">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-214">String</span></span>|  
|<span data-ttu-id="a1316-215">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="a1316-215">DESCRIPTION</span></span>|<span data-ttu-id="a1316-216">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-216">String</span></span>|  
|<span data-ttu-id="a1316-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="a1316-217">DATE_CREATED</span></span>|<span data-ttu-id="a1316-218">DateTime</span><span class="sxs-lookup"><span data-stu-id="a1316-218">DateTime</span></span>|  
|<span data-ttu-id="a1316-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="a1316-219">DATE_MODIFIED</span></span>|<span data-ttu-id="a1316-220">DateTime</span><span class="sxs-lookup"><span data-stu-id="a1316-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="a1316-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="a1316-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="a1316-222">ColumnName</span><span class="sxs-lookup"><span data-stu-id="a1316-222">ColumnName</span></span>|<span data-ttu-id="a1316-223">DataType</span><span class="sxs-lookup"><span data-stu-id="a1316-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="a1316-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a1316-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="a1316-225">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-225">String</span></span>|  
|<span data-ttu-id="a1316-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a1316-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="a1316-227">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-227">String</span></span>|  
|<span data-ttu-id="a1316-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="a1316-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="a1316-229">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-229">String</span></span>|  
|<span data-ttu-id="a1316-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="a1316-230">PARAMETER_NAME</span></span>|<span data-ttu-id="a1316-231">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-231">String</span></span>|  
|<span data-ttu-id="a1316-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="a1316-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="a1316-233">Int32</span><span class="sxs-lookup"><span data-stu-id="a1316-233">Int32</span></span>|  
|<span data-ttu-id="a1316-234">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="a1316-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="a1316-235">Int32</span><span class="sxs-lookup"><span data-stu-id="a1316-235">Int32</span></span>|  
|<span data-ttu-id="a1316-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="a1316-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="a1316-237">Boole</span><span class="sxs-lookup"><span data-stu-id="a1316-237">Boolean</span></span>|  
|<span data-ttu-id="a1316-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="a1316-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="a1316-239">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-239">String</span></span>|  
|<span data-ttu-id="a1316-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="a1316-240">IS_NULLABLE</span></span>|<span data-ttu-id="a1316-241">Boole</span><span class="sxs-lookup"><span data-stu-id="a1316-241">Boolean</span></span>|  
|<span data-ttu-id="a1316-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="a1316-242">DATA_TYPE</span></span>|<span data-ttu-id="a1316-243">Int32</span><span class="sxs-lookup"><span data-stu-id="a1316-243">Int32</span></span>|  
|<span data-ttu-id="a1316-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="a1316-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="a1316-245">Int64</span><span class="sxs-lookup"><span data-stu-id="a1316-245">Int64</span></span>|  
|<span data-ttu-id="a1316-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="a1316-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="a1316-247">Int64</span><span class="sxs-lookup"><span data-stu-id="a1316-247">Int64</span></span>|  
|<span data-ttu-id="a1316-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="a1316-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="a1316-249">Int32</span><span class="sxs-lookup"><span data-stu-id="a1316-249">Int32</span></span>|  
|<span data-ttu-id="a1316-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="a1316-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="a1316-251">Int16</span><span class="sxs-lookup"><span data-stu-id="a1316-251">Int16</span></span>|  
|<span data-ttu-id="a1316-252">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="a1316-252">DESCRIPTION</span></span>|<span data-ttu-id="a1316-253">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-253">String</span></span>|  
|<span data-ttu-id="a1316-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="a1316-254">TYPE_NAME</span></span>|<span data-ttu-id="a1316-255">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-255">String</span></span>|  
|<span data-ttu-id="a1316-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="a1316-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="a1316-257">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="a1316-258">Katalog</span><span class="sxs-lookup"><span data-stu-id="a1316-258">Catalog</span></span>  
  
|<span data-ttu-id="a1316-259">ColumnName</span><span class="sxs-lookup"><span data-stu-id="a1316-259">ColumnName</span></span>|<span data-ttu-id="a1316-260">DataType</span><span class="sxs-lookup"><span data-stu-id="a1316-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="a1316-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="a1316-261">CATALOG_NAME</span></span>|<span data-ttu-id="a1316-262">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-262">String</span></span>|  
|<span data-ttu-id="a1316-263">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="a1316-263">DESCRIPTION</span></span>|<span data-ttu-id="a1316-264">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="a1316-265">Dizinler</span><span class="sxs-lookup"><span data-stu-id="a1316-265">Indexes</span></span>  
  
|<span data-ttu-id="a1316-266">ColumnName</span><span class="sxs-lookup"><span data-stu-id="a1316-266">ColumnName</span></span>|<span data-ttu-id="a1316-267">DataType</span><span class="sxs-lookup"><span data-stu-id="a1316-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="a1316-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a1316-268">TABLE_CATALOG</span></span>|<span data-ttu-id="a1316-269">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-269">String</span></span>|  
|<span data-ttu-id="a1316-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a1316-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="a1316-271">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-271">String</span></span>|  
|<span data-ttu-id="a1316-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="a1316-272">TABLE_NAME</span></span>|<span data-ttu-id="a1316-273">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-273">String</span></span>|  
|<span data-ttu-id="a1316-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a1316-274">INDEX_CATALOG</span></span>|<span data-ttu-id="a1316-275">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-275">String</span></span>|  
|<span data-ttu-id="a1316-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a1316-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="a1316-277">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-277">String</span></span>|  
|<span data-ttu-id="a1316-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="a1316-278">INDEX_NAME</span></span>|<span data-ttu-id="a1316-279">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-279">String</span></span>|  
|<span data-ttu-id="a1316-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="a1316-280">PRIMARY_KEY</span></span>|<span data-ttu-id="a1316-281">Boole</span><span class="sxs-lookup"><span data-stu-id="a1316-281">Boolean</span></span>|  
|<span data-ttu-id="a1316-282">EŞI</span><span class="sxs-lookup"><span data-stu-id="a1316-282">UNIQUE</span></span>|<span data-ttu-id="a1316-283">Boole</span><span class="sxs-lookup"><span data-stu-id="a1316-283">Boolean</span></span>|  
|<span data-ttu-id="a1316-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="a1316-284">CLUSTERED</span></span>|<span data-ttu-id="a1316-285">Boole</span><span class="sxs-lookup"><span data-stu-id="a1316-285">Boolean</span></span>|  
|<span data-ttu-id="a1316-286">TÜR</span><span class="sxs-lookup"><span data-stu-id="a1316-286">TYPE</span></span>|<span data-ttu-id="a1316-287">Int32</span><span class="sxs-lookup"><span data-stu-id="a1316-287">Int32</span></span>|  
|<span data-ttu-id="a1316-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="a1316-288">FILL_FACTOR</span></span>|<span data-ttu-id="a1316-289">Int32</span><span class="sxs-lookup"><span data-stu-id="a1316-289">Int32</span></span>|  
|<span data-ttu-id="a1316-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="a1316-290">INITIAL_SIZE</span></span>|<span data-ttu-id="a1316-291">Int32</span><span class="sxs-lookup"><span data-stu-id="a1316-291">Int32</span></span>|  
|<span data-ttu-id="a1316-292">NULLS</span><span class="sxs-lookup"><span data-stu-id="a1316-292">NULLS</span></span>|<span data-ttu-id="a1316-293">Int32</span><span class="sxs-lookup"><span data-stu-id="a1316-293">Int32</span></span>|  
|<span data-ttu-id="a1316-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="a1316-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="a1316-295">Boole</span><span class="sxs-lookup"><span data-stu-id="a1316-295">Boolean</span></span>|  
|<span data-ttu-id="a1316-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="a1316-296">AUTO_UPDATE</span></span>|<span data-ttu-id="a1316-297">Boole</span><span class="sxs-lookup"><span data-stu-id="a1316-297">Boolean</span></span>|  
|<span data-ttu-id="a1316-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="a1316-298">NULL_COLLATION</span></span>|<span data-ttu-id="a1316-299">Int32</span><span class="sxs-lookup"><span data-stu-id="a1316-299">Int32</span></span>|  
|<span data-ttu-id="a1316-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="a1316-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="a1316-301">Int64</span><span class="sxs-lookup"><span data-stu-id="a1316-301">Int64</span></span>|  
|<span data-ttu-id="a1316-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="a1316-302">COLUMN_NAME</span></span>|<span data-ttu-id="a1316-303">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-303">String</span></span>|  
|<span data-ttu-id="a1316-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="a1316-304">COLUMN_GUID</span></span>|<span data-ttu-id="a1316-305">Guid</span><span class="sxs-lookup"><span data-stu-id="a1316-305">Guid</span></span>|  
|<span data-ttu-id="a1316-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="a1316-306">COLUMN_PROPID</span></span>|<span data-ttu-id="a1316-307">Int64</span><span class="sxs-lookup"><span data-stu-id="a1316-307">Int64</span></span>|  
|<span data-ttu-id="a1316-308">MEDIĞINDEN</span><span class="sxs-lookup"><span data-stu-id="a1316-308">COLLATION</span></span>|<span data-ttu-id="a1316-309">Int16</span><span class="sxs-lookup"><span data-stu-id="a1316-309">Int16</span></span>|  
|<span data-ttu-id="a1316-310">ITE</span><span class="sxs-lookup"><span data-stu-id="a1316-310">CARDINALITY</span></span>|<span data-ttu-id="a1316-311">Ondalık</span><span class="sxs-lookup"><span data-stu-id="a1316-311">Decimal</span></span>|  
|<span data-ttu-id="a1316-312">SAYFALARı</span><span class="sxs-lookup"><span data-stu-id="a1316-312">PAGES</span></span>|<span data-ttu-id="a1316-313">Int32</span><span class="sxs-lookup"><span data-stu-id="a1316-313">Int32</span></span>|  
|<span data-ttu-id="a1316-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="a1316-314">FILTER_CONDITION</span></span>|<span data-ttu-id="a1316-315">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-315">String</span></span>|  
|<span data-ttu-id="a1316-316">ILMIŞTIR</span><span class="sxs-lookup"><span data-stu-id="a1316-316">INTEGRATED</span></span>|<span data-ttu-id="a1316-317">Boole</span><span class="sxs-lookup"><span data-stu-id="a1316-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="a1316-318">Microsoft Oracle OLE DB sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="a1316-318">Microsoft Oracle OLE DB Provider</span></span>  

 <span data-ttu-id="a1316-319">Microsoft Oracle OLE DB sürücüsü, ortak şema koleksiyonlarına ek olarak aşağıdaki belirli şema koleksiyonlarını destekler:</span><span class="sxs-lookup"><span data-stu-id="a1316-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="a1316-320">Tablolar</span><span class="sxs-lookup"><span data-stu-id="a1316-320">Tables</span></span>  
  
- <span data-ttu-id="a1316-321">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="a1316-321">Columns</span></span>  
  
- <span data-ttu-id="a1316-322">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="a1316-322">Procedures</span></span>  
  
- <span data-ttu-id="a1316-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="a1316-323">ProcedureColumns</span></span>  
  
- <span data-ttu-id="a1316-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="a1316-324">ProcedureParameters</span></span>  
  
- <span data-ttu-id="a1316-325">Görünümler</span><span class="sxs-lookup"><span data-stu-id="a1316-325">Views</span></span>  
  
- <span data-ttu-id="a1316-326">Dizinler</span><span class="sxs-lookup"><span data-stu-id="a1316-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="a1316-327">Tablolar</span><span class="sxs-lookup"><span data-stu-id="a1316-327">Tables</span></span>  
  
|<span data-ttu-id="a1316-328">ColumnName</span><span class="sxs-lookup"><span data-stu-id="a1316-328">ColumnName</span></span>|<span data-ttu-id="a1316-329">DataType</span><span class="sxs-lookup"><span data-stu-id="a1316-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="a1316-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a1316-330">TABLE_CATALOG</span></span>|<span data-ttu-id="a1316-331">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-331">String</span></span>|  
|<span data-ttu-id="a1316-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a1316-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="a1316-333">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-333">String</span></span>|  
|<span data-ttu-id="a1316-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="a1316-334">TABLE_NAME</span></span>|<span data-ttu-id="a1316-335">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-335">String</span></span>|  
|<span data-ttu-id="a1316-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="a1316-336">TABLE_TYPE</span></span>|<span data-ttu-id="a1316-337">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-337">String</span></span>|  
|<span data-ttu-id="a1316-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="a1316-338">TABLE_GUID</span></span>|<span data-ttu-id="a1316-339">Guid</span><span class="sxs-lookup"><span data-stu-id="a1316-339">Guid</span></span>|  
|<span data-ttu-id="a1316-340">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="a1316-340">DESCRIPTION</span></span>|<span data-ttu-id="a1316-341">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-341">String</span></span>|  
|<span data-ttu-id="a1316-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="a1316-342">TABLE_PROPID</span></span>|<span data-ttu-id="a1316-343">Int64</span><span class="sxs-lookup"><span data-stu-id="a1316-343">Int64</span></span>|  
|<span data-ttu-id="a1316-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="a1316-344">DATE_CREATED</span></span>|<span data-ttu-id="a1316-345">DateTime</span><span class="sxs-lookup"><span data-stu-id="a1316-345">DateTime</span></span>|  
|<span data-ttu-id="a1316-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="a1316-346">DATE_MODIFIED</span></span>|<span data-ttu-id="a1316-347">DateTime</span><span class="sxs-lookup"><span data-stu-id="a1316-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="a1316-348">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="a1316-348">Columns</span></span>  
  
|<span data-ttu-id="a1316-349">ColumnName</span><span class="sxs-lookup"><span data-stu-id="a1316-349">ColumnName</span></span>|<span data-ttu-id="a1316-350">DataType</span><span class="sxs-lookup"><span data-stu-id="a1316-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="a1316-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a1316-351">TABLE_CATALOG</span></span>|<span data-ttu-id="a1316-352">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-352">String</span></span>|  
|<span data-ttu-id="a1316-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a1316-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="a1316-354">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-354">String</span></span>|  
|<span data-ttu-id="a1316-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="a1316-355">TABLE_NAME</span></span>|<span data-ttu-id="a1316-356">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-356">String</span></span>|  
|<span data-ttu-id="a1316-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="a1316-357">COLUMN_NAME</span></span>|<span data-ttu-id="a1316-358">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-358">String</span></span>|  
|<span data-ttu-id="a1316-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="a1316-359">COLUMN_GUID</span></span>|<span data-ttu-id="a1316-360">Guid</span><span class="sxs-lookup"><span data-stu-id="a1316-360">Guid</span></span>|  
|<span data-ttu-id="a1316-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="a1316-361">COLUMN_PROPID</span></span>|<span data-ttu-id="a1316-362">Int64</span><span class="sxs-lookup"><span data-stu-id="a1316-362">Int64</span></span>|  
|<span data-ttu-id="a1316-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="a1316-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="a1316-364">Int64</span><span class="sxs-lookup"><span data-stu-id="a1316-364">Int64</span></span>|  
|<span data-ttu-id="a1316-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="a1316-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="a1316-366">Boole</span><span class="sxs-lookup"><span data-stu-id="a1316-366">Boolean</span></span>|  
|<span data-ttu-id="a1316-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="a1316-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="a1316-368">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-368">String</span></span>|  
|<span data-ttu-id="a1316-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="a1316-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="a1316-370">Int64</span><span class="sxs-lookup"><span data-stu-id="a1316-370">Int64</span></span>|  
|<span data-ttu-id="a1316-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="a1316-371">IS_NULLABLE</span></span>|<span data-ttu-id="a1316-372">Boole</span><span class="sxs-lookup"><span data-stu-id="a1316-372">Boolean</span></span>|  
|<span data-ttu-id="a1316-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="a1316-373">DATA_TYPE</span></span>|<span data-ttu-id="a1316-374">Int32</span><span class="sxs-lookup"><span data-stu-id="a1316-374">Int32</span></span>|  
|<span data-ttu-id="a1316-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="a1316-375">TYPE_GUID</span></span>|<span data-ttu-id="a1316-376">Guid</span><span class="sxs-lookup"><span data-stu-id="a1316-376">Guid</span></span>|  
|<span data-ttu-id="a1316-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="a1316-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="a1316-378">Int64</span><span class="sxs-lookup"><span data-stu-id="a1316-378">Int64</span></span>|  
|<span data-ttu-id="a1316-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="a1316-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="a1316-380">Int64</span><span class="sxs-lookup"><span data-stu-id="a1316-380">Int64</span></span>|  
|<span data-ttu-id="a1316-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="a1316-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="a1316-382">Int32</span><span class="sxs-lookup"><span data-stu-id="a1316-382">Int32</span></span>|  
|<span data-ttu-id="a1316-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="a1316-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="a1316-384">Int16</span><span class="sxs-lookup"><span data-stu-id="a1316-384">Int16</span></span>|  
|<span data-ttu-id="a1316-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="a1316-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="a1316-386">Int64</span><span class="sxs-lookup"><span data-stu-id="a1316-386">Int64</span></span>|  
|<span data-ttu-id="a1316-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a1316-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="a1316-388">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-388">String</span></span>|  
|<span data-ttu-id="a1316-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a1316-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="a1316-390">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-390">String</span></span>|  
|<span data-ttu-id="a1316-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="a1316-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="a1316-392">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-392">String</span></span>|  
|<span data-ttu-id="a1316-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a1316-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="a1316-394">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-394">String</span></span>|  
|<span data-ttu-id="a1316-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a1316-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="a1316-396">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-396">String</span></span>|  
|<span data-ttu-id="a1316-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="a1316-397">COLLATION_NAME</span></span>|<span data-ttu-id="a1316-398">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-398">String</span></span>|  
|<span data-ttu-id="a1316-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a1316-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="a1316-400">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-400">String</span></span>|  
|<span data-ttu-id="a1316-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a1316-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="a1316-402">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-402">String</span></span>|  
|<span data-ttu-id="a1316-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="a1316-403">DOMAIN_NAME</span></span>|<span data-ttu-id="a1316-404">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-404">String</span></span>|  
|<span data-ttu-id="a1316-405">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="a1316-405">DESCRIPTION</span></span>|<span data-ttu-id="a1316-406">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="a1316-407">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="a1316-407">Procedures</span></span>  
  
|<span data-ttu-id="a1316-408">ColumnName</span><span class="sxs-lookup"><span data-stu-id="a1316-408">ColumnName</span></span>|<span data-ttu-id="a1316-409">DataType</span><span class="sxs-lookup"><span data-stu-id="a1316-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="a1316-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a1316-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="a1316-411">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-411">String</span></span>|  
|<span data-ttu-id="a1316-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a1316-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="a1316-413">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-413">String</span></span>|  
|<span data-ttu-id="a1316-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="a1316-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="a1316-415">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-415">String</span></span>|  
|<span data-ttu-id="a1316-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="a1316-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="a1316-417">Int16</span><span class="sxs-lookup"><span data-stu-id="a1316-417">Int16</span></span>|  
|<span data-ttu-id="a1316-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="a1316-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="a1316-419">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-419">String</span></span>|  
|<span data-ttu-id="a1316-420">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="a1316-420">DESCRIPTION</span></span>|<span data-ttu-id="a1316-421">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-421">String</span></span>|  
|<span data-ttu-id="a1316-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="a1316-422">DATE_CREATED</span></span>|<span data-ttu-id="a1316-423">DateTime</span><span class="sxs-lookup"><span data-stu-id="a1316-423">DateTime</span></span>|  
|<span data-ttu-id="a1316-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="a1316-424">DATE_MODIFIED</span></span>|<span data-ttu-id="a1316-425">DateTime</span><span class="sxs-lookup"><span data-stu-id="a1316-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="a1316-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="a1316-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="a1316-427">ColumnName</span><span class="sxs-lookup"><span data-stu-id="a1316-427">ColumnName</span></span>|<span data-ttu-id="a1316-428">DataType</span><span class="sxs-lookup"><span data-stu-id="a1316-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="a1316-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a1316-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="a1316-430">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-430">String</span></span>|  
|<span data-ttu-id="a1316-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a1316-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="a1316-432">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-432">String</span></span>|  
|<span data-ttu-id="a1316-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="a1316-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="a1316-434">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-434">String</span></span>|  
|<span data-ttu-id="a1316-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="a1316-435">COLUMN_NAME</span></span>|<span data-ttu-id="a1316-436">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-436">String</span></span>|  
|<span data-ttu-id="a1316-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="a1316-437">COLUMN_GUID</span></span>|<span data-ttu-id="a1316-438">Guid</span><span class="sxs-lookup"><span data-stu-id="a1316-438">Guid</span></span>|  
|<span data-ttu-id="a1316-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="a1316-439">COLUMN_PROPID</span></span>|<span data-ttu-id="a1316-440">Int64</span><span class="sxs-lookup"><span data-stu-id="a1316-440">Int64</span></span>|  
|<span data-ttu-id="a1316-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="a1316-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="a1316-442">Int64</span><span class="sxs-lookup"><span data-stu-id="a1316-442">Int64</span></span>|  
|<span data-ttu-id="a1316-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="a1316-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="a1316-444">Int64</span><span class="sxs-lookup"><span data-stu-id="a1316-444">Int64</span></span>|  
|<span data-ttu-id="a1316-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="a1316-445">IS_NULLABLE</span></span>|<span data-ttu-id="a1316-446">Boole</span><span class="sxs-lookup"><span data-stu-id="a1316-446">Boolean</span></span>|  
|<span data-ttu-id="a1316-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="a1316-447">DATA_TYPE</span></span>|<span data-ttu-id="a1316-448">Int32</span><span class="sxs-lookup"><span data-stu-id="a1316-448">Int32</span></span>|  
|<span data-ttu-id="a1316-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="a1316-449">TYPE_GUID</span></span>|<span data-ttu-id="a1316-450">Guid</span><span class="sxs-lookup"><span data-stu-id="a1316-450">Guid</span></span>|  
|<span data-ttu-id="a1316-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="a1316-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="a1316-452">Int64</span><span class="sxs-lookup"><span data-stu-id="a1316-452">Int64</span></span>|  
|<span data-ttu-id="a1316-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="a1316-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="a1316-454">Int64</span><span class="sxs-lookup"><span data-stu-id="a1316-454">Int64</span></span>|  
|<span data-ttu-id="a1316-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="a1316-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="a1316-456">Int32</span><span class="sxs-lookup"><span data-stu-id="a1316-456">Int32</span></span>|  
|<span data-ttu-id="a1316-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="a1316-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="a1316-458">Int16</span><span class="sxs-lookup"><span data-stu-id="a1316-458">Int16</span></span>|  
|<span data-ttu-id="a1316-459">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="a1316-459">DESCRIPTION</span></span>|<span data-ttu-id="a1316-460">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-460">String</span></span>|  
|<span data-ttu-id="a1316-461">YÜKLEMEK</span><span class="sxs-lookup"><span data-stu-id="a1316-461">OVERLOAD</span></span>|<span data-ttu-id="a1316-462">Int16</span><span class="sxs-lookup"><span data-stu-id="a1316-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="a1316-463">Görünümler</span><span class="sxs-lookup"><span data-stu-id="a1316-463">Views</span></span>  
  
|<span data-ttu-id="a1316-464">ColumnName</span><span class="sxs-lookup"><span data-stu-id="a1316-464">ColumnName</span></span>|<span data-ttu-id="a1316-465">DataType</span><span class="sxs-lookup"><span data-stu-id="a1316-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="a1316-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a1316-466">TABLE_CATALOG</span></span>|<span data-ttu-id="a1316-467">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-467">String</span></span>|  
|<span data-ttu-id="a1316-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a1316-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="a1316-469">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-469">String</span></span>|  
|<span data-ttu-id="a1316-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="a1316-470">TABLE_NAME</span></span>|<span data-ttu-id="a1316-471">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-471">String</span></span>|  
|<span data-ttu-id="a1316-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="a1316-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="a1316-473">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-473">String</span></span>|  
|<span data-ttu-id="a1316-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="a1316-474">CHECK_OPTION</span></span>|<span data-ttu-id="a1316-475">Boole</span><span class="sxs-lookup"><span data-stu-id="a1316-475">Boolean</span></span>|  
|<span data-ttu-id="a1316-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="a1316-476">IS_UPDATABLE</span></span>|<span data-ttu-id="a1316-477">Boole</span><span class="sxs-lookup"><span data-stu-id="a1316-477">Boolean</span></span>|  
|<span data-ttu-id="a1316-478">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="a1316-478">DESCRIPTION</span></span>|<span data-ttu-id="a1316-479">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-479">String</span></span>|  
|<span data-ttu-id="a1316-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="a1316-480">DATE_CREATED</span></span>|<span data-ttu-id="a1316-481">DateTime</span><span class="sxs-lookup"><span data-stu-id="a1316-481">DateTime</span></span>|  
|<span data-ttu-id="a1316-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="a1316-482">DATE_MODIFIED</span></span>|<span data-ttu-id="a1316-483">DateTime</span><span class="sxs-lookup"><span data-stu-id="a1316-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="a1316-484">Dizinler</span><span class="sxs-lookup"><span data-stu-id="a1316-484">Indexes</span></span>  
  
|<span data-ttu-id="a1316-485">ColumnName</span><span class="sxs-lookup"><span data-stu-id="a1316-485">ColumnName</span></span>|<span data-ttu-id="a1316-486">DataType</span><span class="sxs-lookup"><span data-stu-id="a1316-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="a1316-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a1316-487">TABLE_CATALOG</span></span>|<span data-ttu-id="a1316-488">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-488">String</span></span>|  
|<span data-ttu-id="a1316-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a1316-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="a1316-490">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-490">String</span></span>|  
|<span data-ttu-id="a1316-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="a1316-491">TABLE_NAME</span></span>|<span data-ttu-id="a1316-492">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-492">String</span></span>|  
|<span data-ttu-id="a1316-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a1316-493">INDEX_CATALOG</span></span>|<span data-ttu-id="a1316-494">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-494">String</span></span>|  
|<span data-ttu-id="a1316-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a1316-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="a1316-496">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-496">String</span></span>|  
|<span data-ttu-id="a1316-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="a1316-497">INDEX_NAME</span></span>|<span data-ttu-id="a1316-498">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-498">String</span></span>|  
|<span data-ttu-id="a1316-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="a1316-499">PRIMARY_KEY</span></span>|<span data-ttu-id="a1316-500">Boole</span><span class="sxs-lookup"><span data-stu-id="a1316-500">Boolean</span></span>|  
|<span data-ttu-id="a1316-501">EŞI</span><span class="sxs-lookup"><span data-stu-id="a1316-501">UNIQUE</span></span>|<span data-ttu-id="a1316-502">Boole</span><span class="sxs-lookup"><span data-stu-id="a1316-502">Boolean</span></span>|  
|<span data-ttu-id="a1316-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="a1316-503">CLUSTERED</span></span>|<span data-ttu-id="a1316-504">Boole</span><span class="sxs-lookup"><span data-stu-id="a1316-504">Boolean</span></span>|  
|<span data-ttu-id="a1316-505">TÜR</span><span class="sxs-lookup"><span data-stu-id="a1316-505">TYPE</span></span>|<span data-ttu-id="a1316-506">Int32</span><span class="sxs-lookup"><span data-stu-id="a1316-506">Int32</span></span>|  
|<span data-ttu-id="a1316-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="a1316-507">FILL_FACTOR</span></span>|<span data-ttu-id="a1316-508">Int32</span><span class="sxs-lookup"><span data-stu-id="a1316-508">Int32</span></span>|  
|<span data-ttu-id="a1316-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="a1316-509">INITIAL_SIZE</span></span>|<span data-ttu-id="a1316-510">Int32</span><span class="sxs-lookup"><span data-stu-id="a1316-510">Int32</span></span>|  
|<span data-ttu-id="a1316-511">NULLS</span><span class="sxs-lookup"><span data-stu-id="a1316-511">NULLS</span></span>|<span data-ttu-id="a1316-512">Int32</span><span class="sxs-lookup"><span data-stu-id="a1316-512">Int32</span></span>|  
|<span data-ttu-id="a1316-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="a1316-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="a1316-514">Boole</span><span class="sxs-lookup"><span data-stu-id="a1316-514">Boolean</span></span>|  
|<span data-ttu-id="a1316-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="a1316-515">AUTO_UPDATE</span></span>|<span data-ttu-id="a1316-516">Boole</span><span class="sxs-lookup"><span data-stu-id="a1316-516">Boolean</span></span>|  
|<span data-ttu-id="a1316-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="a1316-517">NULL_COLLATION</span></span>|<span data-ttu-id="a1316-518">Int32</span><span class="sxs-lookup"><span data-stu-id="a1316-518">Int32</span></span>|  
|<span data-ttu-id="a1316-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="a1316-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="a1316-520">Int64</span><span class="sxs-lookup"><span data-stu-id="a1316-520">Int64</span></span>|  
|<span data-ttu-id="a1316-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="a1316-521">COLUMN_NAME</span></span>|<span data-ttu-id="a1316-522">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-522">String</span></span>|  
|<span data-ttu-id="a1316-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="a1316-523">COLUMN_GUID</span></span>|<span data-ttu-id="a1316-524">Guid</span><span class="sxs-lookup"><span data-stu-id="a1316-524">Guid</span></span>|  
|<span data-ttu-id="a1316-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="a1316-525">COLUMN_PROPID</span></span>|<span data-ttu-id="a1316-526">Int64</span><span class="sxs-lookup"><span data-stu-id="a1316-526">Int64</span></span>|  
|<span data-ttu-id="a1316-527">MEDIĞINDEN</span><span class="sxs-lookup"><span data-stu-id="a1316-527">COLLATION</span></span>|<span data-ttu-id="a1316-528">Int16</span><span class="sxs-lookup"><span data-stu-id="a1316-528">Int16</span></span>|  
|<span data-ttu-id="a1316-529">ITE</span><span class="sxs-lookup"><span data-stu-id="a1316-529">CARDINALITY</span></span>|<span data-ttu-id="a1316-530">Ondalık</span><span class="sxs-lookup"><span data-stu-id="a1316-530">Decimal</span></span>|  
|<span data-ttu-id="a1316-531">SAYFALARı</span><span class="sxs-lookup"><span data-stu-id="a1316-531">PAGES</span></span>|<span data-ttu-id="a1316-532">Int32</span><span class="sxs-lookup"><span data-stu-id="a1316-532">Int32</span></span>|  
|<span data-ttu-id="a1316-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="a1316-533">FILTER_CONDITION</span></span>|<span data-ttu-id="a1316-534">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-534">String</span></span>|  
|<span data-ttu-id="a1316-535">ILMIŞTIR</span><span class="sxs-lookup"><span data-stu-id="a1316-535">INTEGRATED</span></span>|<span data-ttu-id="a1316-536">Boole</span><span class="sxs-lookup"><span data-stu-id="a1316-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="a1316-537">Microsoft Jet OLE DB sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="a1316-537">Microsoft Jet OLE DB Provider</span></span>  

 <span data-ttu-id="a1316-538">Microsoft Jet OLE DB sürücüsü, ortak şema koleksiyonlarına ek olarak aşağıdaki belirli şema koleksiyonlarını destekler:</span><span class="sxs-lookup"><span data-stu-id="a1316-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="a1316-539">Tablolar</span><span class="sxs-lookup"><span data-stu-id="a1316-539">Tables</span></span>  
  
- <span data-ttu-id="a1316-540">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="a1316-540">Columns</span></span>  
  
- <span data-ttu-id="a1316-541">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="a1316-541">Procedures</span></span>  
  
- <span data-ttu-id="a1316-542">Görünümler</span><span class="sxs-lookup"><span data-stu-id="a1316-542">Views</span></span>  
  
- <span data-ttu-id="a1316-543">Dizinler</span><span class="sxs-lookup"><span data-stu-id="a1316-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="a1316-544">Tablolar</span><span class="sxs-lookup"><span data-stu-id="a1316-544">Tables</span></span>  
  
|<span data-ttu-id="a1316-545">ColumnName</span><span class="sxs-lookup"><span data-stu-id="a1316-545">ColumnName</span></span>|<span data-ttu-id="a1316-546">DataType</span><span class="sxs-lookup"><span data-stu-id="a1316-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="a1316-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a1316-547">TABLE_CATALOG</span></span>|<span data-ttu-id="a1316-548">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-548">String</span></span>|  
|<span data-ttu-id="a1316-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a1316-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="a1316-550">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-550">String</span></span>|  
|<span data-ttu-id="a1316-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="a1316-551">TABLE_NAME</span></span>|<span data-ttu-id="a1316-552">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-552">String</span></span>|  
|<span data-ttu-id="a1316-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="a1316-553">TABLE_TYPE</span></span>|<span data-ttu-id="a1316-554">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-554">String</span></span>|  
|<span data-ttu-id="a1316-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="a1316-555">TABLE_GUID</span></span>|<span data-ttu-id="a1316-556">Guid</span><span class="sxs-lookup"><span data-stu-id="a1316-556">Guid</span></span>|  
|<span data-ttu-id="a1316-557">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="a1316-557">DESCRIPTION</span></span>|<span data-ttu-id="a1316-558">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-558">String</span></span>|  
|<span data-ttu-id="a1316-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="a1316-559">TABLE_PROPID</span></span>|<span data-ttu-id="a1316-560">Int64</span><span class="sxs-lookup"><span data-stu-id="a1316-560">Int64</span></span>|  
|<span data-ttu-id="a1316-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="a1316-561">DATE_CREATED</span></span>|<span data-ttu-id="a1316-562">DateTime</span><span class="sxs-lookup"><span data-stu-id="a1316-562">DateTime</span></span>|  
|<span data-ttu-id="a1316-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="a1316-563">DATE_MODIFIED</span></span>|<span data-ttu-id="a1316-564">DateTime</span><span class="sxs-lookup"><span data-stu-id="a1316-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="a1316-565">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="a1316-565">Columns</span></span>  
  
|<span data-ttu-id="a1316-566">ColumnName</span><span class="sxs-lookup"><span data-stu-id="a1316-566">ColumnName</span></span>|<span data-ttu-id="a1316-567">DataType</span><span class="sxs-lookup"><span data-stu-id="a1316-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="a1316-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a1316-568">TABLE_CATALOG</span></span>|<span data-ttu-id="a1316-569">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-569">String</span></span>|  
|<span data-ttu-id="a1316-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a1316-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="a1316-571">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-571">String</span></span>|  
|<span data-ttu-id="a1316-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="a1316-572">TABLE_NAME</span></span>|<span data-ttu-id="a1316-573">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-573">String</span></span>|  
|<span data-ttu-id="a1316-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="a1316-574">COLUMN_NAME</span></span>|<span data-ttu-id="a1316-575">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-575">String</span></span>|  
|<span data-ttu-id="a1316-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="a1316-576">COLUMN_GUID</span></span>|<span data-ttu-id="a1316-577">Guid</span><span class="sxs-lookup"><span data-stu-id="a1316-577">Guid</span></span>|  
|<span data-ttu-id="a1316-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="a1316-578">COLUMN_PROPID</span></span>|<span data-ttu-id="a1316-579">Int64</span><span class="sxs-lookup"><span data-stu-id="a1316-579">Int64</span></span>|  
|<span data-ttu-id="a1316-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="a1316-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="a1316-581">Int64</span><span class="sxs-lookup"><span data-stu-id="a1316-581">Int64</span></span>|  
|<span data-ttu-id="a1316-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="a1316-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="a1316-583">Boole</span><span class="sxs-lookup"><span data-stu-id="a1316-583">Boolean</span></span>|  
|<span data-ttu-id="a1316-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="a1316-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="a1316-585">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-585">String</span></span>|  
|<span data-ttu-id="a1316-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="a1316-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="a1316-587">Int64</span><span class="sxs-lookup"><span data-stu-id="a1316-587">Int64</span></span>|  
|<span data-ttu-id="a1316-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="a1316-588">IS_NULLABLE</span></span>|<span data-ttu-id="a1316-589">Boole</span><span class="sxs-lookup"><span data-stu-id="a1316-589">Boolean</span></span>|  
|<span data-ttu-id="a1316-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="a1316-590">DATA_TYPE</span></span>|<span data-ttu-id="a1316-591">Int32</span><span class="sxs-lookup"><span data-stu-id="a1316-591">Int32</span></span>|  
|<span data-ttu-id="a1316-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="a1316-592">TYPE_GUID</span></span>|<span data-ttu-id="a1316-593">Guid</span><span class="sxs-lookup"><span data-stu-id="a1316-593">Guid</span></span>|  
|<span data-ttu-id="a1316-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="a1316-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="a1316-595">Int64</span><span class="sxs-lookup"><span data-stu-id="a1316-595">Int64</span></span>|  
|<span data-ttu-id="a1316-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="a1316-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="a1316-597">Int64</span><span class="sxs-lookup"><span data-stu-id="a1316-597">Int64</span></span>|  
|<span data-ttu-id="a1316-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="a1316-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="a1316-599">Int32</span><span class="sxs-lookup"><span data-stu-id="a1316-599">Int32</span></span>|  
|<span data-ttu-id="a1316-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="a1316-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="a1316-601">Int16</span><span class="sxs-lookup"><span data-stu-id="a1316-601">Int16</span></span>|  
|<span data-ttu-id="a1316-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="a1316-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="a1316-603">Int64</span><span class="sxs-lookup"><span data-stu-id="a1316-603">Int64</span></span>|  
|<span data-ttu-id="a1316-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a1316-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="a1316-605">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-605">String</span></span>|  
|<span data-ttu-id="a1316-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a1316-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="a1316-607">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-607">String</span></span>|  
|<span data-ttu-id="a1316-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="a1316-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="a1316-609">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-609">String</span></span>|  
|<span data-ttu-id="a1316-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a1316-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="a1316-611">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-611">String</span></span>|  
|<span data-ttu-id="a1316-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a1316-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="a1316-613">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-613">String</span></span>|  
|<span data-ttu-id="a1316-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="a1316-614">COLLATION_NAME</span></span>|<span data-ttu-id="a1316-615">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-615">String</span></span>|  
|<span data-ttu-id="a1316-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a1316-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="a1316-617">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-617">String</span></span>|  
|<span data-ttu-id="a1316-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a1316-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="a1316-619">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-619">String</span></span>|  
|<span data-ttu-id="a1316-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="a1316-620">DOMAIN_NAME</span></span>|<span data-ttu-id="a1316-621">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-621">String</span></span>|  
|<span data-ttu-id="a1316-622">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="a1316-622">DESCRIPTION</span></span>|<span data-ttu-id="a1316-623">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="a1316-624">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="a1316-624">Procedures</span></span>  
  
|<span data-ttu-id="a1316-625">ColumnName</span><span class="sxs-lookup"><span data-stu-id="a1316-625">ColumnName</span></span>|<span data-ttu-id="a1316-626">DataType</span><span class="sxs-lookup"><span data-stu-id="a1316-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="a1316-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a1316-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="a1316-628">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-628">String</span></span>|  
|<span data-ttu-id="a1316-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a1316-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="a1316-630">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-630">String</span></span>|  
|<span data-ttu-id="a1316-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="a1316-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="a1316-632">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-632">String</span></span>|  
|<span data-ttu-id="a1316-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="a1316-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="a1316-634">Int16</span><span class="sxs-lookup"><span data-stu-id="a1316-634">Int16</span></span>|  
|<span data-ttu-id="a1316-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="a1316-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="a1316-636">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-636">String</span></span>|  
|<span data-ttu-id="a1316-637">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="a1316-637">DESCRIPTION</span></span>|<span data-ttu-id="a1316-638">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-638">String</span></span>|  
|<span data-ttu-id="a1316-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="a1316-639">DATE_CREATED</span></span>|<span data-ttu-id="a1316-640">DateTime</span><span class="sxs-lookup"><span data-stu-id="a1316-640">DateTime</span></span>|  
|<span data-ttu-id="a1316-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="a1316-641">DATE_MODIFIED</span></span>|<span data-ttu-id="a1316-642">DateTime</span><span class="sxs-lookup"><span data-stu-id="a1316-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="a1316-643">Görünümler</span><span class="sxs-lookup"><span data-stu-id="a1316-643">Views</span></span>  
  
|<span data-ttu-id="a1316-644">ColumnName</span><span class="sxs-lookup"><span data-stu-id="a1316-644">ColumnName</span></span>|<span data-ttu-id="a1316-645">DataType</span><span class="sxs-lookup"><span data-stu-id="a1316-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="a1316-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a1316-646">TABLE_CATALOG</span></span>|<span data-ttu-id="a1316-647">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-647">String</span></span>|  
|<span data-ttu-id="a1316-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a1316-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="a1316-649">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-649">String</span></span>|  
|<span data-ttu-id="a1316-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="a1316-650">TABLE_NAME</span></span>|<span data-ttu-id="a1316-651">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-651">String</span></span>|  
|<span data-ttu-id="a1316-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="a1316-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="a1316-653">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-653">String</span></span>|  
|<span data-ttu-id="a1316-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="a1316-654">CHECK_OPTION</span></span>|<span data-ttu-id="a1316-655">Boole</span><span class="sxs-lookup"><span data-stu-id="a1316-655">Boolean</span></span>|  
|<span data-ttu-id="a1316-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="a1316-656">IS_UPDATABLE</span></span>|<span data-ttu-id="a1316-657">Boole</span><span class="sxs-lookup"><span data-stu-id="a1316-657">Boolean</span></span>|  
|<span data-ttu-id="a1316-658">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="a1316-658">DESCRIPTION</span></span>|<span data-ttu-id="a1316-659">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-659">String</span></span>|  
|<span data-ttu-id="a1316-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="a1316-660">DATE_CREATED</span></span>|<span data-ttu-id="a1316-661">DateTime</span><span class="sxs-lookup"><span data-stu-id="a1316-661">DateTime</span></span>|  
|<span data-ttu-id="a1316-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="a1316-662">DATE_MODIFIED</span></span>|<span data-ttu-id="a1316-663">DateTime</span><span class="sxs-lookup"><span data-stu-id="a1316-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="a1316-664">Dizinler</span><span class="sxs-lookup"><span data-stu-id="a1316-664">Indexes</span></span>  
  
|<span data-ttu-id="a1316-665">ColumnName</span><span class="sxs-lookup"><span data-stu-id="a1316-665">ColumnName</span></span>|<span data-ttu-id="a1316-666">DataType</span><span class="sxs-lookup"><span data-stu-id="a1316-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="a1316-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a1316-667">TABLE_CATALOG</span></span>|<span data-ttu-id="a1316-668">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-668">String</span></span>|  
|<span data-ttu-id="a1316-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a1316-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="a1316-670">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-670">String</span></span>|  
|<span data-ttu-id="a1316-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="a1316-671">TABLE_NAME</span></span>|<span data-ttu-id="a1316-672">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-672">String</span></span>|  
|<span data-ttu-id="a1316-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a1316-673">INDEX_CATALOG</span></span>|<span data-ttu-id="a1316-674">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-674">String</span></span>|  
|<span data-ttu-id="a1316-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a1316-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="a1316-676">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-676">String</span></span>|  
|<span data-ttu-id="a1316-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="a1316-677">INDEX_NAME</span></span>|<span data-ttu-id="a1316-678">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-678">String</span></span>|  
|<span data-ttu-id="a1316-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="a1316-679">PRIMARY_KEY</span></span>|<span data-ttu-id="a1316-680">Boole</span><span class="sxs-lookup"><span data-stu-id="a1316-680">Boolean</span></span>|  
|<span data-ttu-id="a1316-681">EŞI</span><span class="sxs-lookup"><span data-stu-id="a1316-681">UNIQUE</span></span>|<span data-ttu-id="a1316-682">Boole</span><span class="sxs-lookup"><span data-stu-id="a1316-682">Boolean</span></span>|  
|<span data-ttu-id="a1316-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="a1316-683">CLUSTERED</span></span>|<span data-ttu-id="a1316-684">Boole</span><span class="sxs-lookup"><span data-stu-id="a1316-684">Boolean</span></span>|  
|<span data-ttu-id="a1316-685">TÜR</span><span class="sxs-lookup"><span data-stu-id="a1316-685">TYPE</span></span>|<span data-ttu-id="a1316-686">Int32</span><span class="sxs-lookup"><span data-stu-id="a1316-686">Int32</span></span>|  
|<span data-ttu-id="a1316-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="a1316-687">FILL_FACTOR</span></span>|<span data-ttu-id="a1316-688">Int32</span><span class="sxs-lookup"><span data-stu-id="a1316-688">Int32</span></span>|  
|<span data-ttu-id="a1316-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="a1316-689">INITIAL_SIZE</span></span>|<span data-ttu-id="a1316-690">Int32</span><span class="sxs-lookup"><span data-stu-id="a1316-690">Int32</span></span>|  
|<span data-ttu-id="a1316-691">NULLS</span><span class="sxs-lookup"><span data-stu-id="a1316-691">NULLS</span></span>|<span data-ttu-id="a1316-692">Int32</span><span class="sxs-lookup"><span data-stu-id="a1316-692">Int32</span></span>|  
|<span data-ttu-id="a1316-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="a1316-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="a1316-694">Boole</span><span class="sxs-lookup"><span data-stu-id="a1316-694">Boolean</span></span>|  
|<span data-ttu-id="a1316-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="a1316-695">AUTO_UPDATE</span></span>|<span data-ttu-id="a1316-696">Boole</span><span class="sxs-lookup"><span data-stu-id="a1316-696">Boolean</span></span>|  
|<span data-ttu-id="a1316-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="a1316-697">NULL_COLLATION</span></span>|<span data-ttu-id="a1316-698">Int32</span><span class="sxs-lookup"><span data-stu-id="a1316-698">Int32</span></span>|  
|<span data-ttu-id="a1316-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="a1316-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="a1316-700">Int64</span><span class="sxs-lookup"><span data-stu-id="a1316-700">Int64</span></span>|  
|<span data-ttu-id="a1316-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="a1316-701">COLUMN_NAME</span></span>|<span data-ttu-id="a1316-702">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-702">String</span></span>|  
|<span data-ttu-id="a1316-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="a1316-703">COLUMN_GUID</span></span>|<span data-ttu-id="a1316-704">Guid</span><span class="sxs-lookup"><span data-stu-id="a1316-704">Guid</span></span>|  
|<span data-ttu-id="a1316-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="a1316-705">COLUMN_PROPID</span></span>|<span data-ttu-id="a1316-706">Int64</span><span class="sxs-lookup"><span data-stu-id="a1316-706">Int64</span></span>|  
|<span data-ttu-id="a1316-707">MEDIĞINDEN</span><span class="sxs-lookup"><span data-stu-id="a1316-707">COLLATION</span></span>|<span data-ttu-id="a1316-708">Int16</span><span class="sxs-lookup"><span data-stu-id="a1316-708">Int16</span></span>|  
|<span data-ttu-id="a1316-709">ITE</span><span class="sxs-lookup"><span data-stu-id="a1316-709">CARDINALITY</span></span>|<span data-ttu-id="a1316-710">Ondalık</span><span class="sxs-lookup"><span data-stu-id="a1316-710">Decimal</span></span>|  
|<span data-ttu-id="a1316-711">SAYFALARı</span><span class="sxs-lookup"><span data-stu-id="a1316-711">PAGES</span></span>|<span data-ttu-id="a1316-712">Int32</span><span class="sxs-lookup"><span data-stu-id="a1316-712">Int32</span></span>|  
|<span data-ttu-id="a1316-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="a1316-713">FILTER_CONDITION</span></span>|<span data-ttu-id="a1316-714">Dize</span><span class="sxs-lookup"><span data-stu-id="a1316-714">String</span></span>|  
|<span data-ttu-id="a1316-715">ILMIŞTIR</span><span class="sxs-lookup"><span data-stu-id="a1316-715">INTEGRATED</span></span>|<span data-ttu-id="a1316-716">Boole</span><span class="sxs-lookup"><span data-stu-id="a1316-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a1316-717">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a1316-717">See also</span></span>

- [<span data-ttu-id="a1316-718">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a1316-718">ADO.NET Overview</span></span>](ado-net-overview.md)
