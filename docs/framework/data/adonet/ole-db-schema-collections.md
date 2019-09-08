---
title: OLE DB Şema Koleksiyonları
ms.date: 03/30/2017
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
ms.openlocfilehash: 2d5718c12100ebea49a6b6fab29a3790918c6ad3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783453"
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="d1e63-102">OLE DB Şema Koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="d1e63-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="d1e63-103">Bu bölümde Microsoft SQL Server, Oracle ve Microsoft Jet için OLE DB sağlayıcıları için şema koleksiyonu desteği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d1e63-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="d1e63-104">Microsoft SQL Server OLE DB sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="d1e63-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="d1e63-105">Microsoft SQL Server OLE DB sürücü, ortak şema koleksiyonlarına ek olarak aşağıdaki belirli şema koleksiyonlarını destekler:</span><span class="sxs-lookup"><span data-stu-id="d1e63-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="d1e63-106">Takvimleri</span><span class="sxs-lookup"><span data-stu-id="d1e63-106">Tables</span></span>  
  
- <span data-ttu-id="d1e63-107">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="d1e63-107">Columns</span></span>  
  
- <span data-ttu-id="d1e63-108">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="d1e63-108">Procedures</span></span>  
  
- <span data-ttu-id="d1e63-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="d1e63-109">ProcedureParameters</span></span>  
  
- <span data-ttu-id="d1e63-110">Katalog</span><span class="sxs-lookup"><span data-stu-id="d1e63-110">Catalog</span></span>  
  
- <span data-ttu-id="d1e63-111">Dizinlerde</span><span class="sxs-lookup"><span data-stu-id="d1e63-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="d1e63-112">Takvimleri</span><span class="sxs-lookup"><span data-stu-id="d1e63-112">Tables</span></span>  
  
|<span data-ttu-id="d1e63-113">Tation</span><span class="sxs-lookup"><span data-stu-id="d1e63-113">ColumnName</span></span>|<span data-ttu-id="d1e63-114">DataType</span><span class="sxs-lookup"><span data-stu-id="d1e63-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d1e63-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d1e63-115">TABLE_CATALOG</span></span>|<span data-ttu-id="d1e63-116">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-116">String</span></span>|  
|<span data-ttu-id="d1e63-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d1e63-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="d1e63-118">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-118">String</span></span>|  
|<span data-ttu-id="d1e63-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d1e63-119">TABLE_NAME</span></span>|<span data-ttu-id="d1e63-120">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-120">String</span></span>|  
|<span data-ttu-id="d1e63-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="d1e63-121">TABLE_TYPE</span></span>|<span data-ttu-id="d1e63-122">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-122">String</span></span>|  
|<span data-ttu-id="d1e63-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="d1e63-123">TABLE_GUID</span></span>|<span data-ttu-id="d1e63-124">Guid</span><span class="sxs-lookup"><span data-stu-id="d1e63-124">Guid</span></span>|  
|<span data-ttu-id="d1e63-125">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="d1e63-125">DESCRIPTION</span></span>|<span data-ttu-id="d1e63-126">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-126">String</span></span>|  
|<span data-ttu-id="d1e63-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="d1e63-127">TABLE_PROPID</span></span>|<span data-ttu-id="d1e63-128">Int64</span><span class="sxs-lookup"><span data-stu-id="d1e63-128">Int64</span></span>|  
|<span data-ttu-id="d1e63-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="d1e63-129">DATE_CREATED</span></span>|<span data-ttu-id="d1e63-130">DateTime</span><span class="sxs-lookup"><span data-stu-id="d1e63-130">DateTime</span></span>|  
|<span data-ttu-id="d1e63-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="d1e63-131">DATE_MODIFIED</span></span>|<span data-ttu-id="d1e63-132">DateTime</span><span class="sxs-lookup"><span data-stu-id="d1e63-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="d1e63-133">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="d1e63-133">Columns</span></span>  
  
|<span data-ttu-id="d1e63-134">Tation</span><span class="sxs-lookup"><span data-stu-id="d1e63-134">ColumnName</span></span>|<span data-ttu-id="d1e63-135">DataType</span><span class="sxs-lookup"><span data-stu-id="d1e63-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d1e63-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d1e63-136">TABLE_CATALOG</span></span>|<span data-ttu-id="d1e63-137">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-137">String</span></span>|  
|<span data-ttu-id="d1e63-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d1e63-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="d1e63-139">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-139">String</span></span>|  
|<span data-ttu-id="d1e63-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d1e63-140">TABLE_NAME</span></span>|<span data-ttu-id="d1e63-141">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-141">String</span></span>|  
|<span data-ttu-id="d1e63-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="d1e63-142">COLUMN_NAME</span></span>|<span data-ttu-id="d1e63-143">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-143">String</span></span>|  
|<span data-ttu-id="d1e63-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="d1e63-144">COLUMN_GUID</span></span>|<span data-ttu-id="d1e63-145">Guid</span><span class="sxs-lookup"><span data-stu-id="d1e63-145">Guid</span></span>|  
|<span data-ttu-id="d1e63-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="d1e63-146">COLUMN_PROPID</span></span>|<span data-ttu-id="d1e63-147">Int64</span><span class="sxs-lookup"><span data-stu-id="d1e63-147">Int64</span></span>|  
|<span data-ttu-id="d1e63-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="d1e63-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="d1e63-149">Int64</span><span class="sxs-lookup"><span data-stu-id="d1e63-149">Int64</span></span>|  
|<span data-ttu-id="d1e63-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="d1e63-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="d1e63-151">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d1e63-151">Boolean</span></span>|  
|<span data-ttu-id="d1e63-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="d1e63-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="d1e63-153">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-153">String</span></span>|  
|<span data-ttu-id="d1e63-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="d1e63-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="d1e63-155">Int64</span><span class="sxs-lookup"><span data-stu-id="d1e63-155">Int64</span></span>|  
|<span data-ttu-id="d1e63-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="d1e63-156">IS_NULLABLE</span></span>|<span data-ttu-id="d1e63-157">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d1e63-157">Boolean</span></span>|  
|<span data-ttu-id="d1e63-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="d1e63-158">DATA_TYPE</span></span>|<span data-ttu-id="d1e63-159">Int32</span><span class="sxs-lookup"><span data-stu-id="d1e63-159">Int32</span></span>|  
|<span data-ttu-id="d1e63-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="d1e63-160">TYPE_GUID</span></span>|<span data-ttu-id="d1e63-161">Guid</span><span class="sxs-lookup"><span data-stu-id="d1e63-161">Guid</span></span>|  
|<span data-ttu-id="d1e63-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="d1e63-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="d1e63-163">Int64</span><span class="sxs-lookup"><span data-stu-id="d1e63-163">Int64</span></span>|  
|<span data-ttu-id="d1e63-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="d1e63-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="d1e63-165">Int64</span><span class="sxs-lookup"><span data-stu-id="d1e63-165">Int64</span></span>|  
|<span data-ttu-id="d1e63-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="d1e63-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="d1e63-167">Int32</span><span class="sxs-lookup"><span data-stu-id="d1e63-167">Int32</span></span>|  
|<span data-ttu-id="d1e63-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="d1e63-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="d1e63-169">Int16</span><span class="sxs-lookup"><span data-stu-id="d1e63-169">Int16</span></span>|  
|<span data-ttu-id="d1e63-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="d1e63-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="d1e63-171">Int64</span><span class="sxs-lookup"><span data-stu-id="d1e63-171">Int64</span></span>|  
|<span data-ttu-id="d1e63-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d1e63-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="d1e63-173">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-173">String</span></span>|  
|<span data-ttu-id="d1e63-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d1e63-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="d1e63-175">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-175">String</span></span>|  
|<span data-ttu-id="d1e63-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="d1e63-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="d1e63-177">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-177">String</span></span>|  
|<span data-ttu-id="d1e63-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d1e63-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="d1e63-179">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-179">String</span></span>|  
|<span data-ttu-id="d1e63-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d1e63-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="d1e63-181">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-181">String</span></span>|  
|<span data-ttu-id="d1e63-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="d1e63-182">COLLATION_NAME</span></span>|<span data-ttu-id="d1e63-183">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-183">String</span></span>|  
|<span data-ttu-id="d1e63-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d1e63-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="d1e63-185">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-185">String</span></span>|  
|<span data-ttu-id="d1e63-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d1e63-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="d1e63-187">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-187">String</span></span>|  
|<span data-ttu-id="d1e63-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="d1e63-188">DOMAIN_NAME</span></span>|<span data-ttu-id="d1e63-189">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-189">String</span></span>|  
|<span data-ttu-id="d1e63-190">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="d1e63-190">DESCRIPTION</span></span>|<span data-ttu-id="d1e63-191">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-191">String</span></span>|  
|<span data-ttu-id="d1e63-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="d1e63-192">COLUMN_LCID</span></span>|<span data-ttu-id="d1e63-193">Int32</span><span class="sxs-lookup"><span data-stu-id="d1e63-193">Int32</span></span>|  
|<span data-ttu-id="d1e63-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="d1e63-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="d1e63-195">Int32</span><span class="sxs-lookup"><span data-stu-id="d1e63-195">Int32</span></span>|  
|<span data-ttu-id="d1e63-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="d1e63-196">COLUMN_SORTID</span></span>|<span data-ttu-id="d1e63-197">Int32</span><span class="sxs-lookup"><span data-stu-id="d1e63-197">Int32</span></span>|  
|<span data-ttu-id="d1e63-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="d1e63-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="d1e63-199">Byte[]</span><span class="sxs-lookup"><span data-stu-id="d1e63-199">Byte[]</span></span>|  
|<span data-ttu-id="d1e63-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="d1e63-200">IS_COMPUTED</span></span>|<span data-ttu-id="d1e63-201">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d1e63-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="d1e63-202">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="d1e63-202">Procedures</span></span>  
  
