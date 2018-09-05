---
title: OLE DB şema koleksiyonları
ms.date: 03/30/2017
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
ms.openlocfilehash: 1ab6426875b73b400a59b7e4cf155615d7472d05
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43514495"
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="d504d-102">OLE DB şema koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="d504d-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="d504d-103">Bu bölümde, Microsoft SQL Server, Oracle ve Microsoft Jet OLE DB sağlayıcıları için şema koleksiyonu desteğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="d504d-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="d504d-104">Microsoft SQL Server'ı OLE DB sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="d504d-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="d504d-105">Microsoft SQL Server OLE DB sürücüsü aşağıdaki özel şema koleksiyonları ortak şema koleksiyonları yanı sıra destekler:</span><span class="sxs-lookup"><span data-stu-id="d504d-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="d504d-106">Tabloları</span><span class="sxs-lookup"><span data-stu-id="d504d-106">Tables</span></span>  
  
-   <span data-ttu-id="d504d-107">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="d504d-107">Columns</span></span>  
  
-   <span data-ttu-id="d504d-108">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="d504d-108">Procedures</span></span>  
  
-   <span data-ttu-id="d504d-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="d504d-109">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="d504d-110">Kataloğu</span><span class="sxs-lookup"><span data-stu-id="d504d-110">Catalog</span></span>  
  
-   <span data-ttu-id="d504d-111">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="d504d-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="d504d-112">Tabloları</span><span class="sxs-lookup"><span data-stu-id="d504d-112">Tables</span></span>  
  
|<span data-ttu-id="d504d-113">ColumnName</span><span class="sxs-lookup"><span data-stu-id="d504d-113">ColumnName</span></span>|<span data-ttu-id="d504d-114">Veri türü</span><span class="sxs-lookup"><span data-stu-id="d504d-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d504d-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d504d-115">TABLE_CATALOG</span></span>|<span data-ttu-id="d504d-116">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-116">String</span></span>|  
|<span data-ttu-id="d504d-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d504d-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="d504d-118">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-118">String</span></span>|  
|<span data-ttu-id="d504d-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d504d-119">TABLE_NAME</span></span>|<span data-ttu-id="d504d-120">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-120">String</span></span>|  
|<span data-ttu-id="d504d-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="d504d-121">TABLE_TYPE</span></span>|<span data-ttu-id="d504d-122">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-122">String</span></span>|  
|<span data-ttu-id="d504d-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="d504d-123">TABLE_GUID</span></span>|<span data-ttu-id="d504d-124">Guid</span><span class="sxs-lookup"><span data-stu-id="d504d-124">Guid</span></span>|  
|<span data-ttu-id="d504d-125">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="d504d-125">DESCRIPTION</span></span>|<span data-ttu-id="d504d-126">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-126">String</span></span>|  
|<span data-ttu-id="d504d-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="d504d-127">TABLE_PROPID</span></span>|<span data-ttu-id="d504d-128">Int64</span><span class="sxs-lookup"><span data-stu-id="d504d-128">Int64</span></span>|  
|<span data-ttu-id="d504d-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="d504d-129">DATE_CREATED</span></span>|<span data-ttu-id="d504d-130">DateTime</span><span class="sxs-lookup"><span data-stu-id="d504d-130">DateTime</span></span>|  
|<span data-ttu-id="d504d-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="d504d-131">DATE_MODIFIED</span></span>|<span data-ttu-id="d504d-132">DateTime</span><span class="sxs-lookup"><span data-stu-id="d504d-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="d504d-133">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="d504d-133">Columns</span></span>  
  
|<span data-ttu-id="d504d-134">ColumnName</span><span class="sxs-lookup"><span data-stu-id="d504d-134">ColumnName</span></span>|<span data-ttu-id="d504d-135">Veri türü</span><span class="sxs-lookup"><span data-stu-id="d504d-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d504d-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d504d-136">TABLE_CATALOG</span></span>|<span data-ttu-id="d504d-137">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-137">String</span></span>|  
|<span data-ttu-id="d504d-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d504d-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="d504d-139">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-139">String</span></span>|  
|<span data-ttu-id="d504d-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d504d-140">TABLE_NAME</span></span>|<span data-ttu-id="d504d-141">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-141">String</span></span>|  
|<span data-ttu-id="d504d-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="d504d-142">COLUMN_NAME</span></span>|<span data-ttu-id="d504d-143">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-143">String</span></span>|  
|<span data-ttu-id="d504d-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="d504d-144">COLUMN_GUID</span></span>|<span data-ttu-id="d504d-145">Guid</span><span class="sxs-lookup"><span data-stu-id="d504d-145">Guid</span></span>|  
|<span data-ttu-id="d504d-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="d504d-146">COLUMN_PROPID</span></span>|<span data-ttu-id="d504d-147">Int64</span><span class="sxs-lookup"><span data-stu-id="d504d-147">Int64</span></span>|  
|<span data-ttu-id="d504d-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="d504d-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="d504d-149">Int64</span><span class="sxs-lookup"><span data-stu-id="d504d-149">Int64</span></span>|  
|<span data-ttu-id="d504d-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="d504d-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="d504d-151">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d504d-151">Boolean</span></span>|  
|<span data-ttu-id="d504d-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="d504d-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="d504d-153">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-153">String</span></span>|  
|<span data-ttu-id="d504d-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="d504d-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="d504d-155">Int64</span><span class="sxs-lookup"><span data-stu-id="d504d-155">Int64</span></span>|  
|<span data-ttu-id="d504d-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="d504d-156">IS_NULLABLE</span></span>|<span data-ttu-id="d504d-157">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d504d-157">Boolean</span></span>|  
|<span data-ttu-id="d504d-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="d504d-158">DATA_TYPE</span></span>|<span data-ttu-id="d504d-159">Int32</span><span class="sxs-lookup"><span data-stu-id="d504d-159">Int32</span></span>|  
|<span data-ttu-id="d504d-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="d504d-160">TYPE_GUID</span></span>|<span data-ttu-id="d504d-161">Guid</span><span class="sxs-lookup"><span data-stu-id="d504d-161">Guid</span></span>|  
|<span data-ttu-id="d504d-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="d504d-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="d504d-163">Int64</span><span class="sxs-lookup"><span data-stu-id="d504d-163">Int64</span></span>|  
|<span data-ttu-id="d504d-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="d504d-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="d504d-165">Int64</span><span class="sxs-lookup"><span data-stu-id="d504d-165">Int64</span></span>|  
|<span data-ttu-id="d504d-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="d504d-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="d504d-167">Int32</span><span class="sxs-lookup"><span data-stu-id="d504d-167">Int32</span></span>|  
|<span data-ttu-id="d504d-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="d504d-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="d504d-169">Int16</span><span class="sxs-lookup"><span data-stu-id="d504d-169">Int16</span></span>|  
|<span data-ttu-id="d504d-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="d504d-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="d504d-171">Int64</span><span class="sxs-lookup"><span data-stu-id="d504d-171">Int64</span></span>|  
|<span data-ttu-id="d504d-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d504d-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="d504d-173">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-173">String</span></span>|  
|<span data-ttu-id="d504d-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d504d-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="d504d-175">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-175">String</span></span>|  
|<span data-ttu-id="d504d-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="d504d-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="d504d-177">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-177">String</span></span>|  
|<span data-ttu-id="d504d-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d504d-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="d504d-179">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-179">String</span></span>|  
|<span data-ttu-id="d504d-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d504d-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="d504d-181">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-181">String</span></span>|  
|<span data-ttu-id="d504d-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="d504d-182">COLLATION_NAME</span></span>|<span data-ttu-id="d504d-183">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-183">String</span></span>|  
|<span data-ttu-id="d504d-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d504d-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="d504d-185">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-185">String</span></span>|  
|<span data-ttu-id="d504d-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d504d-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="d504d-187">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-187">String</span></span>|  
|<span data-ttu-id="d504d-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="d504d-188">DOMAIN_NAME</span></span>|<span data-ttu-id="d504d-189">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-189">String</span></span>|  
|<span data-ttu-id="d504d-190">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="d504d-190">DESCRIPTION</span></span>|<span data-ttu-id="d504d-191">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-191">String</span></span>|  
|<span data-ttu-id="d504d-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="d504d-192">COLUMN_LCID</span></span>|<span data-ttu-id="d504d-193">Int32</span><span class="sxs-lookup"><span data-stu-id="d504d-193">Int32</span></span>|  
|<span data-ttu-id="d504d-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="d504d-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="d504d-195">Int32</span><span class="sxs-lookup"><span data-stu-id="d504d-195">Int32</span></span>|  
|<span data-ttu-id="d504d-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="d504d-196">COLUMN_SORTID</span></span>|<span data-ttu-id="d504d-197">Int32</span><span class="sxs-lookup"><span data-stu-id="d504d-197">Int32</span></span>|  
|<span data-ttu-id="d504d-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="d504d-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="d504d-199">Bayt]</span><span class="sxs-lookup"><span data-stu-id="d504d-199">Byte[]</span></span>|  
|<span data-ttu-id="d504d-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="d504d-200">IS_COMPUTED</span></span>|<span data-ttu-id="d504d-201">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d504d-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="d504d-202">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="d504d-202">Procedures</span></span>  
  
