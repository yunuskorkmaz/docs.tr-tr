---
title: OLE DB Şema Koleksiyonları
ms.date: 03/30/2017
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
ms.openlocfilehash: 6dc187b0a876d9e167a74f2381db156dde2764fe
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59164690"
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="db8bb-102">OLE DB Şema Koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="db8bb-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="db8bb-103">Bu bölümde, Microsoft SQL Server, Oracle ve Microsoft Jet OLE DB sağlayıcıları için şema koleksiyonu desteğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="db8bb-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="db8bb-104">Microsoft SQL Server'ı OLE DB sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="db8bb-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="db8bb-105">Microsoft SQL Server OLE DB sürücüsü aşağıdaki özel şema koleksiyonları ortak şema koleksiyonları yanı sıra destekler:</span><span class="sxs-lookup"><span data-stu-id="db8bb-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="db8bb-106">Tabloları</span><span class="sxs-lookup"><span data-stu-id="db8bb-106">Tables</span></span>  
  
-   <span data-ttu-id="db8bb-107">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="db8bb-107">Columns</span></span>  
  
-   <span data-ttu-id="db8bb-108">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="db8bb-108">Procedures</span></span>  
  
-   <span data-ttu-id="db8bb-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="db8bb-109">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="db8bb-110">Katalog</span><span class="sxs-lookup"><span data-stu-id="db8bb-110">Catalog</span></span>  
  
-   <span data-ttu-id="db8bb-111">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="db8bb-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="db8bb-112">Tabloları</span><span class="sxs-lookup"><span data-stu-id="db8bb-112">Tables</span></span>  
  
|<span data-ttu-id="db8bb-113">ColumnName</span><span class="sxs-lookup"><span data-stu-id="db8bb-113">ColumnName</span></span>|<span data-ttu-id="db8bb-114">DataType</span><span class="sxs-lookup"><span data-stu-id="db8bb-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="db8bb-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="db8bb-115">TABLE_CATALOG</span></span>|<span data-ttu-id="db8bb-116">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-116">String</span></span>|  
|<span data-ttu-id="db8bb-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="db8bb-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="db8bb-118">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-118">String</span></span>|  
|<span data-ttu-id="db8bb-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="db8bb-119">TABLE_NAME</span></span>|<span data-ttu-id="db8bb-120">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-120">String</span></span>|  
|<span data-ttu-id="db8bb-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="db8bb-121">TABLE_TYPE</span></span>|<span data-ttu-id="db8bb-122">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-122">String</span></span>|  
|<span data-ttu-id="db8bb-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="db8bb-123">TABLE_GUID</span></span>|<span data-ttu-id="db8bb-124">Guid</span><span class="sxs-lookup"><span data-stu-id="db8bb-124">Guid</span></span>|  
|<span data-ttu-id="db8bb-125">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="db8bb-125">DESCRIPTION</span></span>|<span data-ttu-id="db8bb-126">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-126">String</span></span>|  
|<span data-ttu-id="db8bb-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="db8bb-127">TABLE_PROPID</span></span>|<span data-ttu-id="db8bb-128">Int64</span><span class="sxs-lookup"><span data-stu-id="db8bb-128">Int64</span></span>|  
|<span data-ttu-id="db8bb-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="db8bb-129">DATE_CREATED</span></span>|<span data-ttu-id="db8bb-130">DateTime</span><span class="sxs-lookup"><span data-stu-id="db8bb-130">DateTime</span></span>|  
|<span data-ttu-id="db8bb-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="db8bb-131">DATE_MODIFIED</span></span>|<span data-ttu-id="db8bb-132">DateTime</span><span class="sxs-lookup"><span data-stu-id="db8bb-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="db8bb-133">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="db8bb-133">Columns</span></span>  
  
|<span data-ttu-id="db8bb-134">ColumnName</span><span class="sxs-lookup"><span data-stu-id="db8bb-134">ColumnName</span></span>|<span data-ttu-id="db8bb-135">DataType</span><span class="sxs-lookup"><span data-stu-id="db8bb-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="db8bb-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="db8bb-136">TABLE_CATALOG</span></span>|<span data-ttu-id="db8bb-137">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-137">String</span></span>|  
|<span data-ttu-id="db8bb-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="db8bb-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="db8bb-139">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-139">String</span></span>|  
|<span data-ttu-id="db8bb-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="db8bb-140">TABLE_NAME</span></span>|<span data-ttu-id="db8bb-141">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-141">String</span></span>|  
|<span data-ttu-id="db8bb-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="db8bb-142">COLUMN_NAME</span></span>|<span data-ttu-id="db8bb-143">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-143">String</span></span>|  
|<span data-ttu-id="db8bb-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="db8bb-144">COLUMN_GUID</span></span>|<span data-ttu-id="db8bb-145">Guid</span><span class="sxs-lookup"><span data-stu-id="db8bb-145">Guid</span></span>|  
|<span data-ttu-id="db8bb-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="db8bb-146">COLUMN_PROPID</span></span>|<span data-ttu-id="db8bb-147">Int64</span><span class="sxs-lookup"><span data-stu-id="db8bb-147">Int64</span></span>|  
|<span data-ttu-id="db8bb-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="db8bb-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="db8bb-149">Int64</span><span class="sxs-lookup"><span data-stu-id="db8bb-149">Int64</span></span>|  
|<span data-ttu-id="db8bb-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="db8bb-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="db8bb-151">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="db8bb-151">Boolean</span></span>|  
|<span data-ttu-id="db8bb-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="db8bb-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="db8bb-153">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-153">String</span></span>|  
|<span data-ttu-id="db8bb-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="db8bb-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="db8bb-155">Int64</span><span class="sxs-lookup"><span data-stu-id="db8bb-155">Int64</span></span>|  
|<span data-ttu-id="db8bb-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="db8bb-156">IS_NULLABLE</span></span>|<span data-ttu-id="db8bb-157">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="db8bb-157">Boolean</span></span>|  
|<span data-ttu-id="db8bb-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="db8bb-158">DATA_TYPE</span></span>|<span data-ttu-id="db8bb-159">Int32</span><span class="sxs-lookup"><span data-stu-id="db8bb-159">Int32</span></span>|  
|<span data-ttu-id="db8bb-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="db8bb-160">TYPE_GUID</span></span>|<span data-ttu-id="db8bb-161">Guid</span><span class="sxs-lookup"><span data-stu-id="db8bb-161">Guid</span></span>|  
|<span data-ttu-id="db8bb-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="db8bb-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="db8bb-163">Int64</span><span class="sxs-lookup"><span data-stu-id="db8bb-163">Int64</span></span>|  
|<span data-ttu-id="db8bb-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="db8bb-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="db8bb-165">Int64</span><span class="sxs-lookup"><span data-stu-id="db8bb-165">Int64</span></span>|  
|<span data-ttu-id="db8bb-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="db8bb-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="db8bb-167">Int32</span><span class="sxs-lookup"><span data-stu-id="db8bb-167">Int32</span></span>|  
|<span data-ttu-id="db8bb-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="db8bb-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="db8bb-169">Int16</span><span class="sxs-lookup"><span data-stu-id="db8bb-169">Int16</span></span>|  
|<span data-ttu-id="db8bb-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="db8bb-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="db8bb-171">Int64</span><span class="sxs-lookup"><span data-stu-id="db8bb-171">Int64</span></span>|  
|<span data-ttu-id="db8bb-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="db8bb-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="db8bb-173">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-173">String</span></span>|  
|<span data-ttu-id="db8bb-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="db8bb-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="db8bb-175">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-175">String</span></span>|  
|<span data-ttu-id="db8bb-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="db8bb-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="db8bb-177">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-177">String</span></span>|  
|<span data-ttu-id="db8bb-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="db8bb-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="db8bb-179">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-179">String</span></span>|  
|<span data-ttu-id="db8bb-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="db8bb-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="db8bb-181">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-181">String</span></span>|  
|<span data-ttu-id="db8bb-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="db8bb-182">COLLATION_NAME</span></span>|<span data-ttu-id="db8bb-183">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-183">String</span></span>|  
|<span data-ttu-id="db8bb-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="db8bb-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="db8bb-185">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-185">String</span></span>|  
|<span data-ttu-id="db8bb-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="db8bb-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="db8bb-187">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-187">String</span></span>|  
|<span data-ttu-id="db8bb-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="db8bb-188">DOMAIN_NAME</span></span>|<span data-ttu-id="db8bb-189">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-189">String</span></span>|  
|<span data-ttu-id="db8bb-190">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="db8bb-190">DESCRIPTION</span></span>|<span data-ttu-id="db8bb-191">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-191">String</span></span>|  
|<span data-ttu-id="db8bb-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="db8bb-192">COLUMN_LCID</span></span>|<span data-ttu-id="db8bb-193">Int32</span><span class="sxs-lookup"><span data-stu-id="db8bb-193">Int32</span></span>|  
|<span data-ttu-id="db8bb-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="db8bb-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="db8bb-195">Int32</span><span class="sxs-lookup"><span data-stu-id="db8bb-195">Int32</span></span>|  
|<span data-ttu-id="db8bb-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="db8bb-196">COLUMN_SORTID</span></span>|<span data-ttu-id="db8bb-197">Int32</span><span class="sxs-lookup"><span data-stu-id="db8bb-197">Int32</span></span>|  
|<span data-ttu-id="db8bb-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="db8bb-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="db8bb-199">Byte[]</span><span class="sxs-lookup"><span data-stu-id="db8bb-199">Byte[]</span></span>|  
|<span data-ttu-id="db8bb-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="db8bb-200">IS_COMPUTED</span></span>|<span data-ttu-id="db8bb-201">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="db8bb-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="db8bb-202">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="db8bb-202">Procedures</span></span>  
  
