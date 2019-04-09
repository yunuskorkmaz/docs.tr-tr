---
title: OLE DB Şema Koleksiyonları
ms.date: 03/30/2017
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
ms.openlocfilehash: 6dc187b0a876d9e167a74f2381db156dde2764fe
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164690"
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="9f751-102">OLE DB Şema Koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="9f751-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="9f751-103">Bu bölümde, Microsoft SQL Server, Oracle ve Microsoft Jet OLE DB sağlayıcıları için şema koleksiyonu desteğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="9f751-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="9f751-104">Microsoft SQL Server'ı OLE DB sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="9f751-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="9f751-105">Microsoft SQL Server OLE DB sürücüsü aşağıdaki özel şema koleksiyonları ortak şema koleksiyonları yanı sıra destekler:</span><span class="sxs-lookup"><span data-stu-id="9f751-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="9f751-106">Tabloları</span><span class="sxs-lookup"><span data-stu-id="9f751-106">Tables</span></span>  
  
-   <span data-ttu-id="9f751-107">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="9f751-107">Columns</span></span>  
  
-   <span data-ttu-id="9f751-108">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="9f751-108">Procedures</span></span>  
  
-   <span data-ttu-id="9f751-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="9f751-109">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="9f751-110">Katalog</span><span class="sxs-lookup"><span data-stu-id="9f751-110">Catalog</span></span>  
  
-   <span data-ttu-id="9f751-111">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="9f751-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="9f751-112">Tabloları</span><span class="sxs-lookup"><span data-stu-id="9f751-112">Tables</span></span>  
  
|<span data-ttu-id="9f751-113">ColumnName</span><span class="sxs-lookup"><span data-stu-id="9f751-113">ColumnName</span></span>|<span data-ttu-id="9f751-114">DataType</span><span class="sxs-lookup"><span data-stu-id="9f751-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9f751-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9f751-115">TABLE_CATALOG</span></span>|<span data-ttu-id="9f751-116">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-116">String</span></span>|  
|<span data-ttu-id="9f751-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9f751-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="9f751-118">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-118">String</span></span>|  
|<span data-ttu-id="9f751-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9f751-119">TABLE_NAME</span></span>|<span data-ttu-id="9f751-120">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-120">String</span></span>|  
|<span data-ttu-id="9f751-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="9f751-121">TABLE_TYPE</span></span>|<span data-ttu-id="9f751-122">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-122">String</span></span>|  
|<span data-ttu-id="9f751-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="9f751-123">TABLE_GUID</span></span>|<span data-ttu-id="9f751-124">Guid</span><span class="sxs-lookup"><span data-stu-id="9f751-124">Guid</span></span>|  
|<span data-ttu-id="9f751-125">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="9f751-125">DESCRIPTION</span></span>|<span data-ttu-id="9f751-126">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-126">String</span></span>|  
|<span data-ttu-id="9f751-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="9f751-127">TABLE_PROPID</span></span>|<span data-ttu-id="9f751-128">Int64</span><span class="sxs-lookup"><span data-stu-id="9f751-128">Int64</span></span>|  
|<span data-ttu-id="9f751-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="9f751-129">DATE_CREATED</span></span>|<span data-ttu-id="9f751-130">DateTime</span><span class="sxs-lookup"><span data-stu-id="9f751-130">DateTime</span></span>|  
|<span data-ttu-id="9f751-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="9f751-131">DATE_MODIFIED</span></span>|<span data-ttu-id="9f751-132">DateTime</span><span class="sxs-lookup"><span data-stu-id="9f751-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="9f751-133">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="9f751-133">Columns</span></span>  
  
|<span data-ttu-id="9f751-134">ColumnName</span><span class="sxs-lookup"><span data-stu-id="9f751-134">ColumnName</span></span>|<span data-ttu-id="9f751-135">DataType</span><span class="sxs-lookup"><span data-stu-id="9f751-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9f751-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9f751-136">TABLE_CATALOG</span></span>|<span data-ttu-id="9f751-137">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-137">String</span></span>|  
|<span data-ttu-id="9f751-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9f751-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="9f751-139">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-139">String</span></span>|  
|<span data-ttu-id="9f751-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9f751-140">TABLE_NAME</span></span>|<span data-ttu-id="9f751-141">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-141">String</span></span>|  
|<span data-ttu-id="9f751-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="9f751-142">COLUMN_NAME</span></span>|<span data-ttu-id="9f751-143">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-143">String</span></span>|  
|<span data-ttu-id="9f751-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="9f751-144">COLUMN_GUID</span></span>|<span data-ttu-id="9f751-145">Guid</span><span class="sxs-lookup"><span data-stu-id="9f751-145">Guid</span></span>|  
|<span data-ttu-id="9f751-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="9f751-146">COLUMN_PROPID</span></span>|<span data-ttu-id="9f751-147">Int64</span><span class="sxs-lookup"><span data-stu-id="9f751-147">Int64</span></span>|  
|<span data-ttu-id="9f751-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="9f751-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="9f751-149">Int64</span><span class="sxs-lookup"><span data-stu-id="9f751-149">Int64</span></span>|  
|<span data-ttu-id="9f751-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="9f751-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="9f751-151">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="9f751-151">Boolean</span></span>|  
|<span data-ttu-id="9f751-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="9f751-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="9f751-153">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-153">String</span></span>|  
|<span data-ttu-id="9f751-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="9f751-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="9f751-155">Int64</span><span class="sxs-lookup"><span data-stu-id="9f751-155">Int64</span></span>|  
|<span data-ttu-id="9f751-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="9f751-156">IS_NULLABLE</span></span>|<span data-ttu-id="9f751-157">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="9f751-157">Boolean</span></span>|  
|<span data-ttu-id="9f751-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="9f751-158">DATA_TYPE</span></span>|<span data-ttu-id="9f751-159">Int32</span><span class="sxs-lookup"><span data-stu-id="9f751-159">Int32</span></span>|  
|<span data-ttu-id="9f751-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="9f751-160">TYPE_GUID</span></span>|<span data-ttu-id="9f751-161">Guid</span><span class="sxs-lookup"><span data-stu-id="9f751-161">Guid</span></span>|  
|<span data-ttu-id="9f751-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="9f751-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="9f751-163">Int64</span><span class="sxs-lookup"><span data-stu-id="9f751-163">Int64</span></span>|  
|<span data-ttu-id="9f751-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="9f751-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="9f751-165">Int64</span><span class="sxs-lookup"><span data-stu-id="9f751-165">Int64</span></span>|  
|<span data-ttu-id="9f751-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="9f751-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="9f751-167">Int32</span><span class="sxs-lookup"><span data-stu-id="9f751-167">Int32</span></span>|  
|<span data-ttu-id="9f751-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="9f751-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="9f751-169">Int16</span><span class="sxs-lookup"><span data-stu-id="9f751-169">Int16</span></span>|  
|<span data-ttu-id="9f751-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="9f751-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="9f751-171">Int64</span><span class="sxs-lookup"><span data-stu-id="9f751-171">Int64</span></span>|  
|<span data-ttu-id="9f751-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9f751-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="9f751-173">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-173">String</span></span>|  
|<span data-ttu-id="9f751-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9f751-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="9f751-175">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-175">String</span></span>|  
|<span data-ttu-id="9f751-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="9f751-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="9f751-177">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-177">String</span></span>|  
|<span data-ttu-id="9f751-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9f751-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="9f751-179">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-179">String</span></span>|  
|<span data-ttu-id="9f751-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9f751-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="9f751-181">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-181">String</span></span>|  
|<span data-ttu-id="9f751-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="9f751-182">COLLATION_NAME</span></span>|<span data-ttu-id="9f751-183">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-183">String</span></span>|  
|<span data-ttu-id="9f751-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9f751-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="9f751-185">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-185">String</span></span>|  
|<span data-ttu-id="9f751-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9f751-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="9f751-187">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-187">String</span></span>|  
|<span data-ttu-id="9f751-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="9f751-188">DOMAIN_NAME</span></span>|<span data-ttu-id="9f751-189">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-189">String</span></span>|  
|<span data-ttu-id="9f751-190">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="9f751-190">DESCRIPTION</span></span>|<span data-ttu-id="9f751-191">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-191">String</span></span>|  
|<span data-ttu-id="9f751-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="9f751-192">COLUMN_LCID</span></span>|<span data-ttu-id="9f751-193">Int32</span><span class="sxs-lookup"><span data-stu-id="9f751-193">Int32</span></span>|  
|<span data-ttu-id="9f751-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="9f751-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="9f751-195">Int32</span><span class="sxs-lookup"><span data-stu-id="9f751-195">Int32</span></span>|  
|<span data-ttu-id="9f751-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="9f751-196">COLUMN_SORTID</span></span>|<span data-ttu-id="9f751-197">Int32</span><span class="sxs-lookup"><span data-stu-id="9f751-197">Int32</span></span>|  
|<span data-ttu-id="9f751-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="9f751-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="9f751-199">Byte[]</span><span class="sxs-lookup"><span data-stu-id="9f751-199">Byte[]</span></span>|  
|<span data-ttu-id="9f751-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="9f751-200">IS_COMPUTED</span></span>|<span data-ttu-id="9f751-201">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="9f751-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="9f751-202">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="9f751-202">Procedures</span></span>  
  