|<span data-ttu-id="d504d-203">ColumnName</span><span class="sxs-lookup"><span data-stu-id="d504d-203">ColumnName</span></span>|<span data-ttu-id="d504d-204">Veri türü</span><span class="sxs-lookup"><span data-stu-id="d504d-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d504d-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d504d-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="d504d-206">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-206">String</span></span>|  
|<span data-ttu-id="d504d-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d504d-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="d504d-208">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-208">String</span></span>|  
|<span data-ttu-id="d504d-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="d504d-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="d504d-210">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-210">String</span></span>|  
|<span data-ttu-id="d504d-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="d504d-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="d504d-212">Int16</span><span class="sxs-lookup"><span data-stu-id="d504d-212">Int16</span></span>|  
|<span data-ttu-id="d504d-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="d504d-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="d504d-214">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-214">String</span></span>|  
|<span data-ttu-id="d504d-215">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="d504d-215">DESCRIPTION</span></span>|<span data-ttu-id="d504d-216">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-216">String</span></span>|  
|<span data-ttu-id="d504d-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="d504d-217">DATE_CREATED</span></span>|<span data-ttu-id="d504d-218">DateTime</span><span class="sxs-lookup"><span data-stu-id="d504d-218">DateTime</span></span>|  
|<span data-ttu-id="d504d-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="d504d-219">DATE_MODIFIED</span></span>|<span data-ttu-id="d504d-220">DateTime</span><span class="sxs-lookup"><span data-stu-id="d504d-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="d504d-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="d504d-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="d504d-222">ColumnName</span><span class="sxs-lookup"><span data-stu-id="d504d-222">ColumnName</span></span>|<span data-ttu-id="d504d-223">Veri türü</span><span class="sxs-lookup"><span data-stu-id="d504d-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d504d-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d504d-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="d504d-225">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-225">String</span></span>|  
|<span data-ttu-id="d504d-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d504d-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="d504d-227">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-227">String</span></span>|  
|<span data-ttu-id="d504d-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="d504d-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="d504d-229">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-229">String</span></span>|  
|<span data-ttu-id="d504d-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="d504d-230">PARAMETER_NAME</span></span>|<span data-ttu-id="d504d-231">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-231">String</span></span>|  
|<span data-ttu-id="d504d-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="d504d-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="d504d-233">Int32</span><span class="sxs-lookup"><span data-stu-id="d504d-233">Int32</span></span>|  
|<span data-ttu-id="d504d-234">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="d504d-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="d504d-235">Int32</span><span class="sxs-lookup"><span data-stu-id="d504d-235">Int32</span></span>|  
|<span data-ttu-id="d504d-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="d504d-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="d504d-237">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d504d-237">Boolean</span></span>|  
|<span data-ttu-id="d504d-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="d504d-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="d504d-239">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-239">String</span></span>|  
|<span data-ttu-id="d504d-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="d504d-240">IS_NULLABLE</span></span>|<span data-ttu-id="d504d-241">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d504d-241">Boolean</span></span>|  
|<span data-ttu-id="d504d-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="d504d-242">DATA_TYPE</span></span>|<span data-ttu-id="d504d-243">Int32</span><span class="sxs-lookup"><span data-stu-id="d504d-243">Int32</span></span>|  
|<span data-ttu-id="d504d-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="d504d-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="d504d-245">Int64</span><span class="sxs-lookup"><span data-stu-id="d504d-245">Int64</span></span>|  
|<span data-ttu-id="d504d-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="d504d-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="d504d-247">Int64</span><span class="sxs-lookup"><span data-stu-id="d504d-247">Int64</span></span>|  
|<span data-ttu-id="d504d-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="d504d-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="d504d-249">Int32</span><span class="sxs-lookup"><span data-stu-id="d504d-249">Int32</span></span>|  
|<span data-ttu-id="d504d-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="d504d-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="d504d-251">Int16</span><span class="sxs-lookup"><span data-stu-id="d504d-251">Int16</span></span>|  
|<span data-ttu-id="d504d-252">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="d504d-252">DESCRIPTION</span></span>|<span data-ttu-id="d504d-253">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-253">String</span></span>|  
|<span data-ttu-id="d504d-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="d504d-254">TYPE_NAME</span></span>|<span data-ttu-id="d504d-255">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-255">String</span></span>|  
|<span data-ttu-id="d504d-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="d504d-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="d504d-257">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="d504d-258">Kataloğu</span><span class="sxs-lookup"><span data-stu-id="d504d-258">Catalog</span></span>  
  
|<span data-ttu-id="d504d-259">ColumnName</span><span class="sxs-lookup"><span data-stu-id="d504d-259">ColumnName</span></span>|<span data-ttu-id="d504d-260">Veri türü</span><span class="sxs-lookup"><span data-stu-id="d504d-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d504d-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="d504d-261">CATALOG_NAME</span></span>|<span data-ttu-id="d504d-262">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-262">String</span></span>|  
|<span data-ttu-id="d504d-263">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="d504d-263">DESCRIPTION</span></span>|<span data-ttu-id="d504d-264">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="d504d-265">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="d504d-265">Indexes</span></span>  
  