|<span data-ttu-id="d1e63-203">Tation</span><span class="sxs-lookup"><span data-stu-id="d1e63-203">ColumnName</span></span>|<span data-ttu-id="d1e63-204">DataType</span><span class="sxs-lookup"><span data-stu-id="d1e63-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d1e63-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d1e63-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="d1e63-206">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-206">String</span></span>|  
|<span data-ttu-id="d1e63-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d1e63-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="d1e63-208">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-208">String</span></span>|  
|<span data-ttu-id="d1e63-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="d1e63-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="d1e63-210">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-210">String</span></span>|  
|<span data-ttu-id="d1e63-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="d1e63-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="d1e63-212">Int16</span><span class="sxs-lookup"><span data-stu-id="d1e63-212">Int16</span></span>|  
|<span data-ttu-id="d1e63-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="d1e63-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="d1e63-214">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-214">String</span></span>|  
|<span data-ttu-id="d1e63-215">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="d1e63-215">DESCRIPTION</span></span>|<span data-ttu-id="d1e63-216">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-216">String</span></span>|  
|<span data-ttu-id="d1e63-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="d1e63-217">DATE_CREATED</span></span>|<span data-ttu-id="d1e63-218">DateTime</span><span class="sxs-lookup"><span data-stu-id="d1e63-218">DateTime</span></span>|  
|<span data-ttu-id="d1e63-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="d1e63-219">DATE_MODIFIED</span></span>|<span data-ttu-id="d1e63-220">DateTime</span><span class="sxs-lookup"><span data-stu-id="d1e63-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="d1e63-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="d1e63-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="d1e63-222">Tation</span><span class="sxs-lookup"><span data-stu-id="d1e63-222">ColumnName</span></span>|<span data-ttu-id="d1e63-223">DataType</span><span class="sxs-lookup"><span data-stu-id="d1e63-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d1e63-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d1e63-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="d1e63-225">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-225">String</span></span>|  
|<span data-ttu-id="d1e63-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d1e63-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="d1e63-227">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-227">String</span></span>|  
|<span data-ttu-id="d1e63-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="d1e63-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="d1e63-229">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-229">String</span></span>|  
|<span data-ttu-id="d1e63-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="d1e63-230">PARAMETER_NAME</span></span>|<span data-ttu-id="d1e63-231">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-231">String</span></span>|  
|<span data-ttu-id="d1e63-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="d1e63-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="d1e63-233">Int32</span><span class="sxs-lookup"><span data-stu-id="d1e63-233">Int32</span></span>|  
|<span data-ttu-id="d1e63-234">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="d1e63-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="d1e63-235">Int32</span><span class="sxs-lookup"><span data-stu-id="d1e63-235">Int32</span></span>|  
|<span data-ttu-id="d1e63-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="d1e63-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="d1e63-237">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d1e63-237">Boolean</span></span>|  
|<span data-ttu-id="d1e63-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="d1e63-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="d1e63-239">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-239">String</span></span>|  
|<span data-ttu-id="d1e63-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="d1e63-240">IS_NULLABLE</span></span>|<span data-ttu-id="d1e63-241">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d1e63-241">Boolean</span></span>|  
|<span data-ttu-id="d1e63-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="d1e63-242">DATA_TYPE</span></span>|<span data-ttu-id="d1e63-243">Int32</span><span class="sxs-lookup"><span data-stu-id="d1e63-243">Int32</span></span>|  
|<span data-ttu-id="d1e63-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="d1e63-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="d1e63-245">Int64</span><span class="sxs-lookup"><span data-stu-id="d1e63-245">Int64</span></span>|  
|<span data-ttu-id="d1e63-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="d1e63-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="d1e63-247">Int64</span><span class="sxs-lookup"><span data-stu-id="d1e63-247">Int64</span></span>|  
|<span data-ttu-id="d1e63-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="d1e63-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="d1e63-249">Int32</span><span class="sxs-lookup"><span data-stu-id="d1e63-249">Int32</span></span>|  
|<span data-ttu-id="d1e63-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="d1e63-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="d1e63-251">Int16</span><span class="sxs-lookup"><span data-stu-id="d1e63-251">Int16</span></span>|  
|<span data-ttu-id="d1e63-252">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="d1e63-252">DESCRIPTION</span></span>|<span data-ttu-id="d1e63-253">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-253">String</span></span>|  
|<span data-ttu-id="d1e63-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="d1e63-254">TYPE_NAME</span></span>|<span data-ttu-id="d1e63-255">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-255">String</span></span>|  
|<span data-ttu-id="d1e63-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="d1e63-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="d1e63-257">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="d1e63-258">Katalog</span><span class="sxs-lookup"><span data-stu-id="d1e63-258">Catalog</span></span>  
  
|<span data-ttu-id="d1e63-259">Tation</span><span class="sxs-lookup"><span data-stu-id="d1e63-259">ColumnName</span></span>|<span data-ttu-id="d1e63-260">DataType</span><span class="sxs-lookup"><span data-stu-id="d1e63-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d1e63-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="d1e63-261">CATALOG_NAME</span></span>|<span data-ttu-id="d1e63-262">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-262">String</span></span>|  
|<span data-ttu-id="d1e63-263">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="d1e63-263">DESCRIPTION</span></span>|<span data-ttu-id="d1e63-264">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="d1e63-265">Dizinlerde</span><span class="sxs-lookup"><span data-stu-id="d1e63-265">Indexes</span></span>  
  