|<span data-ttu-id="9f751-203">ColumnName</span><span class="sxs-lookup"><span data-stu-id="9f751-203">ColumnName</span></span>|<span data-ttu-id="9f751-204">DataType</span><span class="sxs-lookup"><span data-stu-id="9f751-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9f751-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9f751-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="9f751-206">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-206">String</span></span>|  
|<span data-ttu-id="9f751-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9f751-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="9f751-208">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-208">String</span></span>|  
|<span data-ttu-id="9f751-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="9f751-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="9f751-210">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-210">String</span></span>|  
|<span data-ttu-id="9f751-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="9f751-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="9f751-212">Int16</span><span class="sxs-lookup"><span data-stu-id="9f751-212">Int16</span></span>|  
|<span data-ttu-id="9f751-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="9f751-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="9f751-214">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-214">String</span></span>|  
|<span data-ttu-id="9f751-215">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="9f751-215">DESCRIPTION</span></span>|<span data-ttu-id="9f751-216">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-216">String</span></span>|  
|<span data-ttu-id="9f751-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="9f751-217">DATE_CREATED</span></span>|<span data-ttu-id="9f751-218">DateTime</span><span class="sxs-lookup"><span data-stu-id="9f751-218">DateTime</span></span>|  
|<span data-ttu-id="9f751-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="9f751-219">DATE_MODIFIED</span></span>|<span data-ttu-id="9f751-220">DateTime</span><span class="sxs-lookup"><span data-stu-id="9f751-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="9f751-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="9f751-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="9f751-222">ColumnName</span><span class="sxs-lookup"><span data-stu-id="9f751-222">ColumnName</span></span>|<span data-ttu-id="9f751-223">DataType</span><span class="sxs-lookup"><span data-stu-id="9f751-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9f751-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9f751-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="9f751-225">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-225">String</span></span>|  
|<span data-ttu-id="9f751-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9f751-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="9f751-227">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-227">String</span></span>|  
|<span data-ttu-id="9f751-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="9f751-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="9f751-229">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-229">String</span></span>|  
|<span data-ttu-id="9f751-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="9f751-230">PARAMETER_NAME</span></span>|<span data-ttu-id="9f751-231">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-231">String</span></span>|  
|<span data-ttu-id="9f751-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="9f751-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="9f751-233">Int32</span><span class="sxs-lookup"><span data-stu-id="9f751-233">Int32</span></span>|  
|<span data-ttu-id="9f751-234">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="9f751-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="9f751-235">Int32</span><span class="sxs-lookup"><span data-stu-id="9f751-235">Int32</span></span>|  
|<span data-ttu-id="9f751-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="9f751-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="9f751-237">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="9f751-237">Boolean</span></span>|  
|<span data-ttu-id="9f751-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="9f751-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="9f751-239">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-239">String</span></span>|  
|<span data-ttu-id="9f751-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="9f751-240">IS_NULLABLE</span></span>|<span data-ttu-id="9f751-241">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="9f751-241">Boolean</span></span>|  
|<span data-ttu-id="9f751-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="9f751-242">DATA_TYPE</span></span>|<span data-ttu-id="9f751-243">Int32</span><span class="sxs-lookup"><span data-stu-id="9f751-243">Int32</span></span>|  
|<span data-ttu-id="9f751-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="9f751-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="9f751-245">Int64</span><span class="sxs-lookup"><span data-stu-id="9f751-245">Int64</span></span>|  
|<span data-ttu-id="9f751-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="9f751-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="9f751-247">Int64</span><span class="sxs-lookup"><span data-stu-id="9f751-247">Int64</span></span>|  
|<span data-ttu-id="9f751-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="9f751-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="9f751-249">Int32</span><span class="sxs-lookup"><span data-stu-id="9f751-249">Int32</span></span>|  
|<span data-ttu-id="9f751-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="9f751-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="9f751-251">Int16</span><span class="sxs-lookup"><span data-stu-id="9f751-251">Int16</span></span>|  
|<span data-ttu-id="9f751-252">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="9f751-252">DESCRIPTION</span></span>|<span data-ttu-id="9f751-253">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-253">String</span></span>|  
|<span data-ttu-id="9f751-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="9f751-254">TYPE_NAME</span></span>|<span data-ttu-id="9f751-255">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-255">String</span></span>|  
|<span data-ttu-id="9f751-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="9f751-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="9f751-257">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="9f751-258">Katalog</span><span class="sxs-lookup"><span data-stu-id="9f751-258">Catalog</span></span>  
  
|<span data-ttu-id="9f751-259">ColumnName</span><span class="sxs-lookup"><span data-stu-id="9f751-259">ColumnName</span></span>|<span data-ttu-id="9f751-260">DataType</span><span class="sxs-lookup"><span data-stu-id="9f751-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9f751-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="9f751-261">CATALOG_NAME</span></span>|<span data-ttu-id="9f751-262">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-262">String</span></span>|  
|<span data-ttu-id="9f751-263">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="9f751-263">DESCRIPTION</span></span>|<span data-ttu-id="9f751-264">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="9f751-265">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="9f751-265">Indexes</span></span>  
  