|<span data-ttu-id="db8bb-203">ColumnName</span><span class="sxs-lookup"><span data-stu-id="db8bb-203">ColumnName</span></span>|<span data-ttu-id="db8bb-204">DataType</span><span class="sxs-lookup"><span data-stu-id="db8bb-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="db8bb-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="db8bb-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="db8bb-206">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-206">String</span></span>|  
|<span data-ttu-id="db8bb-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="db8bb-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="db8bb-208">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-208">String</span></span>|  
|<span data-ttu-id="db8bb-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="db8bb-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="db8bb-210">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-210">String</span></span>|  
|<span data-ttu-id="db8bb-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="db8bb-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="db8bb-212">Int16</span><span class="sxs-lookup"><span data-stu-id="db8bb-212">Int16</span></span>|  
|<span data-ttu-id="db8bb-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="db8bb-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="db8bb-214">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-214">String</span></span>|  
|<span data-ttu-id="db8bb-215">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="db8bb-215">DESCRIPTION</span></span>|<span data-ttu-id="db8bb-216">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-216">String</span></span>|  
|<span data-ttu-id="db8bb-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="db8bb-217">DATE_CREATED</span></span>|<span data-ttu-id="db8bb-218">DateTime</span><span class="sxs-lookup"><span data-stu-id="db8bb-218">DateTime</span></span>|  
|<span data-ttu-id="db8bb-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="db8bb-219">DATE_MODIFIED</span></span>|<span data-ttu-id="db8bb-220">DateTime</span><span class="sxs-lookup"><span data-stu-id="db8bb-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="db8bb-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="db8bb-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="db8bb-222">ColumnName</span><span class="sxs-lookup"><span data-stu-id="db8bb-222">ColumnName</span></span>|<span data-ttu-id="db8bb-223">DataType</span><span class="sxs-lookup"><span data-stu-id="db8bb-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="db8bb-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="db8bb-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="db8bb-225">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-225">String</span></span>|  
|<span data-ttu-id="db8bb-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="db8bb-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="db8bb-227">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-227">String</span></span>|  
|<span data-ttu-id="db8bb-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="db8bb-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="db8bb-229">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-229">String</span></span>|  
|<span data-ttu-id="db8bb-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="db8bb-230">PARAMETER_NAME</span></span>|<span data-ttu-id="db8bb-231">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-231">String</span></span>|  
|<span data-ttu-id="db8bb-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="db8bb-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="db8bb-233">Int32</span><span class="sxs-lookup"><span data-stu-id="db8bb-233">Int32</span></span>|  
|<span data-ttu-id="db8bb-234">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="db8bb-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="db8bb-235">Int32</span><span class="sxs-lookup"><span data-stu-id="db8bb-235">Int32</span></span>|  
|<span data-ttu-id="db8bb-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="db8bb-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="db8bb-237">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="db8bb-237">Boolean</span></span>|  
|<span data-ttu-id="db8bb-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="db8bb-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="db8bb-239">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-239">String</span></span>|  
|<span data-ttu-id="db8bb-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="db8bb-240">IS_NULLABLE</span></span>|<span data-ttu-id="db8bb-241">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="db8bb-241">Boolean</span></span>|  
|<span data-ttu-id="db8bb-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="db8bb-242">DATA_TYPE</span></span>|<span data-ttu-id="db8bb-243">Int32</span><span class="sxs-lookup"><span data-stu-id="db8bb-243">Int32</span></span>|  
|<span data-ttu-id="db8bb-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="db8bb-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="db8bb-245">Int64</span><span class="sxs-lookup"><span data-stu-id="db8bb-245">Int64</span></span>|  
|<span data-ttu-id="db8bb-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="db8bb-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="db8bb-247">Int64</span><span class="sxs-lookup"><span data-stu-id="db8bb-247">Int64</span></span>|  
|<span data-ttu-id="db8bb-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="db8bb-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="db8bb-249">Int32</span><span class="sxs-lookup"><span data-stu-id="db8bb-249">Int32</span></span>|  
|<span data-ttu-id="db8bb-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="db8bb-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="db8bb-251">Int16</span><span class="sxs-lookup"><span data-stu-id="db8bb-251">Int16</span></span>|  
|<span data-ttu-id="db8bb-252">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="db8bb-252">DESCRIPTION</span></span>|<span data-ttu-id="db8bb-253">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-253">String</span></span>|  
|<span data-ttu-id="db8bb-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="db8bb-254">TYPE_NAME</span></span>|<span data-ttu-id="db8bb-255">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-255">String</span></span>|  
|<span data-ttu-id="db8bb-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="db8bb-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="db8bb-257">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="db8bb-258">Katalog</span><span class="sxs-lookup"><span data-stu-id="db8bb-258">Catalog</span></span>  
  
|<span data-ttu-id="db8bb-259">ColumnName</span><span class="sxs-lookup"><span data-stu-id="db8bb-259">ColumnName</span></span>|<span data-ttu-id="db8bb-260">DataType</span><span class="sxs-lookup"><span data-stu-id="db8bb-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="db8bb-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="db8bb-261">CATALOG_NAME</span></span>|<span data-ttu-id="db8bb-262">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-262">String</span></span>|  
|<span data-ttu-id="db8bb-263">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="db8bb-263">DESCRIPTION</span></span>|<span data-ttu-id="db8bb-264">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="db8bb-265">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="db8bb-265">Indexes</span></span>  
  