|<span data-ttu-id="d504d-266">ColumnName</span><span class="sxs-lookup"><span data-stu-id="d504d-266">ColumnName</span></span>|<span data-ttu-id="d504d-267">Veri türü</span><span class="sxs-lookup"><span data-stu-id="d504d-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d504d-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d504d-268">TABLE_CATALOG</span></span>|<span data-ttu-id="d504d-269">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-269">String</span></span>|  
|<span data-ttu-id="d504d-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d504d-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="d504d-271">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-271">String</span></span>|  
|<span data-ttu-id="d504d-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d504d-272">TABLE_NAME</span></span>|<span data-ttu-id="d504d-273">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-273">String</span></span>|  
|<span data-ttu-id="d504d-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d504d-274">INDEX_CATALOG</span></span>|<span data-ttu-id="d504d-275">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-275">String</span></span>|  
|<span data-ttu-id="d504d-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d504d-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="d504d-277">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-277">String</span></span>|  
|<span data-ttu-id="d504d-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="d504d-278">INDEX_NAME</span></span>|<span data-ttu-id="d504d-279">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-279">String</span></span>|  
|<span data-ttu-id="d504d-280">İŞLEM</span><span class="sxs-lookup"><span data-stu-id="d504d-280">PRIMARY_KEY</span></span>|<span data-ttu-id="d504d-281">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d504d-281">Boolean</span></span>|  
|<span data-ttu-id="d504d-282">BENZERSİZ</span><span class="sxs-lookup"><span data-stu-id="d504d-282">UNIQUE</span></span>|<span data-ttu-id="d504d-283">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d504d-283">Boolean</span></span>|  
|<span data-ttu-id="d504d-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="d504d-284">CLUSTERED</span></span>|<span data-ttu-id="d504d-285">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d504d-285">Boolean</span></span>|  
|<span data-ttu-id="d504d-286">TÜRÜ</span><span class="sxs-lookup"><span data-stu-id="d504d-286">TYPE</span></span>|<span data-ttu-id="d504d-287">Int32</span><span class="sxs-lookup"><span data-stu-id="d504d-287">Int32</span></span>|  
|<span data-ttu-id="d504d-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="d504d-288">FILL_FACTOR</span></span>|<span data-ttu-id="d504d-289">Int32</span><span class="sxs-lookup"><span data-stu-id="d504d-289">Int32</span></span>|  
|<span data-ttu-id="d504d-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="d504d-290">INITIAL_SIZE</span></span>|<span data-ttu-id="d504d-291">Int32</span><span class="sxs-lookup"><span data-stu-id="d504d-291">Int32</span></span>|  
|<span data-ttu-id="d504d-292">NULLS</span><span class="sxs-lookup"><span data-stu-id="d504d-292">NULLS</span></span>|<span data-ttu-id="d504d-293">Int32</span><span class="sxs-lookup"><span data-stu-id="d504d-293">Int32</span></span>|  
|<span data-ttu-id="d504d-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="d504d-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="d504d-295">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d504d-295">Boolean</span></span>|  
|<span data-ttu-id="d504d-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="d504d-296">AUTO_UPDATE</span></span>|<span data-ttu-id="d504d-297">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d504d-297">Boolean</span></span>|  
|<span data-ttu-id="d504d-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="d504d-298">NULL_COLLATION</span></span>|<span data-ttu-id="d504d-299">Int32</span><span class="sxs-lookup"><span data-stu-id="d504d-299">Int32</span></span>|  
|<span data-ttu-id="d504d-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="d504d-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="d504d-301">Int64</span><span class="sxs-lookup"><span data-stu-id="d504d-301">Int64</span></span>|  
|<span data-ttu-id="d504d-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="d504d-302">COLUMN_NAME</span></span>|<span data-ttu-id="d504d-303">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-303">String</span></span>|  
|<span data-ttu-id="d504d-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="d504d-304">COLUMN_GUID</span></span>|<span data-ttu-id="d504d-305">Guid</span><span class="sxs-lookup"><span data-stu-id="d504d-305">Guid</span></span>|  
|<span data-ttu-id="d504d-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="d504d-306">COLUMN_PROPID</span></span>|<span data-ttu-id="d504d-307">Int64</span><span class="sxs-lookup"><span data-stu-id="d504d-307">Int64</span></span>|  
|<span data-ttu-id="d504d-308">HARMANLAMA</span><span class="sxs-lookup"><span data-stu-id="d504d-308">COLLATION</span></span>|<span data-ttu-id="d504d-309">Int16</span><span class="sxs-lookup"><span data-stu-id="d504d-309">Int16</span></span>|  
|<span data-ttu-id="d504d-310">ÖNEM DÜZEYİ</span><span class="sxs-lookup"><span data-stu-id="d504d-310">CARDINALITY</span></span>|<span data-ttu-id="d504d-311">Ondalık</span><span class="sxs-lookup"><span data-stu-id="d504d-311">Decimal</span></span>|  
|<span data-ttu-id="d504d-312">SAYFALARI</span><span class="sxs-lookup"><span data-stu-id="d504d-312">PAGES</span></span>|<span data-ttu-id="d504d-313">Int32</span><span class="sxs-lookup"><span data-stu-id="d504d-313">Int32</span></span>|  
|<span data-ttu-id="d504d-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="d504d-314">FILTER_CONDITION</span></span>|<span data-ttu-id="d504d-315">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-315">String</span></span>|  
|<span data-ttu-id="d504d-316">TÜMLEŞİK</span><span class="sxs-lookup"><span data-stu-id="d504d-316">INTEGRATED</span></span>|<span data-ttu-id="d504d-317">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d504d-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="d504d-318">Microsoft Oracle OLE DB sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="d504d-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="d504d-319">Microsoft Oracle OLE DB sürücüsü aşağıdaki özel şema koleksiyonları ortak şema koleksiyonları yanı sıra destekler:</span><span class="sxs-lookup"><span data-stu-id="d504d-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="d504d-320">Tabloları</span><span class="sxs-lookup"><span data-stu-id="d504d-320">Tables</span></span>  
  
-   <span data-ttu-id="d504d-321">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="d504d-321">Columns</span></span>  
  
-   <span data-ttu-id="d504d-322">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="d504d-322">Procedures</span></span>  
  
-   <span data-ttu-id="d504d-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="d504d-323">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="d504d-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="d504d-324">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="d504d-325">Görünümler</span><span class="sxs-lookup"><span data-stu-id="d504d-325">Views</span></span>  
  
-   <span data-ttu-id="d504d-326">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="d504d-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="d504d-327">Tabloları</span><span class="sxs-lookup"><span data-stu-id="d504d-327">Tables</span></span>  
  