|<span data-ttu-id="9f751-266">ColumnName</span><span class="sxs-lookup"><span data-stu-id="9f751-266">ColumnName</span></span>|<span data-ttu-id="9f751-267">DataType</span><span class="sxs-lookup"><span data-stu-id="9f751-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9f751-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9f751-268">TABLE_CATALOG</span></span>|<span data-ttu-id="9f751-269">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-269">String</span></span>|  
|<span data-ttu-id="9f751-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9f751-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="9f751-271">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-271">String</span></span>|  
|<span data-ttu-id="9f751-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9f751-272">TABLE_NAME</span></span>|<span data-ttu-id="9f751-273">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-273">String</span></span>|  
|<span data-ttu-id="9f751-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9f751-274">INDEX_CATALOG</span></span>|<span data-ttu-id="9f751-275">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-275">String</span></span>|  
|<span data-ttu-id="9f751-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9f751-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="9f751-277">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-277">String</span></span>|  
|<span data-ttu-id="9f751-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="9f751-278">INDEX_NAME</span></span>|<span data-ttu-id="9f751-279">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-279">String</span></span>|  
|<span data-ttu-id="9f751-280">İŞLEM</span><span class="sxs-lookup"><span data-stu-id="9f751-280">PRIMARY_KEY</span></span>|<span data-ttu-id="9f751-281">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="9f751-281">Boolean</span></span>|  
|<span data-ttu-id="9f751-282">BENZERSİZ</span><span class="sxs-lookup"><span data-stu-id="9f751-282">UNIQUE</span></span>|<span data-ttu-id="9f751-283">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="9f751-283">Boolean</span></span>|  
|<span data-ttu-id="9f751-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="9f751-284">CLUSTERED</span></span>|<span data-ttu-id="9f751-285">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="9f751-285">Boolean</span></span>|  
|<span data-ttu-id="9f751-286">TÜRÜ</span><span class="sxs-lookup"><span data-stu-id="9f751-286">TYPE</span></span>|<span data-ttu-id="9f751-287">Int32</span><span class="sxs-lookup"><span data-stu-id="9f751-287">Int32</span></span>|  
|<span data-ttu-id="9f751-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="9f751-288">FILL_FACTOR</span></span>|<span data-ttu-id="9f751-289">Int32</span><span class="sxs-lookup"><span data-stu-id="9f751-289">Int32</span></span>|  
|<span data-ttu-id="9f751-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="9f751-290">INITIAL_SIZE</span></span>|<span data-ttu-id="9f751-291">Int32</span><span class="sxs-lookup"><span data-stu-id="9f751-291">Int32</span></span>|  
|<span data-ttu-id="9f751-292">NULLS</span><span class="sxs-lookup"><span data-stu-id="9f751-292">NULLS</span></span>|<span data-ttu-id="9f751-293">Int32</span><span class="sxs-lookup"><span data-stu-id="9f751-293">Int32</span></span>|  
|<span data-ttu-id="9f751-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="9f751-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="9f751-295">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="9f751-295">Boolean</span></span>|  
|<span data-ttu-id="9f751-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="9f751-296">AUTO_UPDATE</span></span>|<span data-ttu-id="9f751-297">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="9f751-297">Boolean</span></span>|  
|<span data-ttu-id="9f751-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="9f751-298">NULL_COLLATION</span></span>|<span data-ttu-id="9f751-299">Int32</span><span class="sxs-lookup"><span data-stu-id="9f751-299">Int32</span></span>|  
|<span data-ttu-id="9f751-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="9f751-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="9f751-301">Int64</span><span class="sxs-lookup"><span data-stu-id="9f751-301">Int64</span></span>|  
|<span data-ttu-id="9f751-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="9f751-302">COLUMN_NAME</span></span>|<span data-ttu-id="9f751-303">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-303">String</span></span>|  
|<span data-ttu-id="9f751-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="9f751-304">COLUMN_GUID</span></span>|<span data-ttu-id="9f751-305">Guid</span><span class="sxs-lookup"><span data-stu-id="9f751-305">Guid</span></span>|  
|<span data-ttu-id="9f751-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="9f751-306">COLUMN_PROPID</span></span>|<span data-ttu-id="9f751-307">Int64</span><span class="sxs-lookup"><span data-stu-id="9f751-307">Int64</span></span>|  
|<span data-ttu-id="9f751-308">HARMANLAMA</span><span class="sxs-lookup"><span data-stu-id="9f751-308">COLLATION</span></span>|<span data-ttu-id="9f751-309">Int16</span><span class="sxs-lookup"><span data-stu-id="9f751-309">Int16</span></span>|  
|<span data-ttu-id="9f751-310">ÖNEM DÜZEYİ</span><span class="sxs-lookup"><span data-stu-id="9f751-310">CARDINALITY</span></span>|<span data-ttu-id="9f751-311">Ondalık</span><span class="sxs-lookup"><span data-stu-id="9f751-311">Decimal</span></span>|  
|<span data-ttu-id="9f751-312">SAYFALARI</span><span class="sxs-lookup"><span data-stu-id="9f751-312">PAGES</span></span>|<span data-ttu-id="9f751-313">Int32</span><span class="sxs-lookup"><span data-stu-id="9f751-313">Int32</span></span>|  
|<span data-ttu-id="9f751-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="9f751-314">FILTER_CONDITION</span></span>|<span data-ttu-id="9f751-315">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-315">String</span></span>|  
|<span data-ttu-id="9f751-316">TÜMLEŞİK</span><span class="sxs-lookup"><span data-stu-id="9f751-316">INTEGRATED</span></span>|<span data-ttu-id="9f751-317">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="9f751-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="9f751-318">Microsoft Oracle OLE DB sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="9f751-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="9f751-319">Microsoft Oracle OLE DB sürücüsü aşağıdaki özel şema koleksiyonları ortak şema koleksiyonları yanı sıra destekler:</span><span class="sxs-lookup"><span data-stu-id="9f751-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="9f751-320">Tabloları</span><span class="sxs-lookup"><span data-stu-id="9f751-320">Tables</span></span>  
  
-   <span data-ttu-id="9f751-321">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="9f751-321">Columns</span></span>  
  
-   <span data-ttu-id="9f751-322">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="9f751-322">Procedures</span></span>  
  
-   <span data-ttu-id="9f751-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="9f751-323">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="9f751-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="9f751-324">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="9f751-325">Görünümler</span><span class="sxs-lookup"><span data-stu-id="9f751-325">Views</span></span>  
  
-   <span data-ttu-id="9f751-326">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="9f751-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="9f751-327">Tabloları</span><span class="sxs-lookup"><span data-stu-id="9f751-327">Tables</span></span>  
  