|<span data-ttu-id="db8bb-266">ColumnName</span><span class="sxs-lookup"><span data-stu-id="db8bb-266">ColumnName</span></span>|<span data-ttu-id="db8bb-267">DataType</span><span class="sxs-lookup"><span data-stu-id="db8bb-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="db8bb-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="db8bb-268">TABLE_CATALOG</span></span>|<span data-ttu-id="db8bb-269">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-269">String</span></span>|  
|<span data-ttu-id="db8bb-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="db8bb-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="db8bb-271">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-271">String</span></span>|  
|<span data-ttu-id="db8bb-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="db8bb-272">TABLE_NAME</span></span>|<span data-ttu-id="db8bb-273">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-273">String</span></span>|  
|<span data-ttu-id="db8bb-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="db8bb-274">INDEX_CATALOG</span></span>|<span data-ttu-id="db8bb-275">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-275">String</span></span>|  
|<span data-ttu-id="db8bb-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="db8bb-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="db8bb-277">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-277">String</span></span>|  
|<span data-ttu-id="db8bb-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="db8bb-278">INDEX_NAME</span></span>|<span data-ttu-id="db8bb-279">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-279">String</span></span>|  
|<span data-ttu-id="db8bb-280">İŞLEM</span><span class="sxs-lookup"><span data-stu-id="db8bb-280">PRIMARY_KEY</span></span>|<span data-ttu-id="db8bb-281">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="db8bb-281">Boolean</span></span>|  
|<span data-ttu-id="db8bb-282">BENZERSİZ</span><span class="sxs-lookup"><span data-stu-id="db8bb-282">UNIQUE</span></span>|<span data-ttu-id="db8bb-283">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="db8bb-283">Boolean</span></span>|  
|<span data-ttu-id="db8bb-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="db8bb-284">CLUSTERED</span></span>|<span data-ttu-id="db8bb-285">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="db8bb-285">Boolean</span></span>|  
|<span data-ttu-id="db8bb-286">TÜRÜ</span><span class="sxs-lookup"><span data-stu-id="db8bb-286">TYPE</span></span>|<span data-ttu-id="db8bb-287">Int32</span><span class="sxs-lookup"><span data-stu-id="db8bb-287">Int32</span></span>|  
|<span data-ttu-id="db8bb-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="db8bb-288">FILL_FACTOR</span></span>|<span data-ttu-id="db8bb-289">Int32</span><span class="sxs-lookup"><span data-stu-id="db8bb-289">Int32</span></span>|  
|<span data-ttu-id="db8bb-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="db8bb-290">INITIAL_SIZE</span></span>|<span data-ttu-id="db8bb-291">Int32</span><span class="sxs-lookup"><span data-stu-id="db8bb-291">Int32</span></span>|  
|<span data-ttu-id="db8bb-292">NULLS</span><span class="sxs-lookup"><span data-stu-id="db8bb-292">NULLS</span></span>|<span data-ttu-id="db8bb-293">Int32</span><span class="sxs-lookup"><span data-stu-id="db8bb-293">Int32</span></span>|  
|<span data-ttu-id="db8bb-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="db8bb-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="db8bb-295">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="db8bb-295">Boolean</span></span>|  
|<span data-ttu-id="db8bb-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="db8bb-296">AUTO_UPDATE</span></span>|<span data-ttu-id="db8bb-297">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="db8bb-297">Boolean</span></span>|  
|<span data-ttu-id="db8bb-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="db8bb-298">NULL_COLLATION</span></span>|<span data-ttu-id="db8bb-299">Int32</span><span class="sxs-lookup"><span data-stu-id="db8bb-299">Int32</span></span>|  
|<span data-ttu-id="db8bb-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="db8bb-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="db8bb-301">Int64</span><span class="sxs-lookup"><span data-stu-id="db8bb-301">Int64</span></span>|  
|<span data-ttu-id="db8bb-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="db8bb-302">COLUMN_NAME</span></span>|<span data-ttu-id="db8bb-303">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-303">String</span></span>|  
|<span data-ttu-id="db8bb-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="db8bb-304">COLUMN_GUID</span></span>|<span data-ttu-id="db8bb-305">Guid</span><span class="sxs-lookup"><span data-stu-id="db8bb-305">Guid</span></span>|  
|<span data-ttu-id="db8bb-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="db8bb-306">COLUMN_PROPID</span></span>|<span data-ttu-id="db8bb-307">Int64</span><span class="sxs-lookup"><span data-stu-id="db8bb-307">Int64</span></span>|  
|<span data-ttu-id="db8bb-308">HARMANLAMA</span><span class="sxs-lookup"><span data-stu-id="db8bb-308">COLLATION</span></span>|<span data-ttu-id="db8bb-309">Int16</span><span class="sxs-lookup"><span data-stu-id="db8bb-309">Int16</span></span>|  
|<span data-ttu-id="db8bb-310">ÖNEM DÜZEYİ</span><span class="sxs-lookup"><span data-stu-id="db8bb-310">CARDINALITY</span></span>|<span data-ttu-id="db8bb-311">Ondalık</span><span class="sxs-lookup"><span data-stu-id="db8bb-311">Decimal</span></span>|  
|<span data-ttu-id="db8bb-312">SAYFALARI</span><span class="sxs-lookup"><span data-stu-id="db8bb-312">PAGES</span></span>|<span data-ttu-id="db8bb-313">Int32</span><span class="sxs-lookup"><span data-stu-id="db8bb-313">Int32</span></span>|  
|<span data-ttu-id="db8bb-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="db8bb-314">FILTER_CONDITION</span></span>|<span data-ttu-id="db8bb-315">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-315">String</span></span>|  
|<span data-ttu-id="db8bb-316">TÜMLEŞİK</span><span class="sxs-lookup"><span data-stu-id="db8bb-316">INTEGRATED</span></span>|<span data-ttu-id="db8bb-317">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="db8bb-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="db8bb-318">Microsoft Oracle OLE DB sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="db8bb-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="db8bb-319">Microsoft Oracle OLE DB sürücüsü aşağıdaki özel şema koleksiyonları ortak şema koleksiyonları yanı sıra destekler:</span><span class="sxs-lookup"><span data-stu-id="db8bb-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="db8bb-320">Tabloları</span><span class="sxs-lookup"><span data-stu-id="db8bb-320">Tables</span></span>  
  
-   <span data-ttu-id="db8bb-321">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="db8bb-321">Columns</span></span>  
  
-   <span data-ttu-id="db8bb-322">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="db8bb-322">Procedures</span></span>  
  
-   <span data-ttu-id="db8bb-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="db8bb-323">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="db8bb-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="db8bb-324">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="db8bb-325">Görünümler</span><span class="sxs-lookup"><span data-stu-id="db8bb-325">Views</span></span>  
  
-   <span data-ttu-id="db8bb-326">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="db8bb-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="db8bb-327">Tabloları</span><span class="sxs-lookup"><span data-stu-id="db8bb-327">Tables</span></span>  
  