|<span data-ttu-id="d504d-328">ColumnName</span><span class="sxs-lookup"><span data-stu-id="d504d-328">ColumnName</span></span>|<span data-ttu-id="d504d-329">Veri türü</span><span class="sxs-lookup"><span data-stu-id="d504d-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d504d-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d504d-330">TABLE_CATALOG</span></span>|<span data-ttu-id="d504d-331">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-331">String</span></span>|  
|<span data-ttu-id="d504d-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d504d-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="d504d-333">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-333">String</span></span>|  
|<span data-ttu-id="d504d-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d504d-334">TABLE_NAME</span></span>|<span data-ttu-id="d504d-335">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-335">String</span></span>|  
|<span data-ttu-id="d504d-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="d504d-336">TABLE_TYPE</span></span>|<span data-ttu-id="d504d-337">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-337">String</span></span>|  
|<span data-ttu-id="d504d-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="d504d-338">TABLE_GUID</span></span>|<span data-ttu-id="d504d-339">Guid</span><span class="sxs-lookup"><span data-stu-id="d504d-339">Guid</span></span>|  
|<span data-ttu-id="d504d-340">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="d504d-340">DESCRIPTION</span></span>|<span data-ttu-id="d504d-341">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-341">String</span></span>|  
|<span data-ttu-id="d504d-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="d504d-342">TABLE_PROPID</span></span>|<span data-ttu-id="d504d-343">Int64</span><span class="sxs-lookup"><span data-stu-id="d504d-343">Int64</span></span>|  
|<span data-ttu-id="d504d-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="d504d-344">DATE_CREATED</span></span>|<span data-ttu-id="d504d-345">DateTime</span><span class="sxs-lookup"><span data-stu-id="d504d-345">DateTime</span></span>|  
|<span data-ttu-id="d504d-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="d504d-346">DATE_MODIFIED</span></span>|<span data-ttu-id="d504d-347">DateTime</span><span class="sxs-lookup"><span data-stu-id="d504d-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="d504d-348">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="d504d-348">Columns</span></span>  
  
|<span data-ttu-id="d504d-349">ColumnName</span><span class="sxs-lookup"><span data-stu-id="d504d-349">ColumnName</span></span>|<span data-ttu-id="d504d-350">Veri türü</span><span class="sxs-lookup"><span data-stu-id="d504d-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d504d-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d504d-351">TABLE_CATALOG</span></span>|<span data-ttu-id="d504d-352">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-352">String</span></span>|  
|<span data-ttu-id="d504d-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d504d-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="d504d-354">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-354">String</span></span>|  
|<span data-ttu-id="d504d-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d504d-355">TABLE_NAME</span></span>|<span data-ttu-id="d504d-356">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-356">String</span></span>|  
|<span data-ttu-id="d504d-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="d504d-357">COLUMN_NAME</span></span>|<span data-ttu-id="d504d-358">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-358">String</span></span>|  
|<span data-ttu-id="d504d-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="d504d-359">COLUMN_GUID</span></span>|<span data-ttu-id="d504d-360">Guid</span><span class="sxs-lookup"><span data-stu-id="d504d-360">Guid</span></span>|  
|<span data-ttu-id="d504d-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="d504d-361">COLUMN_PROPID</span></span>|<span data-ttu-id="d504d-362">Int64</span><span class="sxs-lookup"><span data-stu-id="d504d-362">Int64</span></span>|  
|<span data-ttu-id="d504d-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="d504d-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="d504d-364">Int64</span><span class="sxs-lookup"><span data-stu-id="d504d-364">Int64</span></span>|  
|<span data-ttu-id="d504d-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="d504d-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="d504d-366">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d504d-366">Boolean</span></span>|  
|<span data-ttu-id="d504d-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="d504d-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="d504d-368">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-368">String</span></span>|  
|<span data-ttu-id="d504d-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="d504d-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="d504d-370">Int64</span><span class="sxs-lookup"><span data-stu-id="d504d-370">Int64</span></span>|  
|<span data-ttu-id="d504d-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="d504d-371">IS_NULLABLE</span></span>|<span data-ttu-id="d504d-372">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d504d-372">Boolean</span></span>|  
|<span data-ttu-id="d504d-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="d504d-373">DATA_TYPE</span></span>|<span data-ttu-id="d504d-374">Int32</span><span class="sxs-lookup"><span data-stu-id="d504d-374">Int32</span></span>|  
|<span data-ttu-id="d504d-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="d504d-375">TYPE_GUID</span></span>|<span data-ttu-id="d504d-376">Guid</span><span class="sxs-lookup"><span data-stu-id="d504d-376">Guid</span></span>|  
|<span data-ttu-id="d504d-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="d504d-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="d504d-378">Int64</span><span class="sxs-lookup"><span data-stu-id="d504d-378">Int64</span></span>|  
|<span data-ttu-id="d504d-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="d504d-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="d504d-380">Int64</span><span class="sxs-lookup"><span data-stu-id="d504d-380">Int64</span></span>|  
|<span data-ttu-id="d504d-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="d504d-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="d504d-382">Int32</span><span class="sxs-lookup"><span data-stu-id="d504d-382">Int32</span></span>|  
|<span data-ttu-id="d504d-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="d504d-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="d504d-384">Int16</span><span class="sxs-lookup"><span data-stu-id="d504d-384">Int16</span></span>|  
|<span data-ttu-id="d504d-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="d504d-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="d504d-386">Int64</span><span class="sxs-lookup"><span data-stu-id="d504d-386">Int64</span></span>|  
|<span data-ttu-id="d504d-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d504d-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="d504d-388">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-388">String</span></span>|  
|<span data-ttu-id="d504d-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d504d-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="d504d-390">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-390">String</span></span>|  
|<span data-ttu-id="d504d-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="d504d-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="d504d-392">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-392">String</span></span>|  
|<span data-ttu-id="d504d-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d504d-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="d504d-394">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-394">String</span></span>|  
|<span data-ttu-id="d504d-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d504d-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="d504d-396">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-396">String</span></span>|  
|<span data-ttu-id="d504d-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="d504d-397">COLLATION_NAME</span></span>|<span data-ttu-id="d504d-398">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-398">String</span></span>|  
|<span data-ttu-id="d504d-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d504d-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="d504d-400">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-400">String</span></span>|  
|<span data-ttu-id="d504d-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d504d-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="d504d-402">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-402">String</span></span>|  
|<span data-ttu-id="d504d-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="d504d-403">DOMAIN_NAME</span></span>|<span data-ttu-id="d504d-404">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-404">String</span></span>|  
|<span data-ttu-id="d504d-405">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="d504d-405">DESCRIPTION</span></span>|<span data-ttu-id="d504d-406">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="d504d-407">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="d504d-407">Procedures</span></span>  
  