|<span data-ttu-id="9f751-328">ColumnName</span><span class="sxs-lookup"><span data-stu-id="9f751-328">ColumnName</span></span>|<span data-ttu-id="9f751-329">DataType</span><span class="sxs-lookup"><span data-stu-id="9f751-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9f751-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9f751-330">TABLE_CATALOG</span></span>|<span data-ttu-id="9f751-331">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-331">String</span></span>|  
|<span data-ttu-id="9f751-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9f751-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="9f751-333">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-333">String</span></span>|  
|<span data-ttu-id="9f751-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9f751-334">TABLE_NAME</span></span>|<span data-ttu-id="9f751-335">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-335">String</span></span>|  
|<span data-ttu-id="9f751-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="9f751-336">TABLE_TYPE</span></span>|<span data-ttu-id="9f751-337">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-337">String</span></span>|  
|<span data-ttu-id="9f751-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="9f751-338">TABLE_GUID</span></span>|<span data-ttu-id="9f751-339">Guid</span><span class="sxs-lookup"><span data-stu-id="9f751-339">Guid</span></span>|  
|<span data-ttu-id="9f751-340">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="9f751-340">DESCRIPTION</span></span>|<span data-ttu-id="9f751-341">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-341">String</span></span>|  
|<span data-ttu-id="9f751-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="9f751-342">TABLE_PROPID</span></span>|<span data-ttu-id="9f751-343">Int64</span><span class="sxs-lookup"><span data-stu-id="9f751-343">Int64</span></span>|  
|<span data-ttu-id="9f751-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="9f751-344">DATE_CREATED</span></span>|<span data-ttu-id="9f751-345">DateTime</span><span class="sxs-lookup"><span data-stu-id="9f751-345">DateTime</span></span>|  
|<span data-ttu-id="9f751-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="9f751-346">DATE_MODIFIED</span></span>|<span data-ttu-id="9f751-347">DateTime</span><span class="sxs-lookup"><span data-stu-id="9f751-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="9f751-348">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="9f751-348">Columns</span></span>  
  
|<span data-ttu-id="9f751-349">ColumnName</span><span class="sxs-lookup"><span data-stu-id="9f751-349">ColumnName</span></span>|<span data-ttu-id="9f751-350">DataType</span><span class="sxs-lookup"><span data-stu-id="9f751-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9f751-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9f751-351">TABLE_CATALOG</span></span>|<span data-ttu-id="9f751-352">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-352">String</span></span>|  
|<span data-ttu-id="9f751-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9f751-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="9f751-354">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-354">String</span></span>|  
|<span data-ttu-id="9f751-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9f751-355">TABLE_NAME</span></span>|<span data-ttu-id="9f751-356">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-356">String</span></span>|  
|<span data-ttu-id="9f751-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="9f751-357">COLUMN_NAME</span></span>|<span data-ttu-id="9f751-358">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-358">String</span></span>|  
|<span data-ttu-id="9f751-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="9f751-359">COLUMN_GUID</span></span>|<span data-ttu-id="9f751-360">Guid</span><span class="sxs-lookup"><span data-stu-id="9f751-360">Guid</span></span>|  
|<span data-ttu-id="9f751-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="9f751-361">COLUMN_PROPID</span></span>|<span data-ttu-id="9f751-362">Int64</span><span class="sxs-lookup"><span data-stu-id="9f751-362">Int64</span></span>|  
|<span data-ttu-id="9f751-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="9f751-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="9f751-364">Int64</span><span class="sxs-lookup"><span data-stu-id="9f751-364">Int64</span></span>|  
|<span data-ttu-id="9f751-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="9f751-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="9f751-366">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="9f751-366">Boolean</span></span>|  
|<span data-ttu-id="9f751-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="9f751-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="9f751-368">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-368">String</span></span>|  
|<span data-ttu-id="9f751-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="9f751-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="9f751-370">Int64</span><span class="sxs-lookup"><span data-stu-id="9f751-370">Int64</span></span>|  
|<span data-ttu-id="9f751-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="9f751-371">IS_NULLABLE</span></span>|<span data-ttu-id="9f751-372">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="9f751-372">Boolean</span></span>|  
|<span data-ttu-id="9f751-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="9f751-373">DATA_TYPE</span></span>|<span data-ttu-id="9f751-374">Int32</span><span class="sxs-lookup"><span data-stu-id="9f751-374">Int32</span></span>|  
|<span data-ttu-id="9f751-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="9f751-375">TYPE_GUID</span></span>|<span data-ttu-id="9f751-376">Guid</span><span class="sxs-lookup"><span data-stu-id="9f751-376">Guid</span></span>|  
|<span data-ttu-id="9f751-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="9f751-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="9f751-378">Int64</span><span class="sxs-lookup"><span data-stu-id="9f751-378">Int64</span></span>|  
|<span data-ttu-id="9f751-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="9f751-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="9f751-380">Int64</span><span class="sxs-lookup"><span data-stu-id="9f751-380">Int64</span></span>|  
|<span data-ttu-id="9f751-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="9f751-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="9f751-382">Int32</span><span class="sxs-lookup"><span data-stu-id="9f751-382">Int32</span></span>|  
|<span data-ttu-id="9f751-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="9f751-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="9f751-384">Int16</span><span class="sxs-lookup"><span data-stu-id="9f751-384">Int16</span></span>|  
|<span data-ttu-id="9f751-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="9f751-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="9f751-386">Int64</span><span class="sxs-lookup"><span data-stu-id="9f751-386">Int64</span></span>|  
|<span data-ttu-id="9f751-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9f751-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="9f751-388">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-388">String</span></span>|  
|<span data-ttu-id="9f751-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9f751-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="9f751-390">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-390">String</span></span>|  
|<span data-ttu-id="9f751-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="9f751-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="9f751-392">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-392">String</span></span>|  
|<span data-ttu-id="9f751-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9f751-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="9f751-394">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-394">String</span></span>|  
|<span data-ttu-id="9f751-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9f751-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="9f751-396">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-396">String</span></span>|  
|<span data-ttu-id="9f751-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="9f751-397">COLLATION_NAME</span></span>|<span data-ttu-id="9f751-398">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-398">String</span></span>|  
|<span data-ttu-id="9f751-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9f751-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="9f751-400">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-400">String</span></span>|  
|<span data-ttu-id="9f751-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9f751-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="9f751-402">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-402">String</span></span>|  
|<span data-ttu-id="9f751-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="9f751-403">DOMAIN_NAME</span></span>|<span data-ttu-id="9f751-404">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-404">String</span></span>|  
|<span data-ttu-id="9f751-405">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="9f751-405">DESCRIPTION</span></span>|<span data-ttu-id="9f751-406">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="9f751-407">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="9f751-407">Procedures</span></span>  
  