|<span data-ttu-id="d1e63-266">Tation</span><span class="sxs-lookup"><span data-stu-id="d1e63-266">ColumnName</span></span>|<span data-ttu-id="d1e63-267">DataType</span><span class="sxs-lookup"><span data-stu-id="d1e63-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d1e63-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d1e63-268">TABLE_CATALOG</span></span>|<span data-ttu-id="d1e63-269">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-269">String</span></span>|  
|<span data-ttu-id="d1e63-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d1e63-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="d1e63-271">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-271">String</span></span>|  
|<span data-ttu-id="d1e63-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d1e63-272">TABLE_NAME</span></span>|<span data-ttu-id="d1e63-273">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-273">String</span></span>|  
|<span data-ttu-id="d1e63-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d1e63-274">INDEX_CATALOG</span></span>|<span data-ttu-id="d1e63-275">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-275">String</span></span>|  
|<span data-ttu-id="d1e63-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d1e63-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="d1e63-277">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-277">String</span></span>|  
|<span data-ttu-id="d1e63-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="d1e63-278">INDEX_NAME</span></span>|<span data-ttu-id="d1e63-279">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-279">String</span></span>|  
|<span data-ttu-id="d1e63-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="d1e63-280">PRIMARY_KEY</span></span>|<span data-ttu-id="d1e63-281">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d1e63-281">Boolean</span></span>|  
|<span data-ttu-id="d1e63-282">EŞI</span><span class="sxs-lookup"><span data-stu-id="d1e63-282">UNIQUE</span></span>|<span data-ttu-id="d1e63-283">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d1e63-283">Boolean</span></span>|  
|<span data-ttu-id="d1e63-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="d1e63-284">CLUSTERED</span></span>|<span data-ttu-id="d1e63-285">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d1e63-285">Boolean</span></span>|  
|<span data-ttu-id="d1e63-286">TÜRÜYLE</span><span class="sxs-lookup"><span data-stu-id="d1e63-286">TYPE</span></span>|<span data-ttu-id="d1e63-287">Int32</span><span class="sxs-lookup"><span data-stu-id="d1e63-287">Int32</span></span>|  
|<span data-ttu-id="d1e63-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="d1e63-288">FILL_FACTOR</span></span>|<span data-ttu-id="d1e63-289">Int32</span><span class="sxs-lookup"><span data-stu-id="d1e63-289">Int32</span></span>|  
|<span data-ttu-id="d1e63-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="d1e63-290">INITIAL_SIZE</span></span>|<span data-ttu-id="d1e63-291">Int32</span><span class="sxs-lookup"><span data-stu-id="d1e63-291">Int32</span></span>|  
|<span data-ttu-id="d1e63-292">NULLS</span><span class="sxs-lookup"><span data-stu-id="d1e63-292">NULLS</span></span>|<span data-ttu-id="d1e63-293">Int32</span><span class="sxs-lookup"><span data-stu-id="d1e63-293">Int32</span></span>|  
|<span data-ttu-id="d1e63-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="d1e63-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="d1e63-295">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d1e63-295">Boolean</span></span>|  
|<span data-ttu-id="d1e63-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="d1e63-296">AUTO_UPDATE</span></span>|<span data-ttu-id="d1e63-297">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d1e63-297">Boolean</span></span>|  
|<span data-ttu-id="d1e63-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="d1e63-298">NULL_COLLATION</span></span>|<span data-ttu-id="d1e63-299">Int32</span><span class="sxs-lookup"><span data-stu-id="d1e63-299">Int32</span></span>|  
|<span data-ttu-id="d1e63-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="d1e63-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="d1e63-301">Int64</span><span class="sxs-lookup"><span data-stu-id="d1e63-301">Int64</span></span>|  
|<span data-ttu-id="d1e63-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="d1e63-302">COLUMN_NAME</span></span>|<span data-ttu-id="d1e63-303">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-303">String</span></span>|  
|<span data-ttu-id="d1e63-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="d1e63-304">COLUMN_GUID</span></span>|<span data-ttu-id="d1e63-305">Guid</span><span class="sxs-lookup"><span data-stu-id="d1e63-305">Guid</span></span>|  
|<span data-ttu-id="d1e63-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="d1e63-306">COLUMN_PROPID</span></span>|<span data-ttu-id="d1e63-307">Int64</span><span class="sxs-lookup"><span data-stu-id="d1e63-307">Int64</span></span>|  
|<span data-ttu-id="d1e63-308">MEDIĞINDEN</span><span class="sxs-lookup"><span data-stu-id="d1e63-308">COLLATION</span></span>|<span data-ttu-id="d1e63-309">Int16</span><span class="sxs-lookup"><span data-stu-id="d1e63-309">Int16</span></span>|  
|<span data-ttu-id="d1e63-310">ITE</span><span class="sxs-lookup"><span data-stu-id="d1e63-310">CARDINALITY</span></span>|<span data-ttu-id="d1e63-311">Ondalık</span><span class="sxs-lookup"><span data-stu-id="d1e63-311">Decimal</span></span>|  
|<span data-ttu-id="d1e63-312">SAYFALARI</span><span class="sxs-lookup"><span data-stu-id="d1e63-312">PAGES</span></span>|<span data-ttu-id="d1e63-313">Int32</span><span class="sxs-lookup"><span data-stu-id="d1e63-313">Int32</span></span>|  
|<span data-ttu-id="d1e63-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="d1e63-314">FILTER_CONDITION</span></span>|<span data-ttu-id="d1e63-315">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-315">String</span></span>|  
|<span data-ttu-id="d1e63-316">ILMIŞTIR</span><span class="sxs-lookup"><span data-stu-id="d1e63-316">INTEGRATED</span></span>|<span data-ttu-id="d1e63-317">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d1e63-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="d1e63-318">Microsoft Oracle OLE DB sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="d1e63-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="d1e63-319">Microsoft Oracle OLE DB sürücüsü, ortak şema koleksiyonlarına ek olarak aşağıdaki belirli şema koleksiyonlarını destekler:</span><span class="sxs-lookup"><span data-stu-id="d1e63-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="d1e63-320">Takvimleri</span><span class="sxs-lookup"><span data-stu-id="d1e63-320">Tables</span></span>  
  
- <span data-ttu-id="d1e63-321">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="d1e63-321">Columns</span></span>  
  
- <span data-ttu-id="d1e63-322">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="d1e63-322">Procedures</span></span>  
  
- <span data-ttu-id="d1e63-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="d1e63-323">ProcedureColumns</span></span>  
  
- <span data-ttu-id="d1e63-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="d1e63-324">ProcedureParameters</span></span>  
  
- <span data-ttu-id="d1e63-325">Görünümler</span><span class="sxs-lookup"><span data-stu-id="d1e63-325">Views</span></span>  
  
- <span data-ttu-id="d1e63-326">Dizinlerde</span><span class="sxs-lookup"><span data-stu-id="d1e63-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="d1e63-327">Takvimleri</span><span class="sxs-lookup"><span data-stu-id="d1e63-327">Tables</span></span>  
  