|<span data-ttu-id="d504d-408">ColumnName</span><span class="sxs-lookup"><span data-stu-id="d504d-408">ColumnName</span></span>|<span data-ttu-id="d504d-409">Veri türü</span><span class="sxs-lookup"><span data-stu-id="d504d-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d504d-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d504d-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="d504d-411">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-411">String</span></span>|  
|<span data-ttu-id="d504d-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d504d-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="d504d-413">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-413">String</span></span>|  
|<span data-ttu-id="d504d-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="d504d-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="d504d-415">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-415">String</span></span>|  
|<span data-ttu-id="d504d-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="d504d-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="d504d-417">Int16</span><span class="sxs-lookup"><span data-stu-id="d504d-417">Int16</span></span>|  
|<span data-ttu-id="d504d-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="d504d-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="d504d-419">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-419">String</span></span>|  
|<span data-ttu-id="d504d-420">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="d504d-420">DESCRIPTION</span></span>|<span data-ttu-id="d504d-421">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-421">String</span></span>|  
|<span data-ttu-id="d504d-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="d504d-422">DATE_CREATED</span></span>|<span data-ttu-id="d504d-423">DateTime</span><span class="sxs-lookup"><span data-stu-id="d504d-423">DateTime</span></span>|  
|<span data-ttu-id="d504d-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="d504d-424">DATE_MODIFIED</span></span>|<span data-ttu-id="d504d-425">DateTime</span><span class="sxs-lookup"><span data-stu-id="d504d-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="d504d-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="d504d-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="d504d-427">ColumnName</span><span class="sxs-lookup"><span data-stu-id="d504d-427">ColumnName</span></span>|<span data-ttu-id="d504d-428">Veri türü</span><span class="sxs-lookup"><span data-stu-id="d504d-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d504d-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d504d-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="d504d-430">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-430">String</span></span>|  
|<span data-ttu-id="d504d-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d504d-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="d504d-432">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-432">String</span></span>|  
|<span data-ttu-id="d504d-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="d504d-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="d504d-434">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-434">String</span></span>|  
|<span data-ttu-id="d504d-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="d504d-435">COLUMN_NAME</span></span>|<span data-ttu-id="d504d-436">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-436">String</span></span>|  
|<span data-ttu-id="d504d-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="d504d-437">COLUMN_GUID</span></span>|<span data-ttu-id="d504d-438">Guid</span><span class="sxs-lookup"><span data-stu-id="d504d-438">Guid</span></span>|  
|<span data-ttu-id="d504d-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="d504d-439">COLUMN_PROPID</span></span>|<span data-ttu-id="d504d-440">Int64</span><span class="sxs-lookup"><span data-stu-id="d504d-440">Int64</span></span>|  
|<span data-ttu-id="d504d-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="d504d-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="d504d-442">Int64</span><span class="sxs-lookup"><span data-stu-id="d504d-442">Int64</span></span>|  
|<span data-ttu-id="d504d-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="d504d-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="d504d-444">Int64</span><span class="sxs-lookup"><span data-stu-id="d504d-444">Int64</span></span>|  
|<span data-ttu-id="d504d-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="d504d-445">IS_NULLABLE</span></span>|<span data-ttu-id="d504d-446">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d504d-446">Boolean</span></span>|  
|<span data-ttu-id="d504d-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="d504d-447">DATA_TYPE</span></span>|<span data-ttu-id="d504d-448">Int32</span><span class="sxs-lookup"><span data-stu-id="d504d-448">Int32</span></span>|  
|<span data-ttu-id="d504d-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="d504d-449">TYPE_GUID</span></span>|<span data-ttu-id="d504d-450">Guid</span><span class="sxs-lookup"><span data-stu-id="d504d-450">Guid</span></span>|  
|<span data-ttu-id="d504d-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="d504d-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="d504d-452">Int64</span><span class="sxs-lookup"><span data-stu-id="d504d-452">Int64</span></span>|  
|<span data-ttu-id="d504d-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="d504d-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="d504d-454">Int64</span><span class="sxs-lookup"><span data-stu-id="d504d-454">Int64</span></span>|  
|<span data-ttu-id="d504d-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="d504d-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="d504d-456">Int32</span><span class="sxs-lookup"><span data-stu-id="d504d-456">Int32</span></span>|  
|<span data-ttu-id="d504d-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="d504d-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="d504d-458">Int16</span><span class="sxs-lookup"><span data-stu-id="d504d-458">Int16</span></span>|  
|<span data-ttu-id="d504d-459">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="d504d-459">DESCRIPTION</span></span>|<span data-ttu-id="d504d-460">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-460">String</span></span>|  
|<span data-ttu-id="d504d-461">AŞIRI YÜKLEME</span><span class="sxs-lookup"><span data-stu-id="d504d-461">OVERLOAD</span></span>|<span data-ttu-id="d504d-462">Int16</span><span class="sxs-lookup"><span data-stu-id="d504d-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="d504d-463">Görünümler</span><span class="sxs-lookup"><span data-stu-id="d504d-463">Views</span></span>  
  
|<span data-ttu-id="d504d-464">ColumnName</span><span class="sxs-lookup"><span data-stu-id="d504d-464">ColumnName</span></span>|<span data-ttu-id="d504d-465">Veri türü</span><span class="sxs-lookup"><span data-stu-id="d504d-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d504d-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d504d-466">TABLE_CATALOG</span></span>|<span data-ttu-id="d504d-467">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-467">String</span></span>|  
|<span data-ttu-id="d504d-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d504d-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="d504d-469">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-469">String</span></span>|  
|<span data-ttu-id="d504d-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d504d-470">TABLE_NAME</span></span>|<span data-ttu-id="d504d-471">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-471">String</span></span>|  
|<span data-ttu-id="d504d-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="d504d-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="d504d-473">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-473">String</span></span>|  
|<span data-ttu-id="d504d-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="d504d-474">CHECK_OPTION</span></span>|<span data-ttu-id="d504d-475">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d504d-475">Boolean</span></span>|  
|<span data-ttu-id="d504d-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="d504d-476">IS_UPDATABLE</span></span>|<span data-ttu-id="d504d-477">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d504d-477">Boolean</span></span>|  
|<span data-ttu-id="d504d-478">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="d504d-478">DESCRIPTION</span></span>|<span data-ttu-id="d504d-479">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-479">String</span></span>|  
|<span data-ttu-id="d504d-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="d504d-480">DATE_CREATED</span></span>|<span data-ttu-id="d504d-481">DateTime</span><span class="sxs-lookup"><span data-stu-id="d504d-481">DateTime</span></span>|  
|<span data-ttu-id="d504d-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="d504d-482">DATE_MODIFIED</span></span>|<span data-ttu-id="d504d-483">DateTime</span><span class="sxs-lookup"><span data-stu-id="d504d-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="d504d-484">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="d504d-484">Indexes</span></span>  
  