|<span data-ttu-id="9f751-408">ColumnName</span><span class="sxs-lookup"><span data-stu-id="9f751-408">ColumnName</span></span>|<span data-ttu-id="9f751-409">DataType</span><span class="sxs-lookup"><span data-stu-id="9f751-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9f751-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9f751-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="9f751-411">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-411">String</span></span>|  
|<span data-ttu-id="9f751-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9f751-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="9f751-413">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-413">String</span></span>|  
|<span data-ttu-id="9f751-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="9f751-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="9f751-415">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-415">String</span></span>|  
|<span data-ttu-id="9f751-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="9f751-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="9f751-417">Int16</span><span class="sxs-lookup"><span data-stu-id="9f751-417">Int16</span></span>|  
|<span data-ttu-id="9f751-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="9f751-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="9f751-419">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-419">String</span></span>|  
|<span data-ttu-id="9f751-420">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="9f751-420">DESCRIPTION</span></span>|<span data-ttu-id="9f751-421">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-421">String</span></span>|  
|<span data-ttu-id="9f751-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="9f751-422">DATE_CREATED</span></span>|<span data-ttu-id="9f751-423">DateTime</span><span class="sxs-lookup"><span data-stu-id="9f751-423">DateTime</span></span>|  
|<span data-ttu-id="9f751-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="9f751-424">DATE_MODIFIED</span></span>|<span data-ttu-id="9f751-425">DateTime</span><span class="sxs-lookup"><span data-stu-id="9f751-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="9f751-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="9f751-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="9f751-427">ColumnName</span><span class="sxs-lookup"><span data-stu-id="9f751-427">ColumnName</span></span>|<span data-ttu-id="9f751-428">DataType</span><span class="sxs-lookup"><span data-stu-id="9f751-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9f751-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9f751-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="9f751-430">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-430">String</span></span>|  
|<span data-ttu-id="9f751-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9f751-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="9f751-432">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-432">String</span></span>|  
|<span data-ttu-id="9f751-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="9f751-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="9f751-434">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-434">String</span></span>|  
|<span data-ttu-id="9f751-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="9f751-435">COLUMN_NAME</span></span>|<span data-ttu-id="9f751-436">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-436">String</span></span>|  
|<span data-ttu-id="9f751-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="9f751-437">COLUMN_GUID</span></span>|<span data-ttu-id="9f751-438">Guid</span><span class="sxs-lookup"><span data-stu-id="9f751-438">Guid</span></span>|  
|<span data-ttu-id="9f751-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="9f751-439">COLUMN_PROPID</span></span>|<span data-ttu-id="9f751-440">Int64</span><span class="sxs-lookup"><span data-stu-id="9f751-440">Int64</span></span>|  
|<span data-ttu-id="9f751-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="9f751-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="9f751-442">Int64</span><span class="sxs-lookup"><span data-stu-id="9f751-442">Int64</span></span>|  
|<span data-ttu-id="9f751-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="9f751-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="9f751-444">Int64</span><span class="sxs-lookup"><span data-stu-id="9f751-444">Int64</span></span>|  
|<span data-ttu-id="9f751-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="9f751-445">IS_NULLABLE</span></span>|<span data-ttu-id="9f751-446">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="9f751-446">Boolean</span></span>|  
|<span data-ttu-id="9f751-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="9f751-447">DATA_TYPE</span></span>|<span data-ttu-id="9f751-448">Int32</span><span class="sxs-lookup"><span data-stu-id="9f751-448">Int32</span></span>|  
|<span data-ttu-id="9f751-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="9f751-449">TYPE_GUID</span></span>|<span data-ttu-id="9f751-450">Guid</span><span class="sxs-lookup"><span data-stu-id="9f751-450">Guid</span></span>|  
|<span data-ttu-id="9f751-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="9f751-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="9f751-452">Int64</span><span class="sxs-lookup"><span data-stu-id="9f751-452">Int64</span></span>|  
|<span data-ttu-id="9f751-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="9f751-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="9f751-454">Int64</span><span class="sxs-lookup"><span data-stu-id="9f751-454">Int64</span></span>|  
|<span data-ttu-id="9f751-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="9f751-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="9f751-456">Int32</span><span class="sxs-lookup"><span data-stu-id="9f751-456">Int32</span></span>|  
|<span data-ttu-id="9f751-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="9f751-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="9f751-458">Int16</span><span class="sxs-lookup"><span data-stu-id="9f751-458">Int16</span></span>|  
|<span data-ttu-id="9f751-459">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="9f751-459">DESCRIPTION</span></span>|<span data-ttu-id="9f751-460">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-460">String</span></span>|  
|<span data-ttu-id="9f751-461">AŞIRI YÜKLEME</span><span class="sxs-lookup"><span data-stu-id="9f751-461">OVERLOAD</span></span>|<span data-ttu-id="9f751-462">Int16</span><span class="sxs-lookup"><span data-stu-id="9f751-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="9f751-463">Görünümler</span><span class="sxs-lookup"><span data-stu-id="9f751-463">Views</span></span>  
  
|<span data-ttu-id="9f751-464">ColumnName</span><span class="sxs-lookup"><span data-stu-id="9f751-464">ColumnName</span></span>|<span data-ttu-id="9f751-465">DataType</span><span class="sxs-lookup"><span data-stu-id="9f751-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9f751-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9f751-466">TABLE_CATALOG</span></span>|<span data-ttu-id="9f751-467">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-467">String</span></span>|  
|<span data-ttu-id="9f751-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9f751-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="9f751-469">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-469">String</span></span>|  
|<span data-ttu-id="9f751-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9f751-470">TABLE_NAME</span></span>|<span data-ttu-id="9f751-471">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-471">String</span></span>|  
|<span data-ttu-id="9f751-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="9f751-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="9f751-473">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-473">String</span></span>|  
|<span data-ttu-id="9f751-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="9f751-474">CHECK_OPTION</span></span>|<span data-ttu-id="9f751-475">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="9f751-475">Boolean</span></span>|  
|<span data-ttu-id="9f751-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="9f751-476">IS_UPDATABLE</span></span>|<span data-ttu-id="9f751-477">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="9f751-477">Boolean</span></span>|  
|<span data-ttu-id="9f751-478">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="9f751-478">DESCRIPTION</span></span>|<span data-ttu-id="9f751-479">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-479">String</span></span>|  
|<span data-ttu-id="9f751-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="9f751-480">DATE_CREATED</span></span>|<span data-ttu-id="9f751-481">DateTime</span><span class="sxs-lookup"><span data-stu-id="9f751-481">DateTime</span></span>|  
|<span data-ttu-id="9f751-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="9f751-482">DATE_MODIFIED</span></span>|<span data-ttu-id="9f751-483">DateTime</span><span class="sxs-lookup"><span data-stu-id="9f751-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="9f751-484">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="9f751-484">Indexes</span></span>  
  