|<span data-ttu-id="db8bb-328">ColumnName</span><span class="sxs-lookup"><span data-stu-id="db8bb-328">ColumnName</span></span>|<span data-ttu-id="db8bb-329">DataType</span><span class="sxs-lookup"><span data-stu-id="db8bb-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="db8bb-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="db8bb-330">TABLE_CATALOG</span></span>|<span data-ttu-id="db8bb-331">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-331">String</span></span>|  
|<span data-ttu-id="db8bb-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="db8bb-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="db8bb-333">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-333">String</span></span>|  
|<span data-ttu-id="db8bb-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="db8bb-334">TABLE_NAME</span></span>|<span data-ttu-id="db8bb-335">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-335">String</span></span>|  
|<span data-ttu-id="db8bb-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="db8bb-336">TABLE_TYPE</span></span>|<span data-ttu-id="db8bb-337">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-337">String</span></span>|  
|<span data-ttu-id="db8bb-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="db8bb-338">TABLE_GUID</span></span>|<span data-ttu-id="db8bb-339">Guid</span><span class="sxs-lookup"><span data-stu-id="db8bb-339">Guid</span></span>|  
|<span data-ttu-id="db8bb-340">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="db8bb-340">DESCRIPTION</span></span>|<span data-ttu-id="db8bb-341">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-341">String</span></span>|  
|<span data-ttu-id="db8bb-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="db8bb-342">TABLE_PROPID</span></span>|<span data-ttu-id="db8bb-343">Int64</span><span class="sxs-lookup"><span data-stu-id="db8bb-343">Int64</span></span>|  
|<span data-ttu-id="db8bb-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="db8bb-344">DATE_CREATED</span></span>|<span data-ttu-id="db8bb-345">DateTime</span><span class="sxs-lookup"><span data-stu-id="db8bb-345">DateTime</span></span>|  
|<span data-ttu-id="db8bb-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="db8bb-346">DATE_MODIFIED</span></span>|<span data-ttu-id="db8bb-347">DateTime</span><span class="sxs-lookup"><span data-stu-id="db8bb-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="db8bb-348">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="db8bb-348">Columns</span></span>  
  
|<span data-ttu-id="db8bb-349">ColumnName</span><span class="sxs-lookup"><span data-stu-id="db8bb-349">ColumnName</span></span>|<span data-ttu-id="db8bb-350">DataType</span><span class="sxs-lookup"><span data-stu-id="db8bb-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="db8bb-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="db8bb-351">TABLE_CATALOG</span></span>|<span data-ttu-id="db8bb-352">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-352">String</span></span>|  
|<span data-ttu-id="db8bb-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="db8bb-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="db8bb-354">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-354">String</span></span>|  
|<span data-ttu-id="db8bb-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="db8bb-355">TABLE_NAME</span></span>|<span data-ttu-id="db8bb-356">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-356">String</span></span>|  
|<span data-ttu-id="db8bb-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="db8bb-357">COLUMN_NAME</span></span>|<span data-ttu-id="db8bb-358">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-358">String</span></span>|  
|<span data-ttu-id="db8bb-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="db8bb-359">COLUMN_GUID</span></span>|<span data-ttu-id="db8bb-360">Guid</span><span class="sxs-lookup"><span data-stu-id="db8bb-360">Guid</span></span>|  
|<span data-ttu-id="db8bb-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="db8bb-361">COLUMN_PROPID</span></span>|<span data-ttu-id="db8bb-362">Int64</span><span class="sxs-lookup"><span data-stu-id="db8bb-362">Int64</span></span>|  
|<span data-ttu-id="db8bb-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="db8bb-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="db8bb-364">Int64</span><span class="sxs-lookup"><span data-stu-id="db8bb-364">Int64</span></span>|  
|<span data-ttu-id="db8bb-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="db8bb-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="db8bb-366">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="db8bb-366">Boolean</span></span>|  
|<span data-ttu-id="db8bb-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="db8bb-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="db8bb-368">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-368">String</span></span>|  
|<span data-ttu-id="db8bb-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="db8bb-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="db8bb-370">Int64</span><span class="sxs-lookup"><span data-stu-id="db8bb-370">Int64</span></span>|  
|<span data-ttu-id="db8bb-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="db8bb-371">IS_NULLABLE</span></span>|<span data-ttu-id="db8bb-372">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="db8bb-372">Boolean</span></span>|  
|<span data-ttu-id="db8bb-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="db8bb-373">DATA_TYPE</span></span>|<span data-ttu-id="db8bb-374">Int32</span><span class="sxs-lookup"><span data-stu-id="db8bb-374">Int32</span></span>|  
|<span data-ttu-id="db8bb-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="db8bb-375">TYPE_GUID</span></span>|<span data-ttu-id="db8bb-376">Guid</span><span class="sxs-lookup"><span data-stu-id="db8bb-376">Guid</span></span>|  
|<span data-ttu-id="db8bb-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="db8bb-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="db8bb-378">Int64</span><span class="sxs-lookup"><span data-stu-id="db8bb-378">Int64</span></span>|  
|<span data-ttu-id="db8bb-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="db8bb-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="db8bb-380">Int64</span><span class="sxs-lookup"><span data-stu-id="db8bb-380">Int64</span></span>|  
|<span data-ttu-id="db8bb-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="db8bb-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="db8bb-382">Int32</span><span class="sxs-lookup"><span data-stu-id="db8bb-382">Int32</span></span>|  
|<span data-ttu-id="db8bb-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="db8bb-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="db8bb-384">Int16</span><span class="sxs-lookup"><span data-stu-id="db8bb-384">Int16</span></span>|  
|<span data-ttu-id="db8bb-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="db8bb-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="db8bb-386">Int64</span><span class="sxs-lookup"><span data-stu-id="db8bb-386">Int64</span></span>|  
|<span data-ttu-id="db8bb-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="db8bb-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="db8bb-388">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-388">String</span></span>|  
|<span data-ttu-id="db8bb-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="db8bb-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="db8bb-390">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-390">String</span></span>|  
|<span data-ttu-id="db8bb-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="db8bb-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="db8bb-392">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-392">String</span></span>|  
|<span data-ttu-id="db8bb-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="db8bb-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="db8bb-394">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-394">String</span></span>|  
|<span data-ttu-id="db8bb-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="db8bb-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="db8bb-396">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-396">String</span></span>|  
|<span data-ttu-id="db8bb-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="db8bb-397">COLLATION_NAME</span></span>|<span data-ttu-id="db8bb-398">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-398">String</span></span>|  
|<span data-ttu-id="db8bb-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="db8bb-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="db8bb-400">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-400">String</span></span>|  
|<span data-ttu-id="db8bb-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="db8bb-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="db8bb-402">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-402">String</span></span>|  
|<span data-ttu-id="db8bb-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="db8bb-403">DOMAIN_NAME</span></span>|<span data-ttu-id="db8bb-404">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-404">String</span></span>|  
|<span data-ttu-id="db8bb-405">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="db8bb-405">DESCRIPTION</span></span>|<span data-ttu-id="db8bb-406">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="db8bb-407">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="db8bb-407">Procedures</span></span>  
  