|<span data-ttu-id="d504d-485">ColumnName</span><span class="sxs-lookup"><span data-stu-id="d504d-485">ColumnName</span></span>|<span data-ttu-id="d504d-486">Veri türü</span><span class="sxs-lookup"><span data-stu-id="d504d-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d504d-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d504d-487">TABLE_CATALOG</span></span>|<span data-ttu-id="d504d-488">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-488">String</span></span>|  
|<span data-ttu-id="d504d-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d504d-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="d504d-490">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-490">String</span></span>|  
|<span data-ttu-id="d504d-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d504d-491">TABLE_NAME</span></span>|<span data-ttu-id="d504d-492">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-492">String</span></span>|  
|<span data-ttu-id="d504d-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d504d-493">INDEX_CATALOG</span></span>|<span data-ttu-id="d504d-494">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-494">String</span></span>|  
|<span data-ttu-id="d504d-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d504d-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="d504d-496">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-496">String</span></span>|  
|<span data-ttu-id="d504d-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="d504d-497">INDEX_NAME</span></span>|<span data-ttu-id="d504d-498">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-498">String</span></span>|  
|<span data-ttu-id="d504d-499">İŞLEM</span><span class="sxs-lookup"><span data-stu-id="d504d-499">PRIMARY_KEY</span></span>|<span data-ttu-id="d504d-500">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d504d-500">Boolean</span></span>|  
|<span data-ttu-id="d504d-501">BENZERSİZ</span><span class="sxs-lookup"><span data-stu-id="d504d-501">UNIQUE</span></span>|<span data-ttu-id="d504d-502">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d504d-502">Boolean</span></span>|  
|<span data-ttu-id="d504d-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="d504d-503">CLUSTERED</span></span>|<span data-ttu-id="d504d-504">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d504d-504">Boolean</span></span>|  
|<span data-ttu-id="d504d-505">TÜRÜ</span><span class="sxs-lookup"><span data-stu-id="d504d-505">TYPE</span></span>|<span data-ttu-id="d504d-506">Int32</span><span class="sxs-lookup"><span data-stu-id="d504d-506">Int32</span></span>|  
|<span data-ttu-id="d504d-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="d504d-507">FILL_FACTOR</span></span>|<span data-ttu-id="d504d-508">Int32</span><span class="sxs-lookup"><span data-stu-id="d504d-508">Int32</span></span>|  
|<span data-ttu-id="d504d-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="d504d-509">INITIAL_SIZE</span></span>|<span data-ttu-id="d504d-510">Int32</span><span class="sxs-lookup"><span data-stu-id="d504d-510">Int32</span></span>|  
|<span data-ttu-id="d504d-511">NULLS</span><span class="sxs-lookup"><span data-stu-id="d504d-511">NULLS</span></span>|<span data-ttu-id="d504d-512">Int32</span><span class="sxs-lookup"><span data-stu-id="d504d-512">Int32</span></span>|  
|<span data-ttu-id="d504d-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="d504d-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="d504d-514">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d504d-514">Boolean</span></span>|  
|<span data-ttu-id="d504d-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="d504d-515">AUTO_UPDATE</span></span>|<span data-ttu-id="d504d-516">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d504d-516">Boolean</span></span>|  
|<span data-ttu-id="d504d-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="d504d-517">NULL_COLLATION</span></span>|<span data-ttu-id="d504d-518">Int32</span><span class="sxs-lookup"><span data-stu-id="d504d-518">Int32</span></span>|  
|<span data-ttu-id="d504d-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="d504d-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="d504d-520">Int64</span><span class="sxs-lookup"><span data-stu-id="d504d-520">Int64</span></span>|  
|<span data-ttu-id="d504d-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="d504d-521">COLUMN_NAME</span></span>|<span data-ttu-id="d504d-522">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-522">String</span></span>|  
|<span data-ttu-id="d504d-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="d504d-523">COLUMN_GUID</span></span>|<span data-ttu-id="d504d-524">Guid</span><span class="sxs-lookup"><span data-stu-id="d504d-524">Guid</span></span>|  
|<span data-ttu-id="d504d-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="d504d-525">COLUMN_PROPID</span></span>|<span data-ttu-id="d504d-526">Int64</span><span class="sxs-lookup"><span data-stu-id="d504d-526">Int64</span></span>|  
|<span data-ttu-id="d504d-527">HARMANLAMA</span><span class="sxs-lookup"><span data-stu-id="d504d-527">COLLATION</span></span>|<span data-ttu-id="d504d-528">Int16</span><span class="sxs-lookup"><span data-stu-id="d504d-528">Int16</span></span>|  
|<span data-ttu-id="d504d-529">ÖNEM DÜZEYİ</span><span class="sxs-lookup"><span data-stu-id="d504d-529">CARDINALITY</span></span>|<span data-ttu-id="d504d-530">Ondalık</span><span class="sxs-lookup"><span data-stu-id="d504d-530">Decimal</span></span>|  
|<span data-ttu-id="d504d-531">SAYFALARI</span><span class="sxs-lookup"><span data-stu-id="d504d-531">PAGES</span></span>|<span data-ttu-id="d504d-532">Int32</span><span class="sxs-lookup"><span data-stu-id="d504d-532">Int32</span></span>|  
|<span data-ttu-id="d504d-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="d504d-533">FILTER_CONDITION</span></span>|<span data-ttu-id="d504d-534">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-534">String</span></span>|  
|<span data-ttu-id="d504d-535">TÜMLEŞİK</span><span class="sxs-lookup"><span data-stu-id="d504d-535">INTEGRATED</span></span>|<span data-ttu-id="d504d-536">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d504d-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="d504d-537">Microsoft Jet OLE DB sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="d504d-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="d504d-538">Microsoft Jet OLE DB sürücüsü aşağıdaki özel şema koleksiyonları ortak şema koleksiyonları yanı sıra destekler:</span><span class="sxs-lookup"><span data-stu-id="d504d-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="d504d-539">Tabloları</span><span class="sxs-lookup"><span data-stu-id="d504d-539">Tables</span></span>  
  
-   <span data-ttu-id="d504d-540">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="d504d-540">Columns</span></span>  
  
-   <span data-ttu-id="d504d-541">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="d504d-541">Procedures</span></span>  
  
-   <span data-ttu-id="d504d-542">Görünümler</span><span class="sxs-lookup"><span data-stu-id="d504d-542">Views</span></span>  
  
-   <span data-ttu-id="d504d-543">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="d504d-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="d504d-544">Tabloları</span><span class="sxs-lookup"><span data-stu-id="d504d-544">Tables</span></span>  
  
|<span data-ttu-id="d504d-545">ColumnName</span><span class="sxs-lookup"><span data-stu-id="d504d-545">ColumnName</span></span>|<span data-ttu-id="d504d-546">Veri türü</span><span class="sxs-lookup"><span data-stu-id="d504d-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d504d-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d504d-547">TABLE_CATALOG</span></span>|<span data-ttu-id="d504d-548">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-548">String</span></span>|  
|<span data-ttu-id="d504d-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d504d-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="d504d-550">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-550">String</span></span>|  
|<span data-ttu-id="d504d-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d504d-551">TABLE_NAME</span></span>|<span data-ttu-id="d504d-552">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-552">String</span></span>|  
|<span data-ttu-id="d504d-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="d504d-553">TABLE_TYPE</span></span>|<span data-ttu-id="d504d-554">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-554">String</span></span>|  
|<span data-ttu-id="d504d-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="d504d-555">TABLE_GUID</span></span>|<span data-ttu-id="d504d-556">Guid</span><span class="sxs-lookup"><span data-stu-id="d504d-556">Guid</span></span>|  
|<span data-ttu-id="d504d-557">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="d504d-557">DESCRIPTION</span></span>|<span data-ttu-id="d504d-558">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-558">String</span></span>|  
|<span data-ttu-id="d504d-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="d504d-559">TABLE_PROPID</span></span>|<span data-ttu-id="d504d-560">Int64</span><span class="sxs-lookup"><span data-stu-id="d504d-560">Int64</span></span>|  
|<span data-ttu-id="d504d-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="d504d-561">DATE_CREATED</span></span>|<span data-ttu-id="d504d-562">DateTime</span><span class="sxs-lookup"><span data-stu-id="d504d-562">DateTime</span></span>|  
|<span data-ttu-id="d504d-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="d504d-563">DATE_MODIFIED</span></span>|<span data-ttu-id="d504d-564">DateTime</span><span class="sxs-lookup"><span data-stu-id="d504d-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="d504d-565">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="d504d-565">Columns</span></span>  
  