|<span data-ttu-id="9f751-485">ColumnName</span><span class="sxs-lookup"><span data-stu-id="9f751-485">ColumnName</span></span>|<span data-ttu-id="9f751-486">DataType</span><span class="sxs-lookup"><span data-stu-id="9f751-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9f751-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9f751-487">TABLE_CATALOG</span></span>|<span data-ttu-id="9f751-488">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-488">String</span></span>|  
|<span data-ttu-id="9f751-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9f751-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="9f751-490">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-490">String</span></span>|  
|<span data-ttu-id="9f751-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9f751-491">TABLE_NAME</span></span>|<span data-ttu-id="9f751-492">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-492">String</span></span>|  
|<span data-ttu-id="9f751-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9f751-493">INDEX_CATALOG</span></span>|<span data-ttu-id="9f751-494">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-494">String</span></span>|  
|<span data-ttu-id="9f751-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9f751-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="9f751-496">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-496">String</span></span>|  
|<span data-ttu-id="9f751-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="9f751-497">INDEX_NAME</span></span>|<span data-ttu-id="9f751-498">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-498">String</span></span>|  
|<span data-ttu-id="9f751-499">İŞLEM</span><span class="sxs-lookup"><span data-stu-id="9f751-499">PRIMARY_KEY</span></span>|<span data-ttu-id="9f751-500">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="9f751-500">Boolean</span></span>|  
|<span data-ttu-id="9f751-501">BENZERSİZ</span><span class="sxs-lookup"><span data-stu-id="9f751-501">UNIQUE</span></span>|<span data-ttu-id="9f751-502">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="9f751-502">Boolean</span></span>|  
|<span data-ttu-id="9f751-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="9f751-503">CLUSTERED</span></span>|<span data-ttu-id="9f751-504">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="9f751-504">Boolean</span></span>|  
|<span data-ttu-id="9f751-505">TÜRÜ</span><span class="sxs-lookup"><span data-stu-id="9f751-505">TYPE</span></span>|<span data-ttu-id="9f751-506">Int32</span><span class="sxs-lookup"><span data-stu-id="9f751-506">Int32</span></span>|  
|<span data-ttu-id="9f751-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="9f751-507">FILL_FACTOR</span></span>|<span data-ttu-id="9f751-508">Int32</span><span class="sxs-lookup"><span data-stu-id="9f751-508">Int32</span></span>|  
|<span data-ttu-id="9f751-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="9f751-509">INITIAL_SIZE</span></span>|<span data-ttu-id="9f751-510">Int32</span><span class="sxs-lookup"><span data-stu-id="9f751-510">Int32</span></span>|  
|<span data-ttu-id="9f751-511">NULLS</span><span class="sxs-lookup"><span data-stu-id="9f751-511">NULLS</span></span>|<span data-ttu-id="9f751-512">Int32</span><span class="sxs-lookup"><span data-stu-id="9f751-512">Int32</span></span>|  
|<span data-ttu-id="9f751-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="9f751-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="9f751-514">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="9f751-514">Boolean</span></span>|  
|<span data-ttu-id="9f751-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="9f751-515">AUTO_UPDATE</span></span>|<span data-ttu-id="9f751-516">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="9f751-516">Boolean</span></span>|  
|<span data-ttu-id="9f751-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="9f751-517">NULL_COLLATION</span></span>|<span data-ttu-id="9f751-518">Int32</span><span class="sxs-lookup"><span data-stu-id="9f751-518">Int32</span></span>|  
|<span data-ttu-id="9f751-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="9f751-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="9f751-520">Int64</span><span class="sxs-lookup"><span data-stu-id="9f751-520">Int64</span></span>|  
|<span data-ttu-id="9f751-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="9f751-521">COLUMN_NAME</span></span>|<span data-ttu-id="9f751-522">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-522">String</span></span>|  
|<span data-ttu-id="9f751-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="9f751-523">COLUMN_GUID</span></span>|<span data-ttu-id="9f751-524">Guid</span><span class="sxs-lookup"><span data-stu-id="9f751-524">Guid</span></span>|  
|<span data-ttu-id="9f751-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="9f751-525">COLUMN_PROPID</span></span>|<span data-ttu-id="9f751-526">Int64</span><span class="sxs-lookup"><span data-stu-id="9f751-526">Int64</span></span>|  
|<span data-ttu-id="9f751-527">HARMANLAMA</span><span class="sxs-lookup"><span data-stu-id="9f751-527">COLLATION</span></span>|<span data-ttu-id="9f751-528">Int16</span><span class="sxs-lookup"><span data-stu-id="9f751-528">Int16</span></span>|  
|<span data-ttu-id="9f751-529">ÖNEM DÜZEYİ</span><span class="sxs-lookup"><span data-stu-id="9f751-529">CARDINALITY</span></span>|<span data-ttu-id="9f751-530">Ondalık</span><span class="sxs-lookup"><span data-stu-id="9f751-530">Decimal</span></span>|  
|<span data-ttu-id="9f751-531">SAYFALARI</span><span class="sxs-lookup"><span data-stu-id="9f751-531">PAGES</span></span>|<span data-ttu-id="9f751-532">Int32</span><span class="sxs-lookup"><span data-stu-id="9f751-532">Int32</span></span>|  
|<span data-ttu-id="9f751-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="9f751-533">FILTER_CONDITION</span></span>|<span data-ttu-id="9f751-534">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-534">String</span></span>|  
|<span data-ttu-id="9f751-535">TÜMLEŞİK</span><span class="sxs-lookup"><span data-stu-id="9f751-535">INTEGRATED</span></span>|<span data-ttu-id="9f751-536">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="9f751-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="9f751-537">Microsoft Jet OLE DB sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="9f751-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="9f751-538">Microsoft Jet OLE DB sürücüsü aşağıdaki özel şema koleksiyonları ortak şema koleksiyonları yanı sıra destekler:</span><span class="sxs-lookup"><span data-stu-id="9f751-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="9f751-539">Tabloları</span><span class="sxs-lookup"><span data-stu-id="9f751-539">Tables</span></span>  
  
-   <span data-ttu-id="9f751-540">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="9f751-540">Columns</span></span>  
  
-   <span data-ttu-id="9f751-541">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="9f751-541">Procedures</span></span>  
  
-   <span data-ttu-id="9f751-542">Görünümler</span><span class="sxs-lookup"><span data-stu-id="9f751-542">Views</span></span>  
  
-   <span data-ttu-id="9f751-543">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="9f751-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="9f751-544">Tabloları</span><span class="sxs-lookup"><span data-stu-id="9f751-544">Tables</span></span>  
  
|<span data-ttu-id="9f751-545">ColumnName</span><span class="sxs-lookup"><span data-stu-id="9f751-545">ColumnName</span></span>|<span data-ttu-id="9f751-546">DataType</span><span class="sxs-lookup"><span data-stu-id="9f751-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9f751-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9f751-547">TABLE_CATALOG</span></span>|<span data-ttu-id="9f751-548">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-548">String</span></span>|  
|<span data-ttu-id="9f751-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9f751-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="9f751-550">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-550">String</span></span>|  
|<span data-ttu-id="9f751-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9f751-551">TABLE_NAME</span></span>|<span data-ttu-id="9f751-552">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-552">String</span></span>|  
|<span data-ttu-id="9f751-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="9f751-553">TABLE_TYPE</span></span>|<span data-ttu-id="9f751-554">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-554">String</span></span>|  
|<span data-ttu-id="9f751-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="9f751-555">TABLE_GUID</span></span>|<span data-ttu-id="9f751-556">Guid</span><span class="sxs-lookup"><span data-stu-id="9f751-556">Guid</span></span>|  
|<span data-ttu-id="9f751-557">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="9f751-557">DESCRIPTION</span></span>|<span data-ttu-id="9f751-558">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-558">String</span></span>|  
|<span data-ttu-id="9f751-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="9f751-559">TABLE_PROPID</span></span>|<span data-ttu-id="9f751-560">Int64</span><span class="sxs-lookup"><span data-stu-id="9f751-560">Int64</span></span>|  
|<span data-ttu-id="9f751-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="9f751-561">DATE_CREATED</span></span>|<span data-ttu-id="9f751-562">DateTime</span><span class="sxs-lookup"><span data-stu-id="9f751-562">DateTime</span></span>|  
|<span data-ttu-id="9f751-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="9f751-563">DATE_MODIFIED</span></span>|<span data-ttu-id="9f751-564">DateTime</span><span class="sxs-lookup"><span data-stu-id="9f751-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="9f751-565">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="9f751-565">Columns</span></span>  
  