|<span data-ttu-id="db8bb-408">ColumnName</span><span class="sxs-lookup"><span data-stu-id="db8bb-408">ColumnName</span></span>|<span data-ttu-id="db8bb-409">DataType</span><span class="sxs-lookup"><span data-stu-id="db8bb-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="db8bb-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="db8bb-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="db8bb-411">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-411">String</span></span>|  
|<span data-ttu-id="db8bb-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="db8bb-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="db8bb-413">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-413">String</span></span>|  
|<span data-ttu-id="db8bb-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="db8bb-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="db8bb-415">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-415">String</span></span>|  
|<span data-ttu-id="db8bb-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="db8bb-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="db8bb-417">Int16</span><span class="sxs-lookup"><span data-stu-id="db8bb-417">Int16</span></span>|  
|<span data-ttu-id="db8bb-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="db8bb-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="db8bb-419">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-419">String</span></span>|  
|<span data-ttu-id="db8bb-420">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="db8bb-420">DESCRIPTION</span></span>|<span data-ttu-id="db8bb-421">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-421">String</span></span>|  
|<span data-ttu-id="db8bb-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="db8bb-422">DATE_CREATED</span></span>|<span data-ttu-id="db8bb-423">DateTime</span><span class="sxs-lookup"><span data-stu-id="db8bb-423">DateTime</span></span>|  
|<span data-ttu-id="db8bb-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="db8bb-424">DATE_MODIFIED</span></span>|<span data-ttu-id="db8bb-425">DateTime</span><span class="sxs-lookup"><span data-stu-id="db8bb-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="db8bb-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="db8bb-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="db8bb-427">ColumnName</span><span class="sxs-lookup"><span data-stu-id="db8bb-427">ColumnName</span></span>|<span data-ttu-id="db8bb-428">DataType</span><span class="sxs-lookup"><span data-stu-id="db8bb-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="db8bb-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="db8bb-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="db8bb-430">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-430">String</span></span>|  
|<span data-ttu-id="db8bb-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="db8bb-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="db8bb-432">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-432">String</span></span>|  
|<span data-ttu-id="db8bb-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="db8bb-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="db8bb-434">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-434">String</span></span>|  
|<span data-ttu-id="db8bb-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="db8bb-435">COLUMN_NAME</span></span>|<span data-ttu-id="db8bb-436">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-436">String</span></span>|  
|<span data-ttu-id="db8bb-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="db8bb-437">COLUMN_GUID</span></span>|<span data-ttu-id="db8bb-438">Guid</span><span class="sxs-lookup"><span data-stu-id="db8bb-438">Guid</span></span>|  
|<span data-ttu-id="db8bb-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="db8bb-439">COLUMN_PROPID</span></span>|<span data-ttu-id="db8bb-440">Int64</span><span class="sxs-lookup"><span data-stu-id="db8bb-440">Int64</span></span>|  
|<span data-ttu-id="db8bb-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="db8bb-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="db8bb-442">Int64</span><span class="sxs-lookup"><span data-stu-id="db8bb-442">Int64</span></span>|  
|<span data-ttu-id="db8bb-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="db8bb-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="db8bb-444">Int64</span><span class="sxs-lookup"><span data-stu-id="db8bb-444">Int64</span></span>|  
|<span data-ttu-id="db8bb-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="db8bb-445">IS_NULLABLE</span></span>|<span data-ttu-id="db8bb-446">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="db8bb-446">Boolean</span></span>|  
|<span data-ttu-id="db8bb-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="db8bb-447">DATA_TYPE</span></span>|<span data-ttu-id="db8bb-448">Int32</span><span class="sxs-lookup"><span data-stu-id="db8bb-448">Int32</span></span>|  
|<span data-ttu-id="db8bb-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="db8bb-449">TYPE_GUID</span></span>|<span data-ttu-id="db8bb-450">Guid</span><span class="sxs-lookup"><span data-stu-id="db8bb-450">Guid</span></span>|  
|<span data-ttu-id="db8bb-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="db8bb-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="db8bb-452">Int64</span><span class="sxs-lookup"><span data-stu-id="db8bb-452">Int64</span></span>|  
|<span data-ttu-id="db8bb-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="db8bb-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="db8bb-454">Int64</span><span class="sxs-lookup"><span data-stu-id="db8bb-454">Int64</span></span>|  
|<span data-ttu-id="db8bb-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="db8bb-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="db8bb-456">Int32</span><span class="sxs-lookup"><span data-stu-id="db8bb-456">Int32</span></span>|  
|<span data-ttu-id="db8bb-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="db8bb-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="db8bb-458">Int16</span><span class="sxs-lookup"><span data-stu-id="db8bb-458">Int16</span></span>|  
|<span data-ttu-id="db8bb-459">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="db8bb-459">DESCRIPTION</span></span>|<span data-ttu-id="db8bb-460">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-460">String</span></span>|  
|<span data-ttu-id="db8bb-461">AŞIRI YÜKLEME</span><span class="sxs-lookup"><span data-stu-id="db8bb-461">OVERLOAD</span></span>|<span data-ttu-id="db8bb-462">Int16</span><span class="sxs-lookup"><span data-stu-id="db8bb-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="db8bb-463">Görünümler</span><span class="sxs-lookup"><span data-stu-id="db8bb-463">Views</span></span>  
  
|<span data-ttu-id="db8bb-464">ColumnName</span><span class="sxs-lookup"><span data-stu-id="db8bb-464">ColumnName</span></span>|<span data-ttu-id="db8bb-465">DataType</span><span class="sxs-lookup"><span data-stu-id="db8bb-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="db8bb-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="db8bb-466">TABLE_CATALOG</span></span>|<span data-ttu-id="db8bb-467">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-467">String</span></span>|  
|<span data-ttu-id="db8bb-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="db8bb-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="db8bb-469">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-469">String</span></span>|  
|<span data-ttu-id="db8bb-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="db8bb-470">TABLE_NAME</span></span>|<span data-ttu-id="db8bb-471">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-471">String</span></span>|  
|<span data-ttu-id="db8bb-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="db8bb-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="db8bb-473">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-473">String</span></span>|  
|<span data-ttu-id="db8bb-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="db8bb-474">CHECK_OPTION</span></span>|<span data-ttu-id="db8bb-475">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="db8bb-475">Boolean</span></span>|  
|<span data-ttu-id="db8bb-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="db8bb-476">IS_UPDATABLE</span></span>|<span data-ttu-id="db8bb-477">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="db8bb-477">Boolean</span></span>|  
|<span data-ttu-id="db8bb-478">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="db8bb-478">DESCRIPTION</span></span>|<span data-ttu-id="db8bb-479">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-479">String</span></span>|  
|<span data-ttu-id="db8bb-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="db8bb-480">DATE_CREATED</span></span>|<span data-ttu-id="db8bb-481">DateTime</span><span class="sxs-lookup"><span data-stu-id="db8bb-481">DateTime</span></span>|  
|<span data-ttu-id="db8bb-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="db8bb-482">DATE_MODIFIED</span></span>|<span data-ttu-id="db8bb-483">DateTime</span><span class="sxs-lookup"><span data-stu-id="db8bb-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="db8bb-484">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="db8bb-484">Indexes</span></span>  
  