|<span data-ttu-id="d1e63-328">Tation</span><span class="sxs-lookup"><span data-stu-id="d1e63-328">ColumnName</span></span>|<span data-ttu-id="d1e63-329">DataType</span><span class="sxs-lookup"><span data-stu-id="d1e63-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d1e63-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d1e63-330">TABLE_CATALOG</span></span>|<span data-ttu-id="d1e63-331">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-331">String</span></span>|  
|<span data-ttu-id="d1e63-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d1e63-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="d1e63-333">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-333">String</span></span>|  
|<span data-ttu-id="d1e63-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d1e63-334">TABLE_NAME</span></span>|<span data-ttu-id="d1e63-335">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-335">String</span></span>|  
|<span data-ttu-id="d1e63-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="d1e63-336">TABLE_TYPE</span></span>|<span data-ttu-id="d1e63-337">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-337">String</span></span>|  
|<span data-ttu-id="d1e63-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="d1e63-338">TABLE_GUID</span></span>|<span data-ttu-id="d1e63-339">Guid</span><span class="sxs-lookup"><span data-stu-id="d1e63-339">Guid</span></span>|  
|<span data-ttu-id="d1e63-340">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="d1e63-340">DESCRIPTION</span></span>|<span data-ttu-id="d1e63-341">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-341">String</span></span>|  
|<span data-ttu-id="d1e63-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="d1e63-342">TABLE_PROPID</span></span>|<span data-ttu-id="d1e63-343">Int64</span><span class="sxs-lookup"><span data-stu-id="d1e63-343">Int64</span></span>|  
|<span data-ttu-id="d1e63-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="d1e63-344">DATE_CREATED</span></span>|<span data-ttu-id="d1e63-345">DateTime</span><span class="sxs-lookup"><span data-stu-id="d1e63-345">DateTime</span></span>|  
|<span data-ttu-id="d1e63-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="d1e63-346">DATE_MODIFIED</span></span>|<span data-ttu-id="d1e63-347">DateTime</span><span class="sxs-lookup"><span data-stu-id="d1e63-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="d1e63-348">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="d1e63-348">Columns</span></span>  
  
|<span data-ttu-id="d1e63-349">Tation</span><span class="sxs-lookup"><span data-stu-id="d1e63-349">ColumnName</span></span>|<span data-ttu-id="d1e63-350">DataType</span><span class="sxs-lookup"><span data-stu-id="d1e63-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d1e63-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d1e63-351">TABLE_CATALOG</span></span>|<span data-ttu-id="d1e63-352">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-352">String</span></span>|  
|<span data-ttu-id="d1e63-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d1e63-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="d1e63-354">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-354">String</span></span>|  
|<span data-ttu-id="d1e63-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d1e63-355">TABLE_NAME</span></span>|<span data-ttu-id="d1e63-356">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-356">String</span></span>|  
|<span data-ttu-id="d1e63-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="d1e63-357">COLUMN_NAME</span></span>|<span data-ttu-id="d1e63-358">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-358">String</span></span>|  
|<span data-ttu-id="d1e63-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="d1e63-359">COLUMN_GUID</span></span>|<span data-ttu-id="d1e63-360">Guid</span><span class="sxs-lookup"><span data-stu-id="d1e63-360">Guid</span></span>|  
|<span data-ttu-id="d1e63-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="d1e63-361">COLUMN_PROPID</span></span>|<span data-ttu-id="d1e63-362">Int64</span><span class="sxs-lookup"><span data-stu-id="d1e63-362">Int64</span></span>|  
|<span data-ttu-id="d1e63-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="d1e63-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="d1e63-364">Int64</span><span class="sxs-lookup"><span data-stu-id="d1e63-364">Int64</span></span>|  
|<span data-ttu-id="d1e63-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="d1e63-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="d1e63-366">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d1e63-366">Boolean</span></span>|  
|<span data-ttu-id="d1e63-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="d1e63-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="d1e63-368">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-368">String</span></span>|  
|<span data-ttu-id="d1e63-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="d1e63-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="d1e63-370">Int64</span><span class="sxs-lookup"><span data-stu-id="d1e63-370">Int64</span></span>|  
|<span data-ttu-id="d1e63-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="d1e63-371">IS_NULLABLE</span></span>|<span data-ttu-id="d1e63-372">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d1e63-372">Boolean</span></span>|  
|<span data-ttu-id="d1e63-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="d1e63-373">DATA_TYPE</span></span>|<span data-ttu-id="d1e63-374">Int32</span><span class="sxs-lookup"><span data-stu-id="d1e63-374">Int32</span></span>|  
|<span data-ttu-id="d1e63-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="d1e63-375">TYPE_GUID</span></span>|<span data-ttu-id="d1e63-376">Guid</span><span class="sxs-lookup"><span data-stu-id="d1e63-376">Guid</span></span>|  
|<span data-ttu-id="d1e63-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="d1e63-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="d1e63-378">Int64</span><span class="sxs-lookup"><span data-stu-id="d1e63-378">Int64</span></span>|  
|<span data-ttu-id="d1e63-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="d1e63-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="d1e63-380">Int64</span><span class="sxs-lookup"><span data-stu-id="d1e63-380">Int64</span></span>|  
|<span data-ttu-id="d1e63-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="d1e63-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="d1e63-382">Int32</span><span class="sxs-lookup"><span data-stu-id="d1e63-382">Int32</span></span>|  
|<span data-ttu-id="d1e63-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="d1e63-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="d1e63-384">Int16</span><span class="sxs-lookup"><span data-stu-id="d1e63-384">Int16</span></span>|  
|<span data-ttu-id="d1e63-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="d1e63-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="d1e63-386">Int64</span><span class="sxs-lookup"><span data-stu-id="d1e63-386">Int64</span></span>|  
|<span data-ttu-id="d1e63-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d1e63-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="d1e63-388">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-388">String</span></span>|  
|<span data-ttu-id="d1e63-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d1e63-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="d1e63-390">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-390">String</span></span>|  
|<span data-ttu-id="d1e63-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="d1e63-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="d1e63-392">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-392">String</span></span>|  
|<span data-ttu-id="d1e63-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d1e63-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="d1e63-394">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-394">String</span></span>|  
|<span data-ttu-id="d1e63-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d1e63-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="d1e63-396">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-396">String</span></span>|  
|<span data-ttu-id="d1e63-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="d1e63-397">COLLATION_NAME</span></span>|<span data-ttu-id="d1e63-398">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-398">String</span></span>|  
|<span data-ttu-id="d1e63-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d1e63-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="d1e63-400">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-400">String</span></span>|  
|<span data-ttu-id="d1e63-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d1e63-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="d1e63-402">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-402">String</span></span>|  
|<span data-ttu-id="d1e63-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="d1e63-403">DOMAIN_NAME</span></span>|<span data-ttu-id="d1e63-404">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-404">String</span></span>|  
|<span data-ttu-id="d1e63-405">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="d1e63-405">DESCRIPTION</span></span>|<span data-ttu-id="d1e63-406">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="d1e63-407">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="d1e63-407">Procedures</span></span>  
  