|<span data-ttu-id="9f751-566">ColumnName</span><span class="sxs-lookup"><span data-stu-id="9f751-566">ColumnName</span></span>|<span data-ttu-id="9f751-567">DataType</span><span class="sxs-lookup"><span data-stu-id="9f751-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9f751-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9f751-568">TABLE_CATALOG</span></span>|<span data-ttu-id="9f751-569">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-569">String</span></span>|  
|<span data-ttu-id="9f751-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9f751-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="9f751-571">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-571">String</span></span>|  
|<span data-ttu-id="9f751-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9f751-572">TABLE_NAME</span></span>|<span data-ttu-id="9f751-573">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-573">String</span></span>|  
|<span data-ttu-id="9f751-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="9f751-574">COLUMN_NAME</span></span>|<span data-ttu-id="9f751-575">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-575">String</span></span>|  
|<span data-ttu-id="9f751-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="9f751-576">COLUMN_GUID</span></span>|<span data-ttu-id="9f751-577">Guid</span><span class="sxs-lookup"><span data-stu-id="9f751-577">Guid</span></span>|  
|<span data-ttu-id="9f751-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="9f751-578">COLUMN_PROPID</span></span>|<span data-ttu-id="9f751-579">Int64</span><span class="sxs-lookup"><span data-stu-id="9f751-579">Int64</span></span>|  
|<span data-ttu-id="9f751-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="9f751-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="9f751-581">Int64</span><span class="sxs-lookup"><span data-stu-id="9f751-581">Int64</span></span>|  
|<span data-ttu-id="9f751-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="9f751-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="9f751-583">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="9f751-583">Boolean</span></span>|  
|<span data-ttu-id="9f751-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="9f751-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="9f751-585">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-585">String</span></span>|  
|<span data-ttu-id="9f751-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="9f751-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="9f751-587">Int64</span><span class="sxs-lookup"><span data-stu-id="9f751-587">Int64</span></span>|  
|<span data-ttu-id="9f751-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="9f751-588">IS_NULLABLE</span></span>|<span data-ttu-id="9f751-589">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="9f751-589">Boolean</span></span>|  
|<span data-ttu-id="9f751-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="9f751-590">DATA_TYPE</span></span>|<span data-ttu-id="9f751-591">Int32</span><span class="sxs-lookup"><span data-stu-id="9f751-591">Int32</span></span>|  
|<span data-ttu-id="9f751-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="9f751-592">TYPE_GUID</span></span>|<span data-ttu-id="9f751-593">Guid</span><span class="sxs-lookup"><span data-stu-id="9f751-593">Guid</span></span>|  
|<span data-ttu-id="9f751-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="9f751-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="9f751-595">Int64</span><span class="sxs-lookup"><span data-stu-id="9f751-595">Int64</span></span>|  
|<span data-ttu-id="9f751-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="9f751-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="9f751-597">Int64</span><span class="sxs-lookup"><span data-stu-id="9f751-597">Int64</span></span>|  
|<span data-ttu-id="9f751-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="9f751-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="9f751-599">Int32</span><span class="sxs-lookup"><span data-stu-id="9f751-599">Int32</span></span>|  
|<span data-ttu-id="9f751-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="9f751-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="9f751-601">Int16</span><span class="sxs-lookup"><span data-stu-id="9f751-601">Int16</span></span>|  
|<span data-ttu-id="9f751-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="9f751-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="9f751-603">Int64</span><span class="sxs-lookup"><span data-stu-id="9f751-603">Int64</span></span>|  
|<span data-ttu-id="9f751-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9f751-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="9f751-605">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-605">String</span></span>|  
|<span data-ttu-id="9f751-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9f751-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="9f751-607">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-607">String</span></span>|  
|<span data-ttu-id="9f751-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="9f751-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="9f751-609">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-609">String</span></span>|  
|<span data-ttu-id="9f751-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9f751-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="9f751-611">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-611">String</span></span>|  
|<span data-ttu-id="9f751-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9f751-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="9f751-613">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-613">String</span></span>|  
|<span data-ttu-id="9f751-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="9f751-614">COLLATION_NAME</span></span>|<span data-ttu-id="9f751-615">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-615">String</span></span>|  
|<span data-ttu-id="9f751-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9f751-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="9f751-617">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-617">String</span></span>|  
|<span data-ttu-id="9f751-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9f751-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="9f751-619">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-619">String</span></span>|  
|<span data-ttu-id="9f751-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="9f751-620">DOMAIN_NAME</span></span>|<span data-ttu-id="9f751-621">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-621">String</span></span>|  
|<span data-ttu-id="9f751-622">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="9f751-622">DESCRIPTION</span></span>|<span data-ttu-id="9f751-623">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="9f751-624">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="9f751-624">Procedures</span></span>  
  
|<span data-ttu-id="9f751-625">ColumnName</span><span class="sxs-lookup"><span data-stu-id="9f751-625">ColumnName</span></span>|<span data-ttu-id="9f751-626">DataType</span><span class="sxs-lookup"><span data-stu-id="9f751-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9f751-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9f751-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="9f751-628">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-628">String</span></span>|  
|<span data-ttu-id="9f751-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9f751-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="9f751-630">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-630">String</span></span>|  
|<span data-ttu-id="9f751-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="9f751-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="9f751-632">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-632">String</span></span>|  
|<span data-ttu-id="9f751-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="9f751-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="9f751-634">Int16</span><span class="sxs-lookup"><span data-stu-id="9f751-634">Int16</span></span>|  
|<span data-ttu-id="9f751-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="9f751-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="9f751-636">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-636">String</span></span>|  
|<span data-ttu-id="9f751-637">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="9f751-637">DESCRIPTION</span></span>|<span data-ttu-id="9f751-638">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-638">String</span></span>|  
|<span data-ttu-id="9f751-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="9f751-639">DATE_CREATED</span></span>|<span data-ttu-id="9f751-640">DateTime</span><span class="sxs-lookup"><span data-stu-id="9f751-640">DateTime</span></span>|  
|<span data-ttu-id="9f751-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="9f751-641">DATE_MODIFIED</span></span>|<span data-ttu-id="9f751-642">DateTime</span><span class="sxs-lookup"><span data-stu-id="9f751-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="9f751-643">Görünümler</span><span class="sxs-lookup"><span data-stu-id="9f751-643">Views</span></span>  
  