|<span data-ttu-id="db8bb-485">ColumnName</span><span class="sxs-lookup"><span data-stu-id="db8bb-485">ColumnName</span></span>|<span data-ttu-id="db8bb-486">DataType</span><span class="sxs-lookup"><span data-stu-id="db8bb-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="db8bb-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="db8bb-487">TABLE_CATALOG</span></span>|<span data-ttu-id="db8bb-488">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-488">String</span></span>|  
|<span data-ttu-id="db8bb-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="db8bb-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="db8bb-490">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-490">String</span></span>|  
|<span data-ttu-id="db8bb-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="db8bb-491">TABLE_NAME</span></span>|<span data-ttu-id="db8bb-492">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-492">String</span></span>|  
|<span data-ttu-id="db8bb-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="db8bb-493">INDEX_CATALOG</span></span>|<span data-ttu-id="db8bb-494">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-494">String</span></span>|  
|<span data-ttu-id="db8bb-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="db8bb-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="db8bb-496">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-496">String</span></span>|  
|<span data-ttu-id="db8bb-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="db8bb-497">INDEX_NAME</span></span>|<span data-ttu-id="db8bb-498">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-498">String</span></span>|  
|<span data-ttu-id="db8bb-499">İŞLEM</span><span class="sxs-lookup"><span data-stu-id="db8bb-499">PRIMARY_KEY</span></span>|<span data-ttu-id="db8bb-500">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="db8bb-500">Boolean</span></span>|  
|<span data-ttu-id="db8bb-501">BENZERSİZ</span><span class="sxs-lookup"><span data-stu-id="db8bb-501">UNIQUE</span></span>|<span data-ttu-id="db8bb-502">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="db8bb-502">Boolean</span></span>|  
|<span data-ttu-id="db8bb-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="db8bb-503">CLUSTERED</span></span>|<span data-ttu-id="db8bb-504">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="db8bb-504">Boolean</span></span>|  
|<span data-ttu-id="db8bb-505">TÜRÜ</span><span class="sxs-lookup"><span data-stu-id="db8bb-505">TYPE</span></span>|<span data-ttu-id="db8bb-506">Int32</span><span class="sxs-lookup"><span data-stu-id="db8bb-506">Int32</span></span>|  
|<span data-ttu-id="db8bb-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="db8bb-507">FILL_FACTOR</span></span>|<span data-ttu-id="db8bb-508">Int32</span><span class="sxs-lookup"><span data-stu-id="db8bb-508">Int32</span></span>|  
|<span data-ttu-id="db8bb-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="db8bb-509">INITIAL_SIZE</span></span>|<span data-ttu-id="db8bb-510">Int32</span><span class="sxs-lookup"><span data-stu-id="db8bb-510">Int32</span></span>|  
|<span data-ttu-id="db8bb-511">NULLS</span><span class="sxs-lookup"><span data-stu-id="db8bb-511">NULLS</span></span>|<span data-ttu-id="db8bb-512">Int32</span><span class="sxs-lookup"><span data-stu-id="db8bb-512">Int32</span></span>|  
|<span data-ttu-id="db8bb-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="db8bb-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="db8bb-514">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="db8bb-514">Boolean</span></span>|  
|<span data-ttu-id="db8bb-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="db8bb-515">AUTO_UPDATE</span></span>|<span data-ttu-id="db8bb-516">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="db8bb-516">Boolean</span></span>|  
|<span data-ttu-id="db8bb-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="db8bb-517">NULL_COLLATION</span></span>|<span data-ttu-id="db8bb-518">Int32</span><span class="sxs-lookup"><span data-stu-id="db8bb-518">Int32</span></span>|  
|<span data-ttu-id="db8bb-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="db8bb-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="db8bb-520">Int64</span><span class="sxs-lookup"><span data-stu-id="db8bb-520">Int64</span></span>|  
|<span data-ttu-id="db8bb-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="db8bb-521">COLUMN_NAME</span></span>|<span data-ttu-id="db8bb-522">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-522">String</span></span>|  
|<span data-ttu-id="db8bb-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="db8bb-523">COLUMN_GUID</span></span>|<span data-ttu-id="db8bb-524">Guid</span><span class="sxs-lookup"><span data-stu-id="db8bb-524">Guid</span></span>|  
|<span data-ttu-id="db8bb-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="db8bb-525">COLUMN_PROPID</span></span>|<span data-ttu-id="db8bb-526">Int64</span><span class="sxs-lookup"><span data-stu-id="db8bb-526">Int64</span></span>|  
|<span data-ttu-id="db8bb-527">HARMANLAMA</span><span class="sxs-lookup"><span data-stu-id="db8bb-527">COLLATION</span></span>|<span data-ttu-id="db8bb-528">Int16</span><span class="sxs-lookup"><span data-stu-id="db8bb-528">Int16</span></span>|  
|<span data-ttu-id="db8bb-529">ÖNEM DÜZEYİ</span><span class="sxs-lookup"><span data-stu-id="db8bb-529">CARDINALITY</span></span>|<span data-ttu-id="db8bb-530">Ondalık</span><span class="sxs-lookup"><span data-stu-id="db8bb-530">Decimal</span></span>|  
|<span data-ttu-id="db8bb-531">SAYFALARI</span><span class="sxs-lookup"><span data-stu-id="db8bb-531">PAGES</span></span>|<span data-ttu-id="db8bb-532">Int32</span><span class="sxs-lookup"><span data-stu-id="db8bb-532">Int32</span></span>|  
|<span data-ttu-id="db8bb-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="db8bb-533">FILTER_CONDITION</span></span>|<span data-ttu-id="db8bb-534">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-534">String</span></span>|  
|<span data-ttu-id="db8bb-535">TÜMLEŞİK</span><span class="sxs-lookup"><span data-stu-id="db8bb-535">INTEGRATED</span></span>|<span data-ttu-id="db8bb-536">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="db8bb-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="db8bb-537">Microsoft Jet OLE DB sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="db8bb-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="db8bb-538">Microsoft Jet OLE DB sürücüsü aşağıdaki özel şema koleksiyonları ortak şema koleksiyonları yanı sıra destekler:</span><span class="sxs-lookup"><span data-stu-id="db8bb-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="db8bb-539">Tabloları</span><span class="sxs-lookup"><span data-stu-id="db8bb-539">Tables</span></span>  
  
-   <span data-ttu-id="db8bb-540">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="db8bb-540">Columns</span></span>  
  
-   <span data-ttu-id="db8bb-541">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="db8bb-541">Procedures</span></span>  
  
-   <span data-ttu-id="db8bb-542">Görünümler</span><span class="sxs-lookup"><span data-stu-id="db8bb-542">Views</span></span>  
  
-   <span data-ttu-id="db8bb-543">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="db8bb-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="db8bb-544">Tabloları</span><span class="sxs-lookup"><span data-stu-id="db8bb-544">Tables</span></span>  
  
|<span data-ttu-id="db8bb-545">ColumnName</span><span class="sxs-lookup"><span data-stu-id="db8bb-545">ColumnName</span></span>|<span data-ttu-id="db8bb-546">DataType</span><span class="sxs-lookup"><span data-stu-id="db8bb-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="db8bb-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="db8bb-547">TABLE_CATALOG</span></span>|<span data-ttu-id="db8bb-548">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-548">String</span></span>|  
|<span data-ttu-id="db8bb-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="db8bb-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="db8bb-550">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-550">String</span></span>|  
|<span data-ttu-id="db8bb-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="db8bb-551">TABLE_NAME</span></span>|<span data-ttu-id="db8bb-552">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-552">String</span></span>|  
|<span data-ttu-id="db8bb-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="db8bb-553">TABLE_TYPE</span></span>|<span data-ttu-id="db8bb-554">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-554">String</span></span>|  
|<span data-ttu-id="db8bb-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="db8bb-555">TABLE_GUID</span></span>|<span data-ttu-id="db8bb-556">Guid</span><span class="sxs-lookup"><span data-stu-id="db8bb-556">Guid</span></span>|  
|<span data-ttu-id="db8bb-557">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="db8bb-557">DESCRIPTION</span></span>|<span data-ttu-id="db8bb-558">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-558">String</span></span>|  
|<span data-ttu-id="db8bb-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="db8bb-559">TABLE_PROPID</span></span>|<span data-ttu-id="db8bb-560">Int64</span><span class="sxs-lookup"><span data-stu-id="db8bb-560">Int64</span></span>|  
|<span data-ttu-id="db8bb-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="db8bb-561">DATE_CREATED</span></span>|<span data-ttu-id="db8bb-562">DateTime</span><span class="sxs-lookup"><span data-stu-id="db8bb-562">DateTime</span></span>|  
|<span data-ttu-id="db8bb-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="db8bb-563">DATE_MODIFIED</span></span>|<span data-ttu-id="db8bb-564">DateTime</span><span class="sxs-lookup"><span data-stu-id="db8bb-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="db8bb-565">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="db8bb-565">Columns</span></span>  
  