|<span data-ttu-id="d1e63-408">Tation</span><span class="sxs-lookup"><span data-stu-id="d1e63-408">ColumnName</span></span>|<span data-ttu-id="d1e63-409">DataType</span><span class="sxs-lookup"><span data-stu-id="d1e63-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d1e63-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d1e63-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="d1e63-411">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-411">String</span></span>|  
|<span data-ttu-id="d1e63-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d1e63-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="d1e63-413">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-413">String</span></span>|  
|<span data-ttu-id="d1e63-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="d1e63-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="d1e63-415">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-415">String</span></span>|  
|<span data-ttu-id="d1e63-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="d1e63-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="d1e63-417">Int16</span><span class="sxs-lookup"><span data-stu-id="d1e63-417">Int16</span></span>|  
|<span data-ttu-id="d1e63-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="d1e63-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="d1e63-419">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-419">String</span></span>|  
|<span data-ttu-id="d1e63-420">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="d1e63-420">DESCRIPTION</span></span>|<span data-ttu-id="d1e63-421">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-421">String</span></span>|  
|<span data-ttu-id="d1e63-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="d1e63-422">DATE_CREATED</span></span>|<span data-ttu-id="d1e63-423">DateTime</span><span class="sxs-lookup"><span data-stu-id="d1e63-423">DateTime</span></span>|  
|<span data-ttu-id="d1e63-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="d1e63-424">DATE_MODIFIED</span></span>|<span data-ttu-id="d1e63-425">DateTime</span><span class="sxs-lookup"><span data-stu-id="d1e63-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="d1e63-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="d1e63-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="d1e63-427">Tation</span><span class="sxs-lookup"><span data-stu-id="d1e63-427">ColumnName</span></span>|<span data-ttu-id="d1e63-428">DataType</span><span class="sxs-lookup"><span data-stu-id="d1e63-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d1e63-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d1e63-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="d1e63-430">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-430">String</span></span>|  
|<span data-ttu-id="d1e63-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d1e63-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="d1e63-432">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-432">String</span></span>|  
|<span data-ttu-id="d1e63-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="d1e63-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="d1e63-434">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-434">String</span></span>|  
|<span data-ttu-id="d1e63-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="d1e63-435">COLUMN_NAME</span></span>|<span data-ttu-id="d1e63-436">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-436">String</span></span>|  
|<span data-ttu-id="d1e63-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="d1e63-437">COLUMN_GUID</span></span>|<span data-ttu-id="d1e63-438">Guid</span><span class="sxs-lookup"><span data-stu-id="d1e63-438">Guid</span></span>|  
|<span data-ttu-id="d1e63-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="d1e63-439">COLUMN_PROPID</span></span>|<span data-ttu-id="d1e63-440">Int64</span><span class="sxs-lookup"><span data-stu-id="d1e63-440">Int64</span></span>|  
|<span data-ttu-id="d1e63-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="d1e63-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="d1e63-442">Int64</span><span class="sxs-lookup"><span data-stu-id="d1e63-442">Int64</span></span>|  
|<span data-ttu-id="d1e63-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="d1e63-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="d1e63-444">Int64</span><span class="sxs-lookup"><span data-stu-id="d1e63-444">Int64</span></span>|  
|<span data-ttu-id="d1e63-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="d1e63-445">IS_NULLABLE</span></span>|<span data-ttu-id="d1e63-446">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d1e63-446">Boolean</span></span>|  
|<span data-ttu-id="d1e63-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="d1e63-447">DATA_TYPE</span></span>|<span data-ttu-id="d1e63-448">Int32</span><span class="sxs-lookup"><span data-stu-id="d1e63-448">Int32</span></span>|  
|<span data-ttu-id="d1e63-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="d1e63-449">TYPE_GUID</span></span>|<span data-ttu-id="d1e63-450">Guid</span><span class="sxs-lookup"><span data-stu-id="d1e63-450">Guid</span></span>|  
|<span data-ttu-id="d1e63-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="d1e63-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="d1e63-452">Int64</span><span class="sxs-lookup"><span data-stu-id="d1e63-452">Int64</span></span>|  
|<span data-ttu-id="d1e63-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="d1e63-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="d1e63-454">Int64</span><span class="sxs-lookup"><span data-stu-id="d1e63-454">Int64</span></span>|  
|<span data-ttu-id="d1e63-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="d1e63-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="d1e63-456">Int32</span><span class="sxs-lookup"><span data-stu-id="d1e63-456">Int32</span></span>|  
|<span data-ttu-id="d1e63-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="d1e63-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="d1e63-458">Int16</span><span class="sxs-lookup"><span data-stu-id="d1e63-458">Int16</span></span>|  
|<span data-ttu-id="d1e63-459">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="d1e63-459">DESCRIPTION</span></span>|<span data-ttu-id="d1e63-460">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-460">String</span></span>|  
|<span data-ttu-id="d1e63-461">YÜKLEMEK</span><span class="sxs-lookup"><span data-stu-id="d1e63-461">OVERLOAD</span></span>|<span data-ttu-id="d1e63-462">Int16</span><span class="sxs-lookup"><span data-stu-id="d1e63-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="d1e63-463">Görünümler</span><span class="sxs-lookup"><span data-stu-id="d1e63-463">Views</span></span>  
  
|<span data-ttu-id="d1e63-464">Tation</span><span class="sxs-lookup"><span data-stu-id="d1e63-464">ColumnName</span></span>|<span data-ttu-id="d1e63-465">DataType</span><span class="sxs-lookup"><span data-stu-id="d1e63-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d1e63-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d1e63-466">TABLE_CATALOG</span></span>|<span data-ttu-id="d1e63-467">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-467">String</span></span>|  
|<span data-ttu-id="d1e63-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d1e63-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="d1e63-469">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-469">String</span></span>|  
|<span data-ttu-id="d1e63-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d1e63-470">TABLE_NAME</span></span>|<span data-ttu-id="d1e63-471">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-471">String</span></span>|  
|<span data-ttu-id="d1e63-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="d1e63-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="d1e63-473">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-473">String</span></span>|  
|<span data-ttu-id="d1e63-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="d1e63-474">CHECK_OPTION</span></span>|<span data-ttu-id="d1e63-475">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d1e63-475">Boolean</span></span>|  
|<span data-ttu-id="d1e63-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="d1e63-476">IS_UPDATABLE</span></span>|<span data-ttu-id="d1e63-477">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d1e63-477">Boolean</span></span>|  
|<span data-ttu-id="d1e63-478">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="d1e63-478">DESCRIPTION</span></span>|<span data-ttu-id="d1e63-479">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-479">String</span></span>|  
|<span data-ttu-id="d1e63-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="d1e63-480">DATE_CREATED</span></span>|<span data-ttu-id="d1e63-481">DateTime</span><span class="sxs-lookup"><span data-stu-id="d1e63-481">DateTime</span></span>|  
|<span data-ttu-id="d1e63-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="d1e63-482">DATE_MODIFIED</span></span>|<span data-ttu-id="d1e63-483">DateTime</span><span class="sxs-lookup"><span data-stu-id="d1e63-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="d1e63-484">Dizinlerde</span><span class="sxs-lookup"><span data-stu-id="d1e63-484">Indexes</span></span>  
  