|<span data-ttu-id="9f751-644">ColumnName</span><span class="sxs-lookup"><span data-stu-id="9f751-644">ColumnName</span></span>|<span data-ttu-id="9f751-645">DataType</span><span class="sxs-lookup"><span data-stu-id="9f751-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9f751-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9f751-646">TABLE_CATALOG</span></span>|<span data-ttu-id="9f751-647">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-647">String</span></span>|  
|<span data-ttu-id="9f751-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9f751-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="9f751-649">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-649">String</span></span>|  
|<span data-ttu-id="9f751-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9f751-650">TABLE_NAME</span></span>|<span data-ttu-id="9f751-651">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-651">String</span></span>|  
|<span data-ttu-id="9f751-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="9f751-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="9f751-653">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-653">String</span></span>|  
|<span data-ttu-id="9f751-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="9f751-654">CHECK_OPTION</span></span>|<span data-ttu-id="9f751-655">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="9f751-655">Boolean</span></span>|  
|<span data-ttu-id="9f751-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="9f751-656">IS_UPDATABLE</span></span>|<span data-ttu-id="9f751-657">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="9f751-657">Boolean</span></span>|  
|<span data-ttu-id="9f751-658">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="9f751-658">DESCRIPTION</span></span>|<span data-ttu-id="9f751-659">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-659">String</span></span>|  
|<span data-ttu-id="9f751-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="9f751-660">DATE_CREATED</span></span>|<span data-ttu-id="9f751-661">DateTime</span><span class="sxs-lookup"><span data-stu-id="9f751-661">DateTime</span></span>|  
|<span data-ttu-id="9f751-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="9f751-662">DATE_MODIFIED</span></span>|<span data-ttu-id="9f751-663">DateTime</span><span class="sxs-lookup"><span data-stu-id="9f751-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="9f751-664">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="9f751-664">Indexes</span></span>  
  
|<span data-ttu-id="9f751-665">ColumnName</span><span class="sxs-lookup"><span data-stu-id="9f751-665">ColumnName</span></span>|<span data-ttu-id="9f751-666">DataType</span><span class="sxs-lookup"><span data-stu-id="9f751-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9f751-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9f751-667">TABLE_CATALOG</span></span>|<span data-ttu-id="9f751-668">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-668">String</span></span>|  
|<span data-ttu-id="9f751-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9f751-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="9f751-670">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-670">String</span></span>|  
|<span data-ttu-id="9f751-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9f751-671">TABLE_NAME</span></span>|<span data-ttu-id="9f751-672">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-672">String</span></span>|  
|<span data-ttu-id="9f751-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9f751-673">INDEX_CATALOG</span></span>|<span data-ttu-id="9f751-674">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-674">String</span></span>|  
|<span data-ttu-id="9f751-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9f751-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="9f751-676">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-676">String</span></span>|  
|<span data-ttu-id="9f751-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="9f751-677">INDEX_NAME</span></span>|<span data-ttu-id="9f751-678">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-678">String</span></span>|  
|<span data-ttu-id="9f751-679">İŞLEM</span><span class="sxs-lookup"><span data-stu-id="9f751-679">PRIMARY_KEY</span></span>|<span data-ttu-id="9f751-680">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="9f751-680">Boolean</span></span>|  
|<span data-ttu-id="9f751-681">BENZERSİZ</span><span class="sxs-lookup"><span data-stu-id="9f751-681">UNIQUE</span></span>|<span data-ttu-id="9f751-682">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="9f751-682">Boolean</span></span>|  
|<span data-ttu-id="9f751-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="9f751-683">CLUSTERED</span></span>|<span data-ttu-id="9f751-684">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="9f751-684">Boolean</span></span>|  
|<span data-ttu-id="9f751-685">TÜRÜ</span><span class="sxs-lookup"><span data-stu-id="9f751-685">TYPE</span></span>|<span data-ttu-id="9f751-686">Int32</span><span class="sxs-lookup"><span data-stu-id="9f751-686">Int32</span></span>|  
|<span data-ttu-id="9f751-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="9f751-687">FILL_FACTOR</span></span>|<span data-ttu-id="9f751-688">Int32</span><span class="sxs-lookup"><span data-stu-id="9f751-688">Int32</span></span>|  
|<span data-ttu-id="9f751-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="9f751-689">INITIAL_SIZE</span></span>|<span data-ttu-id="9f751-690">Int32</span><span class="sxs-lookup"><span data-stu-id="9f751-690">Int32</span></span>|  
|<span data-ttu-id="9f751-691">NULLS</span><span class="sxs-lookup"><span data-stu-id="9f751-691">NULLS</span></span>|<span data-ttu-id="9f751-692">Int32</span><span class="sxs-lookup"><span data-stu-id="9f751-692">Int32</span></span>|  
|<span data-ttu-id="9f751-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="9f751-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="9f751-694">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="9f751-694">Boolean</span></span>|  
|<span data-ttu-id="9f751-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="9f751-695">AUTO_UPDATE</span></span>|<span data-ttu-id="9f751-696">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="9f751-696">Boolean</span></span>|  
|<span data-ttu-id="9f751-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="9f751-697">NULL_COLLATION</span></span>|<span data-ttu-id="9f751-698">Int32</span><span class="sxs-lookup"><span data-stu-id="9f751-698">Int32</span></span>|  
|<span data-ttu-id="9f751-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="9f751-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="9f751-700">Int64</span><span class="sxs-lookup"><span data-stu-id="9f751-700">Int64</span></span>|  
|<span data-ttu-id="9f751-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="9f751-701">COLUMN_NAME</span></span>|<span data-ttu-id="9f751-702">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-702">String</span></span>|  
|<span data-ttu-id="9f751-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="9f751-703">COLUMN_GUID</span></span>|<span data-ttu-id="9f751-704">Guid</span><span class="sxs-lookup"><span data-stu-id="9f751-704">Guid</span></span>|  
|<span data-ttu-id="9f751-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="9f751-705">COLUMN_PROPID</span></span>|<span data-ttu-id="9f751-706">Int64</span><span class="sxs-lookup"><span data-stu-id="9f751-706">Int64</span></span>|  
|<span data-ttu-id="9f751-707">HARMANLAMA</span><span class="sxs-lookup"><span data-stu-id="9f751-707">COLLATION</span></span>|<span data-ttu-id="9f751-708">Int16</span><span class="sxs-lookup"><span data-stu-id="9f751-708">Int16</span></span>|  
|<span data-ttu-id="9f751-709">ÖNEM DÜZEYİ</span><span class="sxs-lookup"><span data-stu-id="9f751-709">CARDINALITY</span></span>|<span data-ttu-id="9f751-710">Ondalık</span><span class="sxs-lookup"><span data-stu-id="9f751-710">Decimal</span></span>|  
|<span data-ttu-id="9f751-711">SAYFALARI</span><span class="sxs-lookup"><span data-stu-id="9f751-711">PAGES</span></span>|<span data-ttu-id="9f751-712">Int32</span><span class="sxs-lookup"><span data-stu-id="9f751-712">Int32</span></span>|  
|<span data-ttu-id="9f751-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="9f751-713">FILTER_CONDITION</span></span>|<span data-ttu-id="9f751-714">Dize</span><span class="sxs-lookup"><span data-stu-id="9f751-714">String</span></span>|  
|<span data-ttu-id="9f751-715">TÜMLEŞİK</span><span class="sxs-lookup"><span data-stu-id="9f751-715">INTEGRATED</span></span>|<span data-ttu-id="9f751-716">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="9f751-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9f751-717">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f751-717">See also</span></span>

- [<span data-ttu-id="9f751-718">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="9f751-718">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