|<span data-ttu-id="d504d-566">ColumnName</span><span class="sxs-lookup"><span data-stu-id="d504d-566">ColumnName</span></span>|<span data-ttu-id="d504d-567">Veri türü</span><span class="sxs-lookup"><span data-stu-id="d504d-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d504d-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d504d-568">TABLE_CATALOG</span></span>|<span data-ttu-id="d504d-569">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-569">String</span></span>|  
|<span data-ttu-id="d504d-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d504d-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="d504d-571">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-571">String</span></span>|  
|<span data-ttu-id="d504d-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d504d-572">TABLE_NAME</span></span>|<span data-ttu-id="d504d-573">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-573">String</span></span>|  
|<span data-ttu-id="d504d-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="d504d-574">COLUMN_NAME</span></span>|<span data-ttu-id="d504d-575">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-575">String</span></span>|  
|<span data-ttu-id="d504d-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="d504d-576">COLUMN_GUID</span></span>|<span data-ttu-id="d504d-577">Guid</span><span class="sxs-lookup"><span data-stu-id="d504d-577">Guid</span></span>|  
|<span data-ttu-id="d504d-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="d504d-578">COLUMN_PROPID</span></span>|<span data-ttu-id="d504d-579">Int64</span><span class="sxs-lookup"><span data-stu-id="d504d-579">Int64</span></span>|  
|<span data-ttu-id="d504d-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="d504d-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="d504d-581">Int64</span><span class="sxs-lookup"><span data-stu-id="d504d-581">Int64</span></span>|  
|<span data-ttu-id="d504d-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="d504d-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="d504d-583">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d504d-583">Boolean</span></span>|  
|<span data-ttu-id="d504d-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="d504d-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="d504d-585">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-585">String</span></span>|  
|<span data-ttu-id="d504d-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="d504d-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="d504d-587">Int64</span><span class="sxs-lookup"><span data-stu-id="d504d-587">Int64</span></span>|  
|<span data-ttu-id="d504d-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="d504d-588">IS_NULLABLE</span></span>|<span data-ttu-id="d504d-589">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d504d-589">Boolean</span></span>|  
|<span data-ttu-id="d504d-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="d504d-590">DATA_TYPE</span></span>|<span data-ttu-id="d504d-591">Int32</span><span class="sxs-lookup"><span data-stu-id="d504d-591">Int32</span></span>|  
|<span data-ttu-id="d504d-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="d504d-592">TYPE_GUID</span></span>|<span data-ttu-id="d504d-593">Guid</span><span class="sxs-lookup"><span data-stu-id="d504d-593">Guid</span></span>|  
|<span data-ttu-id="d504d-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="d504d-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="d504d-595">Int64</span><span class="sxs-lookup"><span data-stu-id="d504d-595">Int64</span></span>|  
|<span data-ttu-id="d504d-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="d504d-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="d504d-597">Int64</span><span class="sxs-lookup"><span data-stu-id="d504d-597">Int64</span></span>|  
|<span data-ttu-id="d504d-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="d504d-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="d504d-599">Int32</span><span class="sxs-lookup"><span data-stu-id="d504d-599">Int32</span></span>|  
|<span data-ttu-id="d504d-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="d504d-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="d504d-601">Int16</span><span class="sxs-lookup"><span data-stu-id="d504d-601">Int16</span></span>|  
|<span data-ttu-id="d504d-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="d504d-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="d504d-603">Int64</span><span class="sxs-lookup"><span data-stu-id="d504d-603">Int64</span></span>|  
|<span data-ttu-id="d504d-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d504d-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="d504d-605">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-605">String</span></span>|  
|<span data-ttu-id="d504d-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d504d-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="d504d-607">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-607">String</span></span>|  
|<span data-ttu-id="d504d-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="d504d-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="d504d-609">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-609">String</span></span>|  
|<span data-ttu-id="d504d-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d504d-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="d504d-611">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-611">String</span></span>|  
|<span data-ttu-id="d504d-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d504d-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="d504d-613">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-613">String</span></span>|  
|<span data-ttu-id="d504d-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="d504d-614">COLLATION_NAME</span></span>|<span data-ttu-id="d504d-615">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-615">String</span></span>|  
|<span data-ttu-id="d504d-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d504d-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="d504d-617">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-617">String</span></span>|  
|<span data-ttu-id="d504d-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d504d-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="d504d-619">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-619">String</span></span>|  
|<span data-ttu-id="d504d-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="d504d-620">DOMAIN_NAME</span></span>|<span data-ttu-id="d504d-621">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-621">String</span></span>|  
|<span data-ttu-id="d504d-622">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="d504d-622">DESCRIPTION</span></span>|<span data-ttu-id="d504d-623">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="d504d-624">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="d504d-624">Procedures</span></span>  
  
|<span data-ttu-id="d504d-625">ColumnName</span><span class="sxs-lookup"><span data-stu-id="d504d-625">ColumnName</span></span>|<span data-ttu-id="d504d-626">Veri türü</span><span class="sxs-lookup"><span data-stu-id="d504d-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d504d-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d504d-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="d504d-628">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-628">String</span></span>|  
|<span data-ttu-id="d504d-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d504d-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="d504d-630">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-630">String</span></span>|  
|<span data-ttu-id="d504d-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="d504d-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="d504d-632">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-632">String</span></span>|  
|<span data-ttu-id="d504d-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="d504d-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="d504d-634">Int16</span><span class="sxs-lookup"><span data-stu-id="d504d-634">Int16</span></span>|  
|<span data-ttu-id="d504d-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="d504d-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="d504d-636">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-636">String</span></span>|  
|<span data-ttu-id="d504d-637">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="d504d-637">DESCRIPTION</span></span>|<span data-ttu-id="d504d-638">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-638">String</span></span>|  
|<span data-ttu-id="d504d-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="d504d-639">DATE_CREATED</span></span>|<span data-ttu-id="d504d-640">DateTime</span><span class="sxs-lookup"><span data-stu-id="d504d-640">DateTime</span></span>|  
|<span data-ttu-id="d504d-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="d504d-641">DATE_MODIFIED</span></span>|<span data-ttu-id="d504d-642">DateTime</span><span class="sxs-lookup"><span data-stu-id="d504d-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="d504d-643">Görünümler</span><span class="sxs-lookup"><span data-stu-id="d504d-643">Views</span></span>  
  