|<span data-ttu-id="db8bb-566">ColumnName</span><span class="sxs-lookup"><span data-stu-id="db8bb-566">ColumnName</span></span>|<span data-ttu-id="db8bb-567">DataType</span><span class="sxs-lookup"><span data-stu-id="db8bb-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="db8bb-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="db8bb-568">TABLE_CATALOG</span></span>|<span data-ttu-id="db8bb-569">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-569">String</span></span>|  
|<span data-ttu-id="db8bb-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="db8bb-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="db8bb-571">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-571">String</span></span>|  
|<span data-ttu-id="db8bb-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="db8bb-572">TABLE_NAME</span></span>|<span data-ttu-id="db8bb-573">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-573">String</span></span>|  
|<span data-ttu-id="db8bb-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="db8bb-574">COLUMN_NAME</span></span>|<span data-ttu-id="db8bb-575">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-575">String</span></span>|  
|<span data-ttu-id="db8bb-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="db8bb-576">COLUMN_GUID</span></span>|<span data-ttu-id="db8bb-577">Guid</span><span class="sxs-lookup"><span data-stu-id="db8bb-577">Guid</span></span>|  
|<span data-ttu-id="db8bb-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="db8bb-578">COLUMN_PROPID</span></span>|<span data-ttu-id="db8bb-579">Int64</span><span class="sxs-lookup"><span data-stu-id="db8bb-579">Int64</span></span>|  
|<span data-ttu-id="db8bb-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="db8bb-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="db8bb-581">Int64</span><span class="sxs-lookup"><span data-stu-id="db8bb-581">Int64</span></span>|  
|<span data-ttu-id="db8bb-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="db8bb-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="db8bb-583">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="db8bb-583">Boolean</span></span>|  
|<span data-ttu-id="db8bb-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="db8bb-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="db8bb-585">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-585">String</span></span>|  
|<span data-ttu-id="db8bb-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="db8bb-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="db8bb-587">Int64</span><span class="sxs-lookup"><span data-stu-id="db8bb-587">Int64</span></span>|  
|<span data-ttu-id="db8bb-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="db8bb-588">IS_NULLABLE</span></span>|<span data-ttu-id="db8bb-589">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="db8bb-589">Boolean</span></span>|  
|<span data-ttu-id="db8bb-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="db8bb-590">DATA_TYPE</span></span>|<span data-ttu-id="db8bb-591">Int32</span><span class="sxs-lookup"><span data-stu-id="db8bb-591">Int32</span></span>|  
|<span data-ttu-id="db8bb-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="db8bb-592">TYPE_GUID</span></span>|<span data-ttu-id="db8bb-593">Guid</span><span class="sxs-lookup"><span data-stu-id="db8bb-593">Guid</span></span>|  
|<span data-ttu-id="db8bb-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="db8bb-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="db8bb-595">Int64</span><span class="sxs-lookup"><span data-stu-id="db8bb-595">Int64</span></span>|  
|<span data-ttu-id="db8bb-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="db8bb-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="db8bb-597">Int64</span><span class="sxs-lookup"><span data-stu-id="db8bb-597">Int64</span></span>|  
|<span data-ttu-id="db8bb-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="db8bb-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="db8bb-599">Int32</span><span class="sxs-lookup"><span data-stu-id="db8bb-599">Int32</span></span>|  
|<span data-ttu-id="db8bb-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="db8bb-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="db8bb-601">Int16</span><span class="sxs-lookup"><span data-stu-id="db8bb-601">Int16</span></span>|  
|<span data-ttu-id="db8bb-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="db8bb-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="db8bb-603">Int64</span><span class="sxs-lookup"><span data-stu-id="db8bb-603">Int64</span></span>|  
|<span data-ttu-id="db8bb-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="db8bb-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="db8bb-605">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-605">String</span></span>|  
|<span data-ttu-id="db8bb-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="db8bb-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="db8bb-607">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-607">String</span></span>|  
|<span data-ttu-id="db8bb-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="db8bb-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="db8bb-609">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-609">String</span></span>|  
|<span data-ttu-id="db8bb-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="db8bb-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="db8bb-611">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-611">String</span></span>|  
|<span data-ttu-id="db8bb-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="db8bb-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="db8bb-613">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-613">String</span></span>|  
|<span data-ttu-id="db8bb-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="db8bb-614">COLLATION_NAME</span></span>|<span data-ttu-id="db8bb-615">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-615">String</span></span>|  
|<span data-ttu-id="db8bb-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="db8bb-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="db8bb-617">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-617">String</span></span>|  
|<span data-ttu-id="db8bb-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="db8bb-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="db8bb-619">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-619">String</span></span>|  
|<span data-ttu-id="db8bb-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="db8bb-620">DOMAIN_NAME</span></span>|<span data-ttu-id="db8bb-621">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-621">String</span></span>|  
|<span data-ttu-id="db8bb-622">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="db8bb-622">DESCRIPTION</span></span>|<span data-ttu-id="db8bb-623">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="db8bb-624">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="db8bb-624">Procedures</span></span>  
  
|<span data-ttu-id="db8bb-625">ColumnName</span><span class="sxs-lookup"><span data-stu-id="db8bb-625">ColumnName</span></span>|<span data-ttu-id="db8bb-626">DataType</span><span class="sxs-lookup"><span data-stu-id="db8bb-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="db8bb-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="db8bb-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="db8bb-628">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-628">String</span></span>|  
|<span data-ttu-id="db8bb-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="db8bb-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="db8bb-630">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-630">String</span></span>|  
|<span data-ttu-id="db8bb-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="db8bb-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="db8bb-632">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-632">String</span></span>|  
|<span data-ttu-id="db8bb-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="db8bb-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="db8bb-634">Int16</span><span class="sxs-lookup"><span data-stu-id="db8bb-634">Int16</span></span>|  
|<span data-ttu-id="db8bb-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="db8bb-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="db8bb-636">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-636">String</span></span>|  
|<span data-ttu-id="db8bb-637">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="db8bb-637">DESCRIPTION</span></span>|<span data-ttu-id="db8bb-638">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-638">String</span></span>|  
|<span data-ttu-id="db8bb-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="db8bb-639">DATE_CREATED</span></span>|<span data-ttu-id="db8bb-640">DateTime</span><span class="sxs-lookup"><span data-stu-id="db8bb-640">DateTime</span></span>|  
|<span data-ttu-id="db8bb-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="db8bb-641">DATE_MODIFIED</span></span>|<span data-ttu-id="db8bb-642">DateTime</span><span class="sxs-lookup"><span data-stu-id="db8bb-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="db8bb-643">Görünümler</span><span class="sxs-lookup"><span data-stu-id="db8bb-643">Views</span></span>  
  