|<span data-ttu-id="d1e63-485">Tation</span><span class="sxs-lookup"><span data-stu-id="d1e63-485">ColumnName</span></span>|<span data-ttu-id="d1e63-486">DataType</span><span class="sxs-lookup"><span data-stu-id="d1e63-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d1e63-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d1e63-487">TABLE_CATALOG</span></span>|<span data-ttu-id="d1e63-488">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-488">String</span></span>|  
|<span data-ttu-id="d1e63-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d1e63-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="d1e63-490">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-490">String</span></span>|  
|<span data-ttu-id="d1e63-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d1e63-491">TABLE_NAME</span></span>|<span data-ttu-id="d1e63-492">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-492">String</span></span>|  
|<span data-ttu-id="d1e63-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d1e63-493">INDEX_CATALOG</span></span>|<span data-ttu-id="d1e63-494">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-494">String</span></span>|  
|<span data-ttu-id="d1e63-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d1e63-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="d1e63-496">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-496">String</span></span>|  
|<span data-ttu-id="d1e63-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="d1e63-497">INDEX_NAME</span></span>|<span data-ttu-id="d1e63-498">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-498">String</span></span>|  
|<span data-ttu-id="d1e63-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="d1e63-499">PRIMARY_KEY</span></span>|<span data-ttu-id="d1e63-500">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d1e63-500">Boolean</span></span>|  
|<span data-ttu-id="d1e63-501">EŞI</span><span class="sxs-lookup"><span data-stu-id="d1e63-501">UNIQUE</span></span>|<span data-ttu-id="d1e63-502">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d1e63-502">Boolean</span></span>|  
|<span data-ttu-id="d1e63-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="d1e63-503">CLUSTERED</span></span>|<span data-ttu-id="d1e63-504">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d1e63-504">Boolean</span></span>|  
|<span data-ttu-id="d1e63-505">TÜRÜYLE</span><span class="sxs-lookup"><span data-stu-id="d1e63-505">TYPE</span></span>|<span data-ttu-id="d1e63-506">Int32</span><span class="sxs-lookup"><span data-stu-id="d1e63-506">Int32</span></span>|  
|<span data-ttu-id="d1e63-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="d1e63-507">FILL_FACTOR</span></span>|<span data-ttu-id="d1e63-508">Int32</span><span class="sxs-lookup"><span data-stu-id="d1e63-508">Int32</span></span>|  
|<span data-ttu-id="d1e63-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="d1e63-509">INITIAL_SIZE</span></span>|<span data-ttu-id="d1e63-510">Int32</span><span class="sxs-lookup"><span data-stu-id="d1e63-510">Int32</span></span>|  
|<span data-ttu-id="d1e63-511">NULLS</span><span class="sxs-lookup"><span data-stu-id="d1e63-511">NULLS</span></span>|<span data-ttu-id="d1e63-512">Int32</span><span class="sxs-lookup"><span data-stu-id="d1e63-512">Int32</span></span>|  
|<span data-ttu-id="d1e63-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="d1e63-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="d1e63-514">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d1e63-514">Boolean</span></span>|  
|<span data-ttu-id="d1e63-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="d1e63-515">AUTO_UPDATE</span></span>|<span data-ttu-id="d1e63-516">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d1e63-516">Boolean</span></span>|  
|<span data-ttu-id="d1e63-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="d1e63-517">NULL_COLLATION</span></span>|<span data-ttu-id="d1e63-518">Int32</span><span class="sxs-lookup"><span data-stu-id="d1e63-518">Int32</span></span>|  
|<span data-ttu-id="d1e63-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="d1e63-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="d1e63-520">Int64</span><span class="sxs-lookup"><span data-stu-id="d1e63-520">Int64</span></span>|  
|<span data-ttu-id="d1e63-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="d1e63-521">COLUMN_NAME</span></span>|<span data-ttu-id="d1e63-522">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-522">String</span></span>|  
|<span data-ttu-id="d1e63-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="d1e63-523">COLUMN_GUID</span></span>|<span data-ttu-id="d1e63-524">Guid</span><span class="sxs-lookup"><span data-stu-id="d1e63-524">Guid</span></span>|  
|<span data-ttu-id="d1e63-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="d1e63-525">COLUMN_PROPID</span></span>|<span data-ttu-id="d1e63-526">Int64</span><span class="sxs-lookup"><span data-stu-id="d1e63-526">Int64</span></span>|  
|<span data-ttu-id="d1e63-527">MEDIĞINDEN</span><span class="sxs-lookup"><span data-stu-id="d1e63-527">COLLATION</span></span>|<span data-ttu-id="d1e63-528">Int16</span><span class="sxs-lookup"><span data-stu-id="d1e63-528">Int16</span></span>|  
|<span data-ttu-id="d1e63-529">ITE</span><span class="sxs-lookup"><span data-stu-id="d1e63-529">CARDINALITY</span></span>|<span data-ttu-id="d1e63-530">Ondalık</span><span class="sxs-lookup"><span data-stu-id="d1e63-530">Decimal</span></span>|  
|<span data-ttu-id="d1e63-531">SAYFALARI</span><span class="sxs-lookup"><span data-stu-id="d1e63-531">PAGES</span></span>|<span data-ttu-id="d1e63-532">Int32</span><span class="sxs-lookup"><span data-stu-id="d1e63-532">Int32</span></span>|  
|<span data-ttu-id="d1e63-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="d1e63-533">FILTER_CONDITION</span></span>|<span data-ttu-id="d1e63-534">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-534">String</span></span>|  
|<span data-ttu-id="d1e63-535">ILMIŞTIR</span><span class="sxs-lookup"><span data-stu-id="d1e63-535">INTEGRATED</span></span>|<span data-ttu-id="d1e63-536">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d1e63-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="d1e63-537">Microsoft Jet OLE DB sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="d1e63-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="d1e63-538">Microsoft Jet OLE DB sürücüsü, ortak şema koleksiyonlarına ek olarak aşağıdaki belirli şema koleksiyonlarını destekler:</span><span class="sxs-lookup"><span data-stu-id="d1e63-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="d1e63-539">Takvimleri</span><span class="sxs-lookup"><span data-stu-id="d1e63-539">Tables</span></span>  
  
- <span data-ttu-id="d1e63-540">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="d1e63-540">Columns</span></span>  
  
- <span data-ttu-id="d1e63-541">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="d1e63-541">Procedures</span></span>  
  
- <span data-ttu-id="d1e63-542">Görünümler</span><span class="sxs-lookup"><span data-stu-id="d1e63-542">Views</span></span>  
  
- <span data-ttu-id="d1e63-543">Dizinlerde</span><span class="sxs-lookup"><span data-stu-id="d1e63-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="d1e63-544">Takvimleri</span><span class="sxs-lookup"><span data-stu-id="d1e63-544">Tables</span></span>  
  
|<span data-ttu-id="d1e63-545">Tation</span><span class="sxs-lookup"><span data-stu-id="d1e63-545">ColumnName</span></span>|<span data-ttu-id="d1e63-546">DataType</span><span class="sxs-lookup"><span data-stu-id="d1e63-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d1e63-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d1e63-547">TABLE_CATALOG</span></span>|<span data-ttu-id="d1e63-548">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-548">String</span></span>|  
|<span data-ttu-id="d1e63-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d1e63-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="d1e63-550">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-550">String</span></span>|  
|<span data-ttu-id="d1e63-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d1e63-551">TABLE_NAME</span></span>|<span data-ttu-id="d1e63-552">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-552">String</span></span>|  
|<span data-ttu-id="d1e63-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="d1e63-553">TABLE_TYPE</span></span>|<span data-ttu-id="d1e63-554">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-554">String</span></span>|  
|<span data-ttu-id="d1e63-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="d1e63-555">TABLE_GUID</span></span>|<span data-ttu-id="d1e63-556">Guid</span><span class="sxs-lookup"><span data-stu-id="d1e63-556">Guid</span></span>|  
|<span data-ttu-id="d1e63-557">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="d1e63-557">DESCRIPTION</span></span>|<span data-ttu-id="d1e63-558">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-558">String</span></span>|  
|<span data-ttu-id="d1e63-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="d1e63-559">TABLE_PROPID</span></span>|<span data-ttu-id="d1e63-560">Int64</span><span class="sxs-lookup"><span data-stu-id="d1e63-560">Int64</span></span>|  
|<span data-ttu-id="d1e63-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="d1e63-561">DATE_CREATED</span></span>|<span data-ttu-id="d1e63-562">DateTime</span><span class="sxs-lookup"><span data-stu-id="d1e63-562">DateTime</span></span>|  
|<span data-ttu-id="d1e63-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="d1e63-563">DATE_MODIFIED</span></span>|<span data-ttu-id="d1e63-564">DateTime</span><span class="sxs-lookup"><span data-stu-id="d1e63-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="d1e63-565">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="d1e63-565">Columns</span></span>  
  