|<span data-ttu-id="d504d-644">ColumnName</span><span class="sxs-lookup"><span data-stu-id="d504d-644">ColumnName</span></span>|<span data-ttu-id="d504d-645">Veri türü</span><span class="sxs-lookup"><span data-stu-id="d504d-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d504d-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d504d-646">TABLE_CATALOG</span></span>|<span data-ttu-id="d504d-647">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-647">String</span></span>|  
|<span data-ttu-id="d504d-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d504d-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="d504d-649">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-649">String</span></span>|  
|<span data-ttu-id="d504d-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d504d-650">TABLE_NAME</span></span>|<span data-ttu-id="d504d-651">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-651">String</span></span>|  
|<span data-ttu-id="d504d-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="d504d-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="d504d-653">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-653">String</span></span>|  
|<span data-ttu-id="d504d-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="d504d-654">CHECK_OPTION</span></span>|<span data-ttu-id="d504d-655">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d504d-655">Boolean</span></span>|  
|<span data-ttu-id="d504d-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="d504d-656">IS_UPDATABLE</span></span>|<span data-ttu-id="d504d-657">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d504d-657">Boolean</span></span>|  
|<span data-ttu-id="d504d-658">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="d504d-658">DESCRIPTION</span></span>|<span data-ttu-id="d504d-659">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-659">String</span></span>|  
|<span data-ttu-id="d504d-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="d504d-660">DATE_CREATED</span></span>|<span data-ttu-id="d504d-661">DateTime</span><span class="sxs-lookup"><span data-stu-id="d504d-661">DateTime</span></span>|  
|<span data-ttu-id="d504d-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="d504d-662">DATE_MODIFIED</span></span>|<span data-ttu-id="d504d-663">DateTime</span><span class="sxs-lookup"><span data-stu-id="d504d-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="d504d-664">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="d504d-664">Indexes</span></span>  
  
|<span data-ttu-id="d504d-665">ColumnName</span><span class="sxs-lookup"><span data-stu-id="d504d-665">ColumnName</span></span>|<span data-ttu-id="d504d-666">Veri türü</span><span class="sxs-lookup"><span data-stu-id="d504d-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d504d-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d504d-667">TABLE_CATALOG</span></span>|<span data-ttu-id="d504d-668">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-668">String</span></span>|  
|<span data-ttu-id="d504d-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d504d-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="d504d-670">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-670">String</span></span>|  
|<span data-ttu-id="d504d-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d504d-671">TABLE_NAME</span></span>|<span data-ttu-id="d504d-672">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-672">String</span></span>|  
|<span data-ttu-id="d504d-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d504d-673">INDEX_CATALOG</span></span>|<span data-ttu-id="d504d-674">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-674">String</span></span>|  
|<span data-ttu-id="d504d-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d504d-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="d504d-676">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-676">String</span></span>|  
|<span data-ttu-id="d504d-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="d504d-677">INDEX_NAME</span></span>|<span data-ttu-id="d504d-678">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-678">String</span></span>|  
|<span data-ttu-id="d504d-679">İŞLEM</span><span class="sxs-lookup"><span data-stu-id="d504d-679">PRIMARY_KEY</span></span>|<span data-ttu-id="d504d-680">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d504d-680">Boolean</span></span>|  
|<span data-ttu-id="d504d-681">BENZERSİZ</span><span class="sxs-lookup"><span data-stu-id="d504d-681">UNIQUE</span></span>|<span data-ttu-id="d504d-682">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d504d-682">Boolean</span></span>|  
|<span data-ttu-id="d504d-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="d504d-683">CLUSTERED</span></span>|<span data-ttu-id="d504d-684">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d504d-684">Boolean</span></span>|  
|<span data-ttu-id="d504d-685">TÜRÜ</span><span class="sxs-lookup"><span data-stu-id="d504d-685">TYPE</span></span>|<span data-ttu-id="d504d-686">Int32</span><span class="sxs-lookup"><span data-stu-id="d504d-686">Int32</span></span>|  
|<span data-ttu-id="d504d-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="d504d-687">FILL_FACTOR</span></span>|<span data-ttu-id="d504d-688">Int32</span><span class="sxs-lookup"><span data-stu-id="d504d-688">Int32</span></span>|  
|<span data-ttu-id="d504d-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="d504d-689">INITIAL_SIZE</span></span>|<span data-ttu-id="d504d-690">Int32</span><span class="sxs-lookup"><span data-stu-id="d504d-690">Int32</span></span>|  
|<span data-ttu-id="d504d-691">NULLS</span><span class="sxs-lookup"><span data-stu-id="d504d-691">NULLS</span></span>|<span data-ttu-id="d504d-692">Int32</span><span class="sxs-lookup"><span data-stu-id="d504d-692">Int32</span></span>|  
|<span data-ttu-id="d504d-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="d504d-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="d504d-694">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d504d-694">Boolean</span></span>|  
|<span data-ttu-id="d504d-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="d504d-695">AUTO_UPDATE</span></span>|<span data-ttu-id="d504d-696">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d504d-696">Boolean</span></span>|  
|<span data-ttu-id="d504d-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="d504d-697">NULL_COLLATION</span></span>|<span data-ttu-id="d504d-698">Int32</span><span class="sxs-lookup"><span data-stu-id="d504d-698">Int32</span></span>|  
|<span data-ttu-id="d504d-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="d504d-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="d504d-700">Int64</span><span class="sxs-lookup"><span data-stu-id="d504d-700">Int64</span></span>|  
|<span data-ttu-id="d504d-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="d504d-701">COLUMN_NAME</span></span>|<span data-ttu-id="d504d-702">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-702">String</span></span>|  
|<span data-ttu-id="d504d-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="d504d-703">COLUMN_GUID</span></span>|<span data-ttu-id="d504d-704">Guid</span><span class="sxs-lookup"><span data-stu-id="d504d-704">Guid</span></span>|  
|<span data-ttu-id="d504d-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="d504d-705">COLUMN_PROPID</span></span>|<span data-ttu-id="d504d-706">Int64</span><span class="sxs-lookup"><span data-stu-id="d504d-706">Int64</span></span>|  
|<span data-ttu-id="d504d-707">HARMANLAMA</span><span class="sxs-lookup"><span data-stu-id="d504d-707">COLLATION</span></span>|<span data-ttu-id="d504d-708">Int16</span><span class="sxs-lookup"><span data-stu-id="d504d-708">Int16</span></span>|  
|<span data-ttu-id="d504d-709">ÖNEM DÜZEYİ</span><span class="sxs-lookup"><span data-stu-id="d504d-709">CARDINALITY</span></span>|<span data-ttu-id="d504d-710">Ondalık</span><span class="sxs-lookup"><span data-stu-id="d504d-710">Decimal</span></span>|  
|<span data-ttu-id="d504d-711">SAYFALARI</span><span class="sxs-lookup"><span data-stu-id="d504d-711">PAGES</span></span>|<span data-ttu-id="d504d-712">Int32</span><span class="sxs-lookup"><span data-stu-id="d504d-712">Int32</span></span>|  
|<span data-ttu-id="d504d-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="d504d-713">FILTER_CONDITION</span></span>|<span data-ttu-id="d504d-714">Dize</span><span class="sxs-lookup"><span data-stu-id="d504d-714">String</span></span>|  
|<span data-ttu-id="d504d-715">TÜMLEŞİK</span><span class="sxs-lookup"><span data-stu-id="d504d-715">INTEGRATED</span></span>|<span data-ttu-id="d504d-716">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d504d-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d504d-717">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d504d-717">See Also</span></span>  
 [<span data-ttu-id="d504d-718">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="d504d-718">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