|<span data-ttu-id="db8bb-644">ColumnName</span><span class="sxs-lookup"><span data-stu-id="db8bb-644">ColumnName</span></span>|<span data-ttu-id="db8bb-645">DataType</span><span class="sxs-lookup"><span data-stu-id="db8bb-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="db8bb-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="db8bb-646">TABLE_CATALOG</span></span>|<span data-ttu-id="db8bb-647">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-647">String</span></span>|  
|<span data-ttu-id="db8bb-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="db8bb-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="db8bb-649">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-649">String</span></span>|  
|<span data-ttu-id="db8bb-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="db8bb-650">TABLE_NAME</span></span>|<span data-ttu-id="db8bb-651">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-651">String</span></span>|  
|<span data-ttu-id="db8bb-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="db8bb-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="db8bb-653">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-653">String</span></span>|  
|<span data-ttu-id="db8bb-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="db8bb-654">CHECK_OPTION</span></span>|<span data-ttu-id="db8bb-655">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="db8bb-655">Boolean</span></span>|  
|<span data-ttu-id="db8bb-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="db8bb-656">IS_UPDATABLE</span></span>|<span data-ttu-id="db8bb-657">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="db8bb-657">Boolean</span></span>|  
|<span data-ttu-id="db8bb-658">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="db8bb-658">DESCRIPTION</span></span>|<span data-ttu-id="db8bb-659">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-659">String</span></span>|  
|<span data-ttu-id="db8bb-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="db8bb-660">DATE_CREATED</span></span>|<span data-ttu-id="db8bb-661">DateTime</span><span class="sxs-lookup"><span data-stu-id="db8bb-661">DateTime</span></span>|  
|<span data-ttu-id="db8bb-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="db8bb-662">DATE_MODIFIED</span></span>|<span data-ttu-id="db8bb-663">DateTime</span><span class="sxs-lookup"><span data-stu-id="db8bb-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="db8bb-664">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="db8bb-664">Indexes</span></span>  
  
|<span data-ttu-id="db8bb-665">ColumnName</span><span class="sxs-lookup"><span data-stu-id="db8bb-665">ColumnName</span></span>|<span data-ttu-id="db8bb-666">DataType</span><span class="sxs-lookup"><span data-stu-id="db8bb-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="db8bb-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="db8bb-667">TABLE_CATALOG</span></span>|<span data-ttu-id="db8bb-668">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-668">String</span></span>|  
|<span data-ttu-id="db8bb-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="db8bb-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="db8bb-670">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-670">String</span></span>|  
|<span data-ttu-id="db8bb-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="db8bb-671">TABLE_NAME</span></span>|<span data-ttu-id="db8bb-672">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-672">String</span></span>|  
|<span data-ttu-id="db8bb-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="db8bb-673">INDEX_CATALOG</span></span>|<span data-ttu-id="db8bb-674">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-674">String</span></span>|  
|<span data-ttu-id="db8bb-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="db8bb-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="db8bb-676">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-676">String</span></span>|  
|<span data-ttu-id="db8bb-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="db8bb-677">INDEX_NAME</span></span>|<span data-ttu-id="db8bb-678">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-678">String</span></span>|  
|<span data-ttu-id="db8bb-679">İŞLEM</span><span class="sxs-lookup"><span data-stu-id="db8bb-679">PRIMARY_KEY</span></span>|<span data-ttu-id="db8bb-680">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="db8bb-680">Boolean</span></span>|  
|<span data-ttu-id="db8bb-681">BENZERSİZ</span><span class="sxs-lookup"><span data-stu-id="db8bb-681">UNIQUE</span></span>|<span data-ttu-id="db8bb-682">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="db8bb-682">Boolean</span></span>|  
|<span data-ttu-id="db8bb-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="db8bb-683">CLUSTERED</span></span>|<span data-ttu-id="db8bb-684">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="db8bb-684">Boolean</span></span>|  
|<span data-ttu-id="db8bb-685">TÜRÜ</span><span class="sxs-lookup"><span data-stu-id="db8bb-685">TYPE</span></span>|<span data-ttu-id="db8bb-686">Int32</span><span class="sxs-lookup"><span data-stu-id="db8bb-686">Int32</span></span>|  
|<span data-ttu-id="db8bb-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="db8bb-687">FILL_FACTOR</span></span>|<span data-ttu-id="db8bb-688">Int32</span><span class="sxs-lookup"><span data-stu-id="db8bb-688">Int32</span></span>|  
|<span data-ttu-id="db8bb-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="db8bb-689">INITIAL_SIZE</span></span>|<span data-ttu-id="db8bb-690">Int32</span><span class="sxs-lookup"><span data-stu-id="db8bb-690">Int32</span></span>|  
|<span data-ttu-id="db8bb-691">NULLS</span><span class="sxs-lookup"><span data-stu-id="db8bb-691">NULLS</span></span>|<span data-ttu-id="db8bb-692">Int32</span><span class="sxs-lookup"><span data-stu-id="db8bb-692">Int32</span></span>|  
|<span data-ttu-id="db8bb-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="db8bb-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="db8bb-694">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="db8bb-694">Boolean</span></span>|  
|<span data-ttu-id="db8bb-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="db8bb-695">AUTO_UPDATE</span></span>|<span data-ttu-id="db8bb-696">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="db8bb-696">Boolean</span></span>|  
|<span data-ttu-id="db8bb-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="db8bb-697">NULL_COLLATION</span></span>|<span data-ttu-id="db8bb-698">Int32</span><span class="sxs-lookup"><span data-stu-id="db8bb-698">Int32</span></span>|  
|<span data-ttu-id="db8bb-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="db8bb-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="db8bb-700">Int64</span><span class="sxs-lookup"><span data-stu-id="db8bb-700">Int64</span></span>|  
|<span data-ttu-id="db8bb-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="db8bb-701">COLUMN_NAME</span></span>|<span data-ttu-id="db8bb-702">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-702">String</span></span>|  
|<span data-ttu-id="db8bb-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="db8bb-703">COLUMN_GUID</span></span>|<span data-ttu-id="db8bb-704">Guid</span><span class="sxs-lookup"><span data-stu-id="db8bb-704">Guid</span></span>|  
|<span data-ttu-id="db8bb-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="db8bb-705">COLUMN_PROPID</span></span>|<span data-ttu-id="db8bb-706">Int64</span><span class="sxs-lookup"><span data-stu-id="db8bb-706">Int64</span></span>|  
|<span data-ttu-id="db8bb-707">HARMANLAMA</span><span class="sxs-lookup"><span data-stu-id="db8bb-707">COLLATION</span></span>|<span data-ttu-id="db8bb-708">Int16</span><span class="sxs-lookup"><span data-stu-id="db8bb-708">Int16</span></span>|  
|<span data-ttu-id="db8bb-709">ÖNEM DÜZEYİ</span><span class="sxs-lookup"><span data-stu-id="db8bb-709">CARDINALITY</span></span>|<span data-ttu-id="db8bb-710">Ondalık</span><span class="sxs-lookup"><span data-stu-id="db8bb-710">Decimal</span></span>|  
|<span data-ttu-id="db8bb-711">SAYFALARI</span><span class="sxs-lookup"><span data-stu-id="db8bb-711">PAGES</span></span>|<span data-ttu-id="db8bb-712">Int32</span><span class="sxs-lookup"><span data-stu-id="db8bb-712">Int32</span></span>|  
|<span data-ttu-id="db8bb-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="db8bb-713">FILTER_CONDITION</span></span>|<span data-ttu-id="db8bb-714">Dize</span><span class="sxs-lookup"><span data-stu-id="db8bb-714">String</span></span>|  
|<span data-ttu-id="db8bb-715">TÜMLEŞİK</span><span class="sxs-lookup"><span data-stu-id="db8bb-715">INTEGRATED</span></span>|<span data-ttu-id="db8bb-716">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="db8bb-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="db8bb-717">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="db8bb-717">See also</span></span>

- [<span data-ttu-id="db8bb-718">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="db8bb-718">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