|<span data-ttu-id="d1e63-566">Tation</span><span class="sxs-lookup"><span data-stu-id="d1e63-566">ColumnName</span></span>|<span data-ttu-id="d1e63-567">DataType</span><span class="sxs-lookup"><span data-stu-id="d1e63-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d1e63-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d1e63-568">TABLE_CATALOG</span></span>|<span data-ttu-id="d1e63-569">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-569">String</span></span>|  
|<span data-ttu-id="d1e63-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d1e63-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="d1e63-571">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-571">String</span></span>|  
|<span data-ttu-id="d1e63-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d1e63-572">TABLE_NAME</span></span>|<span data-ttu-id="d1e63-573">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-573">String</span></span>|  
|<span data-ttu-id="d1e63-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="d1e63-574">COLUMN_NAME</span></span>|<span data-ttu-id="d1e63-575">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-575">String</span></span>|  
|<span data-ttu-id="d1e63-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="d1e63-576">COLUMN_GUID</span></span>|<span data-ttu-id="d1e63-577">Guid</span><span class="sxs-lookup"><span data-stu-id="d1e63-577">Guid</span></span>|  
|<span data-ttu-id="d1e63-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="d1e63-578">COLUMN_PROPID</span></span>|<span data-ttu-id="d1e63-579">Int64</span><span class="sxs-lookup"><span data-stu-id="d1e63-579">Int64</span></span>|  
|<span data-ttu-id="d1e63-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="d1e63-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="d1e63-581">Int64</span><span class="sxs-lookup"><span data-stu-id="d1e63-581">Int64</span></span>|  
|<span data-ttu-id="d1e63-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="d1e63-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="d1e63-583">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d1e63-583">Boolean</span></span>|  
|<span data-ttu-id="d1e63-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="d1e63-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="d1e63-585">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-585">String</span></span>|  
|<span data-ttu-id="d1e63-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="d1e63-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="d1e63-587">Int64</span><span class="sxs-lookup"><span data-stu-id="d1e63-587">Int64</span></span>|  
|<span data-ttu-id="d1e63-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="d1e63-588">IS_NULLABLE</span></span>|<span data-ttu-id="d1e63-589">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d1e63-589">Boolean</span></span>|  
|<span data-ttu-id="d1e63-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="d1e63-590">DATA_TYPE</span></span>|<span data-ttu-id="d1e63-591">Int32</span><span class="sxs-lookup"><span data-stu-id="d1e63-591">Int32</span></span>|  
|<span data-ttu-id="d1e63-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="d1e63-592">TYPE_GUID</span></span>|<span data-ttu-id="d1e63-593">Guid</span><span class="sxs-lookup"><span data-stu-id="d1e63-593">Guid</span></span>|  
|<span data-ttu-id="d1e63-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="d1e63-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="d1e63-595">Int64</span><span class="sxs-lookup"><span data-stu-id="d1e63-595">Int64</span></span>|  
|<span data-ttu-id="d1e63-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="d1e63-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="d1e63-597">Int64</span><span class="sxs-lookup"><span data-stu-id="d1e63-597">Int64</span></span>|  
|<span data-ttu-id="d1e63-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="d1e63-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="d1e63-599">Int32</span><span class="sxs-lookup"><span data-stu-id="d1e63-599">Int32</span></span>|  
|<span data-ttu-id="d1e63-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="d1e63-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="d1e63-601">Int16</span><span class="sxs-lookup"><span data-stu-id="d1e63-601">Int16</span></span>|  
|<span data-ttu-id="d1e63-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="d1e63-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="d1e63-603">Int64</span><span class="sxs-lookup"><span data-stu-id="d1e63-603">Int64</span></span>|  
|<span data-ttu-id="d1e63-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d1e63-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="d1e63-605">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-605">String</span></span>|  
|<span data-ttu-id="d1e63-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d1e63-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="d1e63-607">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-607">String</span></span>|  
|<span data-ttu-id="d1e63-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="d1e63-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="d1e63-609">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-609">String</span></span>|  
|<span data-ttu-id="d1e63-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d1e63-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="d1e63-611">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-611">String</span></span>|  
|<span data-ttu-id="d1e63-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d1e63-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="d1e63-613">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-613">String</span></span>|  
|<span data-ttu-id="d1e63-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="d1e63-614">COLLATION_NAME</span></span>|<span data-ttu-id="d1e63-615">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-615">String</span></span>|  
|<span data-ttu-id="d1e63-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d1e63-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="d1e63-617">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-617">String</span></span>|  
|<span data-ttu-id="d1e63-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d1e63-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="d1e63-619">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-619">String</span></span>|  
|<span data-ttu-id="d1e63-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="d1e63-620">DOMAIN_NAME</span></span>|<span data-ttu-id="d1e63-621">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-621">String</span></span>|  
|<span data-ttu-id="d1e63-622">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="d1e63-622">DESCRIPTION</span></span>|<span data-ttu-id="d1e63-623">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="d1e63-624">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="d1e63-624">Procedures</span></span>  
  
|<span data-ttu-id="d1e63-625">Tation</span><span class="sxs-lookup"><span data-stu-id="d1e63-625">ColumnName</span></span>|<span data-ttu-id="d1e63-626">DataType</span><span class="sxs-lookup"><span data-stu-id="d1e63-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d1e63-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d1e63-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="d1e63-628">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-628">String</span></span>|  
|<span data-ttu-id="d1e63-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d1e63-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="d1e63-630">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-630">String</span></span>|  
|<span data-ttu-id="d1e63-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="d1e63-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="d1e63-632">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-632">String</span></span>|  
|<span data-ttu-id="d1e63-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="d1e63-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="d1e63-634">Int16</span><span class="sxs-lookup"><span data-stu-id="d1e63-634">Int16</span></span>|  
|<span data-ttu-id="d1e63-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="d1e63-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="d1e63-636">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-636">String</span></span>|  
|<span data-ttu-id="d1e63-637">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="d1e63-637">DESCRIPTION</span></span>|<span data-ttu-id="d1e63-638">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-638">String</span></span>|  
|<span data-ttu-id="d1e63-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="d1e63-639">DATE_CREATED</span></span>|<span data-ttu-id="d1e63-640">DateTime</span><span class="sxs-lookup"><span data-stu-id="d1e63-640">DateTime</span></span>|  
|<span data-ttu-id="d1e63-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="d1e63-641">DATE_MODIFIED</span></span>|<span data-ttu-id="d1e63-642">DateTime</span><span class="sxs-lookup"><span data-stu-id="d1e63-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="d1e63-643">Görünümler</span><span class="sxs-lookup"><span data-stu-id="d1e63-643">Views</span></span>  
  
|<span data-ttu-id="d1e63-644">Tation</span><span class="sxs-lookup"><span data-stu-id="d1e63-644">ColumnName</span></span>|<span data-ttu-id="d1e63-645">DataType</span><span class="sxs-lookup"><span data-stu-id="d1e63-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d1e63-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d1e63-646">TABLE_CATALOG</span></span>|<span data-ttu-id="d1e63-647">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-647">String</span></span>|  
|<span data-ttu-id="d1e63-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d1e63-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="d1e63-649">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-649">String</span></span>|  
|<span data-ttu-id="d1e63-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d1e63-650">TABLE_NAME</span></span>|<span data-ttu-id="d1e63-651">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-651">String</span></span>|  
|<span data-ttu-id="d1e63-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="d1e63-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="d1e63-653">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-653">String</span></span>|  
|<span data-ttu-id="d1e63-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="d1e63-654">CHECK_OPTION</span></span>|<span data-ttu-id="d1e63-655">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d1e63-655">Boolean</span></span>|  
|<span data-ttu-id="d1e63-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="d1e63-656">IS_UPDATABLE</span></span>|<span data-ttu-id="d1e63-657">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d1e63-657">Boolean</span></span>|  
|<span data-ttu-id="d1e63-658">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="d1e63-658">DESCRIPTION</span></span>|<span data-ttu-id="d1e63-659">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-659">String</span></span>|  
|<span data-ttu-id="d1e63-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="d1e63-660">DATE_CREATED</span></span>|<span data-ttu-id="d1e63-661">DateTime</span><span class="sxs-lookup"><span data-stu-id="d1e63-661">DateTime</span></span>|  
|<span data-ttu-id="d1e63-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="d1e63-662">DATE_MODIFIED</span></span>|<span data-ttu-id="d1e63-663">DateTime</span><span class="sxs-lookup"><span data-stu-id="d1e63-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="d1e63-664">Dizinlerde</span><span class="sxs-lookup"><span data-stu-id="d1e63-664">Indexes</span></span>  
  
|<span data-ttu-id="d1e63-665">Tation</span><span class="sxs-lookup"><span data-stu-id="d1e63-665">ColumnName</span></span>|<span data-ttu-id="d1e63-666">DataType</span><span class="sxs-lookup"><span data-stu-id="d1e63-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d1e63-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d1e63-667">TABLE_CATALOG</span></span>|<span data-ttu-id="d1e63-668">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-668">String</span></span>|  
|<span data-ttu-id="d1e63-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d1e63-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="d1e63-670">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-670">String</span></span>|  
|<span data-ttu-id="d1e63-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d1e63-671">TABLE_NAME</span></span>|<span data-ttu-id="d1e63-672">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-672">String</span></span>|  
|<span data-ttu-id="d1e63-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d1e63-673">INDEX_CATALOG</span></span>|<span data-ttu-id="d1e63-674">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-674">String</span></span>|  
|<span data-ttu-id="d1e63-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d1e63-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="d1e63-676">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-676">String</span></span>|  
|<span data-ttu-id="d1e63-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="d1e63-677">INDEX_NAME</span></span>|<span data-ttu-id="d1e63-678">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-678">String</span></span>|  
|<span data-ttu-id="d1e63-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="d1e63-679">PRIMARY_KEY</span></span>|<span data-ttu-id="d1e63-680">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d1e63-680">Boolean</span></span>|  
|<span data-ttu-id="d1e63-681">EŞI</span><span class="sxs-lookup"><span data-stu-id="d1e63-681">UNIQUE</span></span>|<span data-ttu-id="d1e63-682">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d1e63-682">Boolean</span></span>|  
|<span data-ttu-id="d1e63-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="d1e63-683">CLUSTERED</span></span>|<span data-ttu-id="d1e63-684">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d1e63-684">Boolean</span></span>|  
|<span data-ttu-id="d1e63-685">TÜRÜYLE</span><span class="sxs-lookup"><span data-stu-id="d1e63-685">TYPE</span></span>|<span data-ttu-id="d1e63-686">Int32</span><span class="sxs-lookup"><span data-stu-id="d1e63-686">Int32</span></span>|  
|<span data-ttu-id="d1e63-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="d1e63-687">FILL_FACTOR</span></span>|<span data-ttu-id="d1e63-688">Int32</span><span class="sxs-lookup"><span data-stu-id="d1e63-688">Int32</span></span>|  
|<span data-ttu-id="d1e63-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="d1e63-689">INITIAL_SIZE</span></span>|<span data-ttu-id="d1e63-690">Int32</span><span class="sxs-lookup"><span data-stu-id="d1e63-690">Int32</span></span>|  
|<span data-ttu-id="d1e63-691">NULLS</span><span class="sxs-lookup"><span data-stu-id="d1e63-691">NULLS</span></span>|<span data-ttu-id="d1e63-692">Int32</span><span class="sxs-lookup"><span data-stu-id="d1e63-692">Int32</span></span>|  
|<span data-ttu-id="d1e63-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="d1e63-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="d1e63-694">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d1e63-694">Boolean</span></span>|  
|<span data-ttu-id="d1e63-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="d1e63-695">AUTO_UPDATE</span></span>|<span data-ttu-id="d1e63-696">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d1e63-696">Boolean</span></span>|  
|<span data-ttu-id="d1e63-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="d1e63-697">NULL_COLLATION</span></span>|<span data-ttu-id="d1e63-698">Int32</span><span class="sxs-lookup"><span data-stu-id="d1e63-698">Int32</span></span>|  
|<span data-ttu-id="d1e63-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="d1e63-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="d1e63-700">Int64</span><span class="sxs-lookup"><span data-stu-id="d1e63-700">Int64</span></span>|  
|<span data-ttu-id="d1e63-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="d1e63-701">COLUMN_NAME</span></span>|<span data-ttu-id="d1e63-702">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-702">String</span></span>|  
|<span data-ttu-id="d1e63-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="d1e63-703">COLUMN_GUID</span></span>|<span data-ttu-id="d1e63-704">Guid</span><span class="sxs-lookup"><span data-stu-id="d1e63-704">Guid</span></span>|  
|<span data-ttu-id="d1e63-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="d1e63-705">COLUMN_PROPID</span></span>|<span data-ttu-id="d1e63-706">Int64</span><span class="sxs-lookup"><span data-stu-id="d1e63-706">Int64</span></span>|  
|<span data-ttu-id="d1e63-707">MEDIĞINDEN</span><span class="sxs-lookup"><span data-stu-id="d1e63-707">COLLATION</span></span>|<span data-ttu-id="d1e63-708">Int16</span><span class="sxs-lookup"><span data-stu-id="d1e63-708">Int16</span></span>|  
|<span data-ttu-id="d1e63-709">ITE</span><span class="sxs-lookup"><span data-stu-id="d1e63-709">CARDINALITY</span></span>|<span data-ttu-id="d1e63-710">Ondalık</span><span class="sxs-lookup"><span data-stu-id="d1e63-710">Decimal</span></span>|  
|<span data-ttu-id="d1e63-711">SAYFALARI</span><span class="sxs-lookup"><span data-stu-id="d1e63-711">PAGES</span></span>|<span data-ttu-id="d1e63-712">Int32</span><span class="sxs-lookup"><span data-stu-id="d1e63-712">Int32</span></span>|  
|<span data-ttu-id="d1e63-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="d1e63-713">FILTER_CONDITION</span></span>|<span data-ttu-id="d1e63-714">Dize</span><span class="sxs-lookup"><span data-stu-id="d1e63-714">String</span></span>|  
|<span data-ttu-id="d1e63-715">ILMIŞTIR</span><span class="sxs-lookup"><span data-stu-id="d1e63-715">INTEGRATED</span></span>|<span data-ttu-id="d1e63-716">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d1e63-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d1e63-717">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1e63-717">See also</span></span>

- [<span data-ttu-id="d1e63-718">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d1e63-718">ADO.NET Overview</span></span>](ado-net-overview.md)
