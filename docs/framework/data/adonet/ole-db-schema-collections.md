---
title: OLE DB Şema Koleksiyonları
ms.date: 03/30/2017
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
ms.openlocfilehash: 6c3441e86d4c5267418cf8002ba17d539c464d5c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645893"
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="5ecb6-102">OLE DB Şema Koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="5ecb6-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="5ecb6-103">Bu bölümde, Microsoft SQL Server, Oracle ve Microsoft Jet OLE DB sağlayıcıları için şema koleksiyonu desteğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="5ecb6-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="5ecb6-104">Microsoft SQL Server'ı OLE DB sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="5ecb6-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="5ecb6-105">Microsoft SQL Server OLE DB sürücüsü aşağıdaki özel şema koleksiyonları ortak şema koleksiyonları yanı sıra destekler:</span><span class="sxs-lookup"><span data-stu-id="5ecb6-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="5ecb6-106">Tabloları</span><span class="sxs-lookup"><span data-stu-id="5ecb6-106">Tables</span></span>  
  
- <span data-ttu-id="5ecb6-107">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="5ecb6-107">Columns</span></span>  
  
- <span data-ttu-id="5ecb6-108">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="5ecb6-108">Procedures</span></span>  
  
- <span data-ttu-id="5ecb6-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="5ecb6-109">ProcedureParameters</span></span>  
  
- <span data-ttu-id="5ecb6-110">Katalog</span><span class="sxs-lookup"><span data-stu-id="5ecb6-110">Catalog</span></span>  
  
- <span data-ttu-id="5ecb6-111">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="5ecb6-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="5ecb6-112">Tabloları</span><span class="sxs-lookup"><span data-stu-id="5ecb6-112">Tables</span></span>  
  
|<span data-ttu-id="5ecb6-113">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5ecb6-113">ColumnName</span></span>|<span data-ttu-id="5ecb6-114">DataType</span><span class="sxs-lookup"><span data-stu-id="5ecb6-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5ecb6-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5ecb6-115">TABLE_CATALOG</span></span>|<span data-ttu-id="5ecb6-116">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-116">String</span></span>|  
|<span data-ttu-id="5ecb6-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5ecb6-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="5ecb6-118">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-118">String</span></span>|  
|<span data-ttu-id="5ecb6-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5ecb6-119">TABLE_NAME</span></span>|<span data-ttu-id="5ecb6-120">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-120">String</span></span>|  
|<span data-ttu-id="5ecb6-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="5ecb6-121">TABLE_TYPE</span></span>|<span data-ttu-id="5ecb6-122">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-122">String</span></span>|  
|<span data-ttu-id="5ecb6-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="5ecb6-123">TABLE_GUID</span></span>|<span data-ttu-id="5ecb6-124">Guid</span><span class="sxs-lookup"><span data-stu-id="5ecb6-124">Guid</span></span>|  
|<span data-ttu-id="5ecb6-125">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="5ecb6-125">DESCRIPTION</span></span>|<span data-ttu-id="5ecb6-126">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-126">String</span></span>|  
|<span data-ttu-id="5ecb6-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="5ecb6-127">TABLE_PROPID</span></span>|<span data-ttu-id="5ecb6-128">Int64</span><span class="sxs-lookup"><span data-stu-id="5ecb6-128">Int64</span></span>|  
|<span data-ttu-id="5ecb6-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="5ecb6-129">DATE_CREATED</span></span>|<span data-ttu-id="5ecb6-130">DateTime</span><span class="sxs-lookup"><span data-stu-id="5ecb6-130">DateTime</span></span>|  
|<span data-ttu-id="5ecb6-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="5ecb6-131">DATE_MODIFIED</span></span>|<span data-ttu-id="5ecb6-132">DateTime</span><span class="sxs-lookup"><span data-stu-id="5ecb6-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="5ecb6-133">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="5ecb6-133">Columns</span></span>  
  
|<span data-ttu-id="5ecb6-134">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5ecb6-134">ColumnName</span></span>|<span data-ttu-id="5ecb6-135">DataType</span><span class="sxs-lookup"><span data-stu-id="5ecb6-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5ecb6-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5ecb6-136">TABLE_CATALOG</span></span>|<span data-ttu-id="5ecb6-137">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-137">String</span></span>|  
|<span data-ttu-id="5ecb6-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5ecb6-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="5ecb6-139">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-139">String</span></span>|  
|<span data-ttu-id="5ecb6-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5ecb6-140">TABLE_NAME</span></span>|<span data-ttu-id="5ecb6-141">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-141">String</span></span>|  
|<span data-ttu-id="5ecb6-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="5ecb6-142">COLUMN_NAME</span></span>|<span data-ttu-id="5ecb6-143">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-143">String</span></span>|  
|<span data-ttu-id="5ecb6-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="5ecb6-144">COLUMN_GUID</span></span>|<span data-ttu-id="5ecb6-145">Guid</span><span class="sxs-lookup"><span data-stu-id="5ecb6-145">Guid</span></span>|  
|<span data-ttu-id="5ecb6-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="5ecb6-146">COLUMN_PROPID</span></span>|<span data-ttu-id="5ecb6-147">Int64</span><span class="sxs-lookup"><span data-stu-id="5ecb6-147">Int64</span></span>|  
|<span data-ttu-id="5ecb6-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="5ecb6-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="5ecb6-149">Int64</span><span class="sxs-lookup"><span data-stu-id="5ecb6-149">Int64</span></span>|  
|<span data-ttu-id="5ecb6-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="5ecb6-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="5ecb6-151">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="5ecb6-151">Boolean</span></span>|  
|<span data-ttu-id="5ecb6-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="5ecb6-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="5ecb6-153">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-153">String</span></span>|  
|<span data-ttu-id="5ecb6-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="5ecb6-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="5ecb6-155">Int64</span><span class="sxs-lookup"><span data-stu-id="5ecb6-155">Int64</span></span>|  
|<span data-ttu-id="5ecb6-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="5ecb6-156">IS_NULLABLE</span></span>|<span data-ttu-id="5ecb6-157">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="5ecb6-157">Boolean</span></span>|  
|<span data-ttu-id="5ecb6-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="5ecb6-158">DATA_TYPE</span></span>|<span data-ttu-id="5ecb6-159">Int32</span><span class="sxs-lookup"><span data-stu-id="5ecb6-159">Int32</span></span>|  
|<span data-ttu-id="5ecb6-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="5ecb6-160">TYPE_GUID</span></span>|<span data-ttu-id="5ecb6-161">Guid</span><span class="sxs-lookup"><span data-stu-id="5ecb6-161">Guid</span></span>|  
|<span data-ttu-id="5ecb6-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="5ecb6-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="5ecb6-163">Int64</span><span class="sxs-lookup"><span data-stu-id="5ecb6-163">Int64</span></span>|  
|<span data-ttu-id="5ecb6-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="5ecb6-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="5ecb6-165">Int64</span><span class="sxs-lookup"><span data-stu-id="5ecb6-165">Int64</span></span>|  
|<span data-ttu-id="5ecb6-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="5ecb6-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="5ecb6-167">Int32</span><span class="sxs-lookup"><span data-stu-id="5ecb6-167">Int32</span></span>|  
|<span data-ttu-id="5ecb6-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="5ecb6-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="5ecb6-169">Int16</span><span class="sxs-lookup"><span data-stu-id="5ecb6-169">Int16</span></span>|  
|<span data-ttu-id="5ecb6-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="5ecb6-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="5ecb6-171">Int64</span><span class="sxs-lookup"><span data-stu-id="5ecb6-171">Int64</span></span>|  
|<span data-ttu-id="5ecb6-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5ecb6-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="5ecb6-173">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-173">String</span></span>|  
|<span data-ttu-id="5ecb6-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5ecb6-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="5ecb6-175">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-175">String</span></span>|  
|<span data-ttu-id="5ecb6-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="5ecb6-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="5ecb6-177">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-177">String</span></span>|  
|<span data-ttu-id="5ecb6-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5ecb6-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="5ecb6-179">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-179">String</span></span>|  
|<span data-ttu-id="5ecb6-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5ecb6-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="5ecb6-181">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-181">String</span></span>|  
|<span data-ttu-id="5ecb6-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="5ecb6-182">COLLATION_NAME</span></span>|<span data-ttu-id="5ecb6-183">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-183">String</span></span>|  
|<span data-ttu-id="5ecb6-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5ecb6-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="5ecb6-185">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-185">String</span></span>|  
|<span data-ttu-id="5ecb6-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5ecb6-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="5ecb6-187">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-187">String</span></span>|  
|<span data-ttu-id="5ecb6-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="5ecb6-188">DOMAIN_NAME</span></span>|<span data-ttu-id="5ecb6-189">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-189">String</span></span>|  
|<span data-ttu-id="5ecb6-190">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="5ecb6-190">DESCRIPTION</span></span>|<span data-ttu-id="5ecb6-191">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-191">String</span></span>|  
|<span data-ttu-id="5ecb6-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="5ecb6-192">COLUMN_LCID</span></span>|<span data-ttu-id="5ecb6-193">Int32</span><span class="sxs-lookup"><span data-stu-id="5ecb6-193">Int32</span></span>|  
|<span data-ttu-id="5ecb6-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="5ecb6-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="5ecb6-195">Int32</span><span class="sxs-lookup"><span data-stu-id="5ecb6-195">Int32</span></span>|  
|<span data-ttu-id="5ecb6-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="5ecb6-196">COLUMN_SORTID</span></span>|<span data-ttu-id="5ecb6-197">Int32</span><span class="sxs-lookup"><span data-stu-id="5ecb6-197">Int32</span></span>|  
|<span data-ttu-id="5ecb6-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="5ecb6-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="5ecb6-199">Byte[]</span><span class="sxs-lookup"><span data-stu-id="5ecb6-199">Byte[]</span></span>|  
|<span data-ttu-id="5ecb6-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="5ecb6-200">IS_COMPUTED</span></span>|<span data-ttu-id="5ecb6-201">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="5ecb6-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="5ecb6-202">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="5ecb6-202">Procedures</span></span>  
  
|<span data-ttu-id="5ecb6-203">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5ecb6-203">ColumnName</span></span>|<span data-ttu-id="5ecb6-204">DataType</span><span class="sxs-lookup"><span data-stu-id="5ecb6-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5ecb6-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5ecb6-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="5ecb6-206">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-206">String</span></span>|  
|<span data-ttu-id="5ecb6-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5ecb6-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="5ecb6-208">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-208">String</span></span>|  
|<span data-ttu-id="5ecb6-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="5ecb6-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="5ecb6-210">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-210">String</span></span>|  
|<span data-ttu-id="5ecb6-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="5ecb6-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="5ecb6-212">Int16</span><span class="sxs-lookup"><span data-stu-id="5ecb6-212">Int16</span></span>|  
|<span data-ttu-id="5ecb6-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="5ecb6-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="5ecb6-214">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-214">String</span></span>|  
|<span data-ttu-id="5ecb6-215">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="5ecb6-215">DESCRIPTION</span></span>|<span data-ttu-id="5ecb6-216">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-216">String</span></span>|  
|<span data-ttu-id="5ecb6-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="5ecb6-217">DATE_CREATED</span></span>|<span data-ttu-id="5ecb6-218">DateTime</span><span class="sxs-lookup"><span data-stu-id="5ecb6-218">DateTime</span></span>|  
|<span data-ttu-id="5ecb6-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="5ecb6-219">DATE_MODIFIED</span></span>|<span data-ttu-id="5ecb6-220">DateTime</span><span class="sxs-lookup"><span data-stu-id="5ecb6-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="5ecb6-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="5ecb6-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="5ecb6-222">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5ecb6-222">ColumnName</span></span>|<span data-ttu-id="5ecb6-223">DataType</span><span class="sxs-lookup"><span data-stu-id="5ecb6-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5ecb6-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5ecb6-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="5ecb6-225">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-225">String</span></span>|  
|<span data-ttu-id="5ecb6-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5ecb6-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="5ecb6-227">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-227">String</span></span>|  
|<span data-ttu-id="5ecb6-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="5ecb6-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="5ecb6-229">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-229">String</span></span>|  
|<span data-ttu-id="5ecb6-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="5ecb6-230">PARAMETER_NAME</span></span>|<span data-ttu-id="5ecb6-231">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-231">String</span></span>|  
|<span data-ttu-id="5ecb6-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="5ecb6-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="5ecb6-233">Int32</span><span class="sxs-lookup"><span data-stu-id="5ecb6-233">Int32</span></span>|  
|<span data-ttu-id="5ecb6-234">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="5ecb6-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="5ecb6-235">Int32</span><span class="sxs-lookup"><span data-stu-id="5ecb6-235">Int32</span></span>|  
|<span data-ttu-id="5ecb6-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="5ecb6-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="5ecb6-237">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="5ecb6-237">Boolean</span></span>|  
|<span data-ttu-id="5ecb6-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="5ecb6-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="5ecb6-239">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-239">String</span></span>|  
|<span data-ttu-id="5ecb6-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="5ecb6-240">IS_NULLABLE</span></span>|<span data-ttu-id="5ecb6-241">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="5ecb6-241">Boolean</span></span>|  
|<span data-ttu-id="5ecb6-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="5ecb6-242">DATA_TYPE</span></span>|<span data-ttu-id="5ecb6-243">Int32</span><span class="sxs-lookup"><span data-stu-id="5ecb6-243">Int32</span></span>|  
|<span data-ttu-id="5ecb6-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="5ecb6-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="5ecb6-245">Int64</span><span class="sxs-lookup"><span data-stu-id="5ecb6-245">Int64</span></span>|  
|<span data-ttu-id="5ecb6-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="5ecb6-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="5ecb6-247">Int64</span><span class="sxs-lookup"><span data-stu-id="5ecb6-247">Int64</span></span>|  
|<span data-ttu-id="5ecb6-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="5ecb6-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="5ecb6-249">Int32</span><span class="sxs-lookup"><span data-stu-id="5ecb6-249">Int32</span></span>|  
|<span data-ttu-id="5ecb6-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="5ecb6-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="5ecb6-251">Int16</span><span class="sxs-lookup"><span data-stu-id="5ecb6-251">Int16</span></span>|  
|<span data-ttu-id="5ecb6-252">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="5ecb6-252">DESCRIPTION</span></span>|<span data-ttu-id="5ecb6-253">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-253">String</span></span>|  
|<span data-ttu-id="5ecb6-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="5ecb6-254">TYPE_NAME</span></span>|<span data-ttu-id="5ecb6-255">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-255">String</span></span>|  
|<span data-ttu-id="5ecb6-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="5ecb6-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="5ecb6-257">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="5ecb6-258">Katalog</span><span class="sxs-lookup"><span data-stu-id="5ecb6-258">Catalog</span></span>  
  
|<span data-ttu-id="5ecb6-259">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5ecb6-259">ColumnName</span></span>|<span data-ttu-id="5ecb6-260">DataType</span><span class="sxs-lookup"><span data-stu-id="5ecb6-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5ecb6-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="5ecb6-261">CATALOG_NAME</span></span>|<span data-ttu-id="5ecb6-262">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-262">String</span></span>|  
|<span data-ttu-id="5ecb6-263">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="5ecb6-263">DESCRIPTION</span></span>|<span data-ttu-id="5ecb6-264">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="5ecb6-265">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="5ecb6-265">Indexes</span></span>  
  
|<span data-ttu-id="5ecb6-266">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5ecb6-266">ColumnName</span></span>|<span data-ttu-id="5ecb6-267">DataType</span><span class="sxs-lookup"><span data-stu-id="5ecb6-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5ecb6-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5ecb6-268">TABLE_CATALOG</span></span>|<span data-ttu-id="5ecb6-269">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-269">String</span></span>|  
|<span data-ttu-id="5ecb6-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5ecb6-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="5ecb6-271">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-271">String</span></span>|  
|<span data-ttu-id="5ecb6-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5ecb6-272">TABLE_NAME</span></span>|<span data-ttu-id="5ecb6-273">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-273">String</span></span>|  
|<span data-ttu-id="5ecb6-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5ecb6-274">INDEX_CATALOG</span></span>|<span data-ttu-id="5ecb6-275">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-275">String</span></span>|  
|<span data-ttu-id="5ecb6-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5ecb6-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="5ecb6-277">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-277">String</span></span>|  
|<span data-ttu-id="5ecb6-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="5ecb6-278">INDEX_NAME</span></span>|<span data-ttu-id="5ecb6-279">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-279">String</span></span>|  
|<span data-ttu-id="5ecb6-280">İŞLEM</span><span class="sxs-lookup"><span data-stu-id="5ecb6-280">PRIMARY_KEY</span></span>|<span data-ttu-id="5ecb6-281">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="5ecb6-281">Boolean</span></span>|  
|<span data-ttu-id="5ecb6-282">BENZERSİZ</span><span class="sxs-lookup"><span data-stu-id="5ecb6-282">UNIQUE</span></span>|<span data-ttu-id="5ecb6-283">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="5ecb6-283">Boolean</span></span>|  
|<span data-ttu-id="5ecb6-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="5ecb6-284">CLUSTERED</span></span>|<span data-ttu-id="5ecb6-285">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="5ecb6-285">Boolean</span></span>|  
|<span data-ttu-id="5ecb6-286">TÜRÜ</span><span class="sxs-lookup"><span data-stu-id="5ecb6-286">TYPE</span></span>|<span data-ttu-id="5ecb6-287">Int32</span><span class="sxs-lookup"><span data-stu-id="5ecb6-287">Int32</span></span>|  
|<span data-ttu-id="5ecb6-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="5ecb6-288">FILL_FACTOR</span></span>|<span data-ttu-id="5ecb6-289">Int32</span><span class="sxs-lookup"><span data-stu-id="5ecb6-289">Int32</span></span>|  
|<span data-ttu-id="5ecb6-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="5ecb6-290">INITIAL_SIZE</span></span>|<span data-ttu-id="5ecb6-291">Int32</span><span class="sxs-lookup"><span data-stu-id="5ecb6-291">Int32</span></span>|  
|<span data-ttu-id="5ecb6-292">NULLS</span><span class="sxs-lookup"><span data-stu-id="5ecb6-292">NULLS</span></span>|<span data-ttu-id="5ecb6-293">Int32</span><span class="sxs-lookup"><span data-stu-id="5ecb6-293">Int32</span></span>|  
|<span data-ttu-id="5ecb6-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="5ecb6-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="5ecb6-295">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="5ecb6-295">Boolean</span></span>|  
|<span data-ttu-id="5ecb6-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="5ecb6-296">AUTO_UPDATE</span></span>|<span data-ttu-id="5ecb6-297">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="5ecb6-297">Boolean</span></span>|  
|<span data-ttu-id="5ecb6-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="5ecb6-298">NULL_COLLATION</span></span>|<span data-ttu-id="5ecb6-299">Int32</span><span class="sxs-lookup"><span data-stu-id="5ecb6-299">Int32</span></span>|  
|<span data-ttu-id="5ecb6-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="5ecb6-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="5ecb6-301">Int64</span><span class="sxs-lookup"><span data-stu-id="5ecb6-301">Int64</span></span>|  
|<span data-ttu-id="5ecb6-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="5ecb6-302">COLUMN_NAME</span></span>|<span data-ttu-id="5ecb6-303">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-303">String</span></span>|  
|<span data-ttu-id="5ecb6-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="5ecb6-304">COLUMN_GUID</span></span>|<span data-ttu-id="5ecb6-305">Guid</span><span class="sxs-lookup"><span data-stu-id="5ecb6-305">Guid</span></span>|  
|<span data-ttu-id="5ecb6-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="5ecb6-306">COLUMN_PROPID</span></span>|<span data-ttu-id="5ecb6-307">Int64</span><span class="sxs-lookup"><span data-stu-id="5ecb6-307">Int64</span></span>|  
|<span data-ttu-id="5ecb6-308">HARMANLAMA</span><span class="sxs-lookup"><span data-stu-id="5ecb6-308">COLLATION</span></span>|<span data-ttu-id="5ecb6-309">Int16</span><span class="sxs-lookup"><span data-stu-id="5ecb6-309">Int16</span></span>|  
|<span data-ttu-id="5ecb6-310">ÖNEM DÜZEYİ</span><span class="sxs-lookup"><span data-stu-id="5ecb6-310">CARDINALITY</span></span>|<span data-ttu-id="5ecb6-311">Ondalık</span><span class="sxs-lookup"><span data-stu-id="5ecb6-311">Decimal</span></span>|  
|<span data-ttu-id="5ecb6-312">SAYFALARI</span><span class="sxs-lookup"><span data-stu-id="5ecb6-312">PAGES</span></span>|<span data-ttu-id="5ecb6-313">Int32</span><span class="sxs-lookup"><span data-stu-id="5ecb6-313">Int32</span></span>|  
|<span data-ttu-id="5ecb6-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="5ecb6-314">FILTER_CONDITION</span></span>|<span data-ttu-id="5ecb6-315">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-315">String</span></span>|  
|<span data-ttu-id="5ecb6-316">TÜMLEŞİK</span><span class="sxs-lookup"><span data-stu-id="5ecb6-316">INTEGRATED</span></span>|<span data-ttu-id="5ecb6-317">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="5ecb6-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="5ecb6-318">Microsoft Oracle OLE DB sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="5ecb6-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="5ecb6-319">Microsoft Oracle OLE DB sürücüsü aşağıdaki özel şema koleksiyonları ortak şema koleksiyonları yanı sıra destekler:</span><span class="sxs-lookup"><span data-stu-id="5ecb6-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="5ecb6-320">Tabloları</span><span class="sxs-lookup"><span data-stu-id="5ecb6-320">Tables</span></span>  
  
- <span data-ttu-id="5ecb6-321">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="5ecb6-321">Columns</span></span>  
  
- <span data-ttu-id="5ecb6-322">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="5ecb6-322">Procedures</span></span>  
  
- <span data-ttu-id="5ecb6-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="5ecb6-323">ProcedureColumns</span></span>  
  
- <span data-ttu-id="5ecb6-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="5ecb6-324">ProcedureParameters</span></span>  
  
- <span data-ttu-id="5ecb6-325">Görünümler</span><span class="sxs-lookup"><span data-stu-id="5ecb6-325">Views</span></span>  
  
- <span data-ttu-id="5ecb6-326">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="5ecb6-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="5ecb6-327">Tabloları</span><span class="sxs-lookup"><span data-stu-id="5ecb6-327">Tables</span></span>  
  
|<span data-ttu-id="5ecb6-328">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5ecb6-328">ColumnName</span></span>|<span data-ttu-id="5ecb6-329">DataType</span><span class="sxs-lookup"><span data-stu-id="5ecb6-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5ecb6-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5ecb6-330">TABLE_CATALOG</span></span>|<span data-ttu-id="5ecb6-331">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-331">String</span></span>|  
|<span data-ttu-id="5ecb6-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5ecb6-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="5ecb6-333">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-333">String</span></span>|  
|<span data-ttu-id="5ecb6-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5ecb6-334">TABLE_NAME</span></span>|<span data-ttu-id="5ecb6-335">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-335">String</span></span>|  
|<span data-ttu-id="5ecb6-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="5ecb6-336">TABLE_TYPE</span></span>|<span data-ttu-id="5ecb6-337">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-337">String</span></span>|  
|<span data-ttu-id="5ecb6-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="5ecb6-338">TABLE_GUID</span></span>|<span data-ttu-id="5ecb6-339">Guid</span><span class="sxs-lookup"><span data-stu-id="5ecb6-339">Guid</span></span>|  
|<span data-ttu-id="5ecb6-340">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="5ecb6-340">DESCRIPTION</span></span>|<span data-ttu-id="5ecb6-341">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-341">String</span></span>|  
|<span data-ttu-id="5ecb6-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="5ecb6-342">TABLE_PROPID</span></span>|<span data-ttu-id="5ecb6-343">Int64</span><span class="sxs-lookup"><span data-stu-id="5ecb6-343">Int64</span></span>|  
|<span data-ttu-id="5ecb6-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="5ecb6-344">DATE_CREATED</span></span>|<span data-ttu-id="5ecb6-345">DateTime</span><span class="sxs-lookup"><span data-stu-id="5ecb6-345">DateTime</span></span>|  
|<span data-ttu-id="5ecb6-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="5ecb6-346">DATE_MODIFIED</span></span>|<span data-ttu-id="5ecb6-347">DateTime</span><span class="sxs-lookup"><span data-stu-id="5ecb6-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="5ecb6-348">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="5ecb6-348">Columns</span></span>  
  
|<span data-ttu-id="5ecb6-349">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5ecb6-349">ColumnName</span></span>|<span data-ttu-id="5ecb6-350">DataType</span><span class="sxs-lookup"><span data-stu-id="5ecb6-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5ecb6-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5ecb6-351">TABLE_CATALOG</span></span>|<span data-ttu-id="5ecb6-352">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-352">String</span></span>|  
|<span data-ttu-id="5ecb6-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5ecb6-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="5ecb6-354">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-354">String</span></span>|  
|<span data-ttu-id="5ecb6-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5ecb6-355">TABLE_NAME</span></span>|<span data-ttu-id="5ecb6-356">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-356">String</span></span>|  
|<span data-ttu-id="5ecb6-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="5ecb6-357">COLUMN_NAME</span></span>|<span data-ttu-id="5ecb6-358">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-358">String</span></span>|  
|<span data-ttu-id="5ecb6-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="5ecb6-359">COLUMN_GUID</span></span>|<span data-ttu-id="5ecb6-360">Guid</span><span class="sxs-lookup"><span data-stu-id="5ecb6-360">Guid</span></span>|  
|<span data-ttu-id="5ecb6-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="5ecb6-361">COLUMN_PROPID</span></span>|<span data-ttu-id="5ecb6-362">Int64</span><span class="sxs-lookup"><span data-stu-id="5ecb6-362">Int64</span></span>|  
|<span data-ttu-id="5ecb6-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="5ecb6-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="5ecb6-364">Int64</span><span class="sxs-lookup"><span data-stu-id="5ecb6-364">Int64</span></span>|  
|<span data-ttu-id="5ecb6-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="5ecb6-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="5ecb6-366">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="5ecb6-366">Boolean</span></span>|  
|<span data-ttu-id="5ecb6-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="5ecb6-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="5ecb6-368">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-368">String</span></span>|  
|<span data-ttu-id="5ecb6-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="5ecb6-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="5ecb6-370">Int64</span><span class="sxs-lookup"><span data-stu-id="5ecb6-370">Int64</span></span>|  
|<span data-ttu-id="5ecb6-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="5ecb6-371">IS_NULLABLE</span></span>|<span data-ttu-id="5ecb6-372">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="5ecb6-372">Boolean</span></span>|  
|<span data-ttu-id="5ecb6-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="5ecb6-373">DATA_TYPE</span></span>|<span data-ttu-id="5ecb6-374">Int32</span><span class="sxs-lookup"><span data-stu-id="5ecb6-374">Int32</span></span>|  
|<span data-ttu-id="5ecb6-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="5ecb6-375">TYPE_GUID</span></span>|<span data-ttu-id="5ecb6-376">Guid</span><span class="sxs-lookup"><span data-stu-id="5ecb6-376">Guid</span></span>|  
|<span data-ttu-id="5ecb6-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="5ecb6-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="5ecb6-378">Int64</span><span class="sxs-lookup"><span data-stu-id="5ecb6-378">Int64</span></span>|  
|<span data-ttu-id="5ecb6-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="5ecb6-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="5ecb6-380">Int64</span><span class="sxs-lookup"><span data-stu-id="5ecb6-380">Int64</span></span>|  
|<span data-ttu-id="5ecb6-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="5ecb6-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="5ecb6-382">Int32</span><span class="sxs-lookup"><span data-stu-id="5ecb6-382">Int32</span></span>|  
|<span data-ttu-id="5ecb6-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="5ecb6-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="5ecb6-384">Int16</span><span class="sxs-lookup"><span data-stu-id="5ecb6-384">Int16</span></span>|  
|<span data-ttu-id="5ecb6-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="5ecb6-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="5ecb6-386">Int64</span><span class="sxs-lookup"><span data-stu-id="5ecb6-386">Int64</span></span>|  
|<span data-ttu-id="5ecb6-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5ecb6-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="5ecb6-388">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-388">String</span></span>|  
|<span data-ttu-id="5ecb6-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5ecb6-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="5ecb6-390">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-390">String</span></span>|  
|<span data-ttu-id="5ecb6-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="5ecb6-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="5ecb6-392">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-392">String</span></span>|  
|<span data-ttu-id="5ecb6-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5ecb6-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="5ecb6-394">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-394">String</span></span>|  
|<span data-ttu-id="5ecb6-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5ecb6-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="5ecb6-396">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-396">String</span></span>|  
|<span data-ttu-id="5ecb6-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="5ecb6-397">COLLATION_NAME</span></span>|<span data-ttu-id="5ecb6-398">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-398">String</span></span>|  
|<span data-ttu-id="5ecb6-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5ecb6-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="5ecb6-400">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-400">String</span></span>|  
|<span data-ttu-id="5ecb6-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5ecb6-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="5ecb6-402">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-402">String</span></span>|  
|<span data-ttu-id="5ecb6-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="5ecb6-403">DOMAIN_NAME</span></span>|<span data-ttu-id="5ecb6-404">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-404">String</span></span>|  
|<span data-ttu-id="5ecb6-405">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="5ecb6-405">DESCRIPTION</span></span>|<span data-ttu-id="5ecb6-406">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="5ecb6-407">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="5ecb6-407">Procedures</span></span>  
  
|<span data-ttu-id="5ecb6-408">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5ecb6-408">ColumnName</span></span>|<span data-ttu-id="5ecb6-409">DataType</span><span class="sxs-lookup"><span data-stu-id="5ecb6-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5ecb6-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5ecb6-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="5ecb6-411">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-411">String</span></span>|  
|<span data-ttu-id="5ecb6-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5ecb6-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="5ecb6-413">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-413">String</span></span>|  
|<span data-ttu-id="5ecb6-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="5ecb6-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="5ecb6-415">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-415">String</span></span>|  
|<span data-ttu-id="5ecb6-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="5ecb6-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="5ecb6-417">Int16</span><span class="sxs-lookup"><span data-stu-id="5ecb6-417">Int16</span></span>|  
|<span data-ttu-id="5ecb6-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="5ecb6-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="5ecb6-419">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-419">String</span></span>|  
|<span data-ttu-id="5ecb6-420">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="5ecb6-420">DESCRIPTION</span></span>|<span data-ttu-id="5ecb6-421">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-421">String</span></span>|  
|<span data-ttu-id="5ecb6-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="5ecb6-422">DATE_CREATED</span></span>|<span data-ttu-id="5ecb6-423">DateTime</span><span class="sxs-lookup"><span data-stu-id="5ecb6-423">DateTime</span></span>|  
|<span data-ttu-id="5ecb6-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="5ecb6-424">DATE_MODIFIED</span></span>|<span data-ttu-id="5ecb6-425">DateTime</span><span class="sxs-lookup"><span data-stu-id="5ecb6-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="5ecb6-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="5ecb6-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="5ecb6-427">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5ecb6-427">ColumnName</span></span>|<span data-ttu-id="5ecb6-428">DataType</span><span class="sxs-lookup"><span data-stu-id="5ecb6-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5ecb6-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5ecb6-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="5ecb6-430">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-430">String</span></span>|  
|<span data-ttu-id="5ecb6-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5ecb6-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="5ecb6-432">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-432">String</span></span>|  
|<span data-ttu-id="5ecb6-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="5ecb6-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="5ecb6-434">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-434">String</span></span>|  
|<span data-ttu-id="5ecb6-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="5ecb6-435">COLUMN_NAME</span></span>|<span data-ttu-id="5ecb6-436">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-436">String</span></span>|  
|<span data-ttu-id="5ecb6-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="5ecb6-437">COLUMN_GUID</span></span>|<span data-ttu-id="5ecb6-438">Guid</span><span class="sxs-lookup"><span data-stu-id="5ecb6-438">Guid</span></span>|  
|<span data-ttu-id="5ecb6-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="5ecb6-439">COLUMN_PROPID</span></span>|<span data-ttu-id="5ecb6-440">Int64</span><span class="sxs-lookup"><span data-stu-id="5ecb6-440">Int64</span></span>|  
|<span data-ttu-id="5ecb6-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="5ecb6-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="5ecb6-442">Int64</span><span class="sxs-lookup"><span data-stu-id="5ecb6-442">Int64</span></span>|  
|<span data-ttu-id="5ecb6-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="5ecb6-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="5ecb6-444">Int64</span><span class="sxs-lookup"><span data-stu-id="5ecb6-444">Int64</span></span>|  
|<span data-ttu-id="5ecb6-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="5ecb6-445">IS_NULLABLE</span></span>|<span data-ttu-id="5ecb6-446">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="5ecb6-446">Boolean</span></span>|  
|<span data-ttu-id="5ecb6-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="5ecb6-447">DATA_TYPE</span></span>|<span data-ttu-id="5ecb6-448">Int32</span><span class="sxs-lookup"><span data-stu-id="5ecb6-448">Int32</span></span>|  
|<span data-ttu-id="5ecb6-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="5ecb6-449">TYPE_GUID</span></span>|<span data-ttu-id="5ecb6-450">Guid</span><span class="sxs-lookup"><span data-stu-id="5ecb6-450">Guid</span></span>|  
|<span data-ttu-id="5ecb6-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="5ecb6-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="5ecb6-452">Int64</span><span class="sxs-lookup"><span data-stu-id="5ecb6-452">Int64</span></span>|  
|<span data-ttu-id="5ecb6-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="5ecb6-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="5ecb6-454">Int64</span><span class="sxs-lookup"><span data-stu-id="5ecb6-454">Int64</span></span>|  
|<span data-ttu-id="5ecb6-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="5ecb6-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="5ecb6-456">Int32</span><span class="sxs-lookup"><span data-stu-id="5ecb6-456">Int32</span></span>|  
|<span data-ttu-id="5ecb6-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="5ecb6-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="5ecb6-458">Int16</span><span class="sxs-lookup"><span data-stu-id="5ecb6-458">Int16</span></span>|  
|<span data-ttu-id="5ecb6-459">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="5ecb6-459">DESCRIPTION</span></span>|<span data-ttu-id="5ecb6-460">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-460">String</span></span>|  
|<span data-ttu-id="5ecb6-461">AŞIRI YÜKLEME</span><span class="sxs-lookup"><span data-stu-id="5ecb6-461">OVERLOAD</span></span>|<span data-ttu-id="5ecb6-462">Int16</span><span class="sxs-lookup"><span data-stu-id="5ecb6-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="5ecb6-463">Görünümler</span><span class="sxs-lookup"><span data-stu-id="5ecb6-463">Views</span></span>  
  
|<span data-ttu-id="5ecb6-464">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5ecb6-464">ColumnName</span></span>|<span data-ttu-id="5ecb6-465">DataType</span><span class="sxs-lookup"><span data-stu-id="5ecb6-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5ecb6-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5ecb6-466">TABLE_CATALOG</span></span>|<span data-ttu-id="5ecb6-467">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-467">String</span></span>|  
|<span data-ttu-id="5ecb6-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5ecb6-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="5ecb6-469">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-469">String</span></span>|  
|<span data-ttu-id="5ecb6-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5ecb6-470">TABLE_NAME</span></span>|<span data-ttu-id="5ecb6-471">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-471">String</span></span>|  
|<span data-ttu-id="5ecb6-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="5ecb6-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="5ecb6-473">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-473">String</span></span>|  
|<span data-ttu-id="5ecb6-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="5ecb6-474">CHECK_OPTION</span></span>|<span data-ttu-id="5ecb6-475">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="5ecb6-475">Boolean</span></span>|  
|<span data-ttu-id="5ecb6-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="5ecb6-476">IS_UPDATABLE</span></span>|<span data-ttu-id="5ecb6-477">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="5ecb6-477">Boolean</span></span>|  
|<span data-ttu-id="5ecb6-478">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="5ecb6-478">DESCRIPTION</span></span>|<span data-ttu-id="5ecb6-479">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-479">String</span></span>|  
|<span data-ttu-id="5ecb6-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="5ecb6-480">DATE_CREATED</span></span>|<span data-ttu-id="5ecb6-481">DateTime</span><span class="sxs-lookup"><span data-stu-id="5ecb6-481">DateTime</span></span>|  
|<span data-ttu-id="5ecb6-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="5ecb6-482">DATE_MODIFIED</span></span>|<span data-ttu-id="5ecb6-483">DateTime</span><span class="sxs-lookup"><span data-stu-id="5ecb6-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="5ecb6-484">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="5ecb6-484">Indexes</span></span>  
  
|<span data-ttu-id="5ecb6-485">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5ecb6-485">ColumnName</span></span>|<span data-ttu-id="5ecb6-486">DataType</span><span class="sxs-lookup"><span data-stu-id="5ecb6-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5ecb6-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5ecb6-487">TABLE_CATALOG</span></span>|<span data-ttu-id="5ecb6-488">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-488">String</span></span>|  
|<span data-ttu-id="5ecb6-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5ecb6-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="5ecb6-490">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-490">String</span></span>|  
|<span data-ttu-id="5ecb6-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5ecb6-491">TABLE_NAME</span></span>|<span data-ttu-id="5ecb6-492">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-492">String</span></span>|  
|<span data-ttu-id="5ecb6-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5ecb6-493">INDEX_CATALOG</span></span>|<span data-ttu-id="5ecb6-494">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-494">String</span></span>|  
|<span data-ttu-id="5ecb6-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5ecb6-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="5ecb6-496">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-496">String</span></span>|  
|<span data-ttu-id="5ecb6-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="5ecb6-497">INDEX_NAME</span></span>|<span data-ttu-id="5ecb6-498">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-498">String</span></span>|  
|<span data-ttu-id="5ecb6-499">İŞLEM</span><span class="sxs-lookup"><span data-stu-id="5ecb6-499">PRIMARY_KEY</span></span>|<span data-ttu-id="5ecb6-500">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="5ecb6-500">Boolean</span></span>|  
|<span data-ttu-id="5ecb6-501">BENZERSİZ</span><span class="sxs-lookup"><span data-stu-id="5ecb6-501">UNIQUE</span></span>|<span data-ttu-id="5ecb6-502">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="5ecb6-502">Boolean</span></span>|  
|<span data-ttu-id="5ecb6-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="5ecb6-503">CLUSTERED</span></span>|<span data-ttu-id="5ecb6-504">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="5ecb6-504">Boolean</span></span>|  
|<span data-ttu-id="5ecb6-505">TÜRÜ</span><span class="sxs-lookup"><span data-stu-id="5ecb6-505">TYPE</span></span>|<span data-ttu-id="5ecb6-506">Int32</span><span class="sxs-lookup"><span data-stu-id="5ecb6-506">Int32</span></span>|  
|<span data-ttu-id="5ecb6-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="5ecb6-507">FILL_FACTOR</span></span>|<span data-ttu-id="5ecb6-508">Int32</span><span class="sxs-lookup"><span data-stu-id="5ecb6-508">Int32</span></span>|  
|<span data-ttu-id="5ecb6-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="5ecb6-509">INITIAL_SIZE</span></span>|<span data-ttu-id="5ecb6-510">Int32</span><span class="sxs-lookup"><span data-stu-id="5ecb6-510">Int32</span></span>|  
|<span data-ttu-id="5ecb6-511">NULLS</span><span class="sxs-lookup"><span data-stu-id="5ecb6-511">NULLS</span></span>|<span data-ttu-id="5ecb6-512">Int32</span><span class="sxs-lookup"><span data-stu-id="5ecb6-512">Int32</span></span>|  
|<span data-ttu-id="5ecb6-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="5ecb6-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="5ecb6-514">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="5ecb6-514">Boolean</span></span>|  
|<span data-ttu-id="5ecb6-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="5ecb6-515">AUTO_UPDATE</span></span>|<span data-ttu-id="5ecb6-516">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="5ecb6-516">Boolean</span></span>|  
|<span data-ttu-id="5ecb6-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="5ecb6-517">NULL_COLLATION</span></span>|<span data-ttu-id="5ecb6-518">Int32</span><span class="sxs-lookup"><span data-stu-id="5ecb6-518">Int32</span></span>|  
|<span data-ttu-id="5ecb6-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="5ecb6-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="5ecb6-520">Int64</span><span class="sxs-lookup"><span data-stu-id="5ecb6-520">Int64</span></span>|  
|<span data-ttu-id="5ecb6-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="5ecb6-521">COLUMN_NAME</span></span>|<span data-ttu-id="5ecb6-522">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-522">String</span></span>|  
|<span data-ttu-id="5ecb6-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="5ecb6-523">COLUMN_GUID</span></span>|<span data-ttu-id="5ecb6-524">Guid</span><span class="sxs-lookup"><span data-stu-id="5ecb6-524">Guid</span></span>|  
|<span data-ttu-id="5ecb6-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="5ecb6-525">COLUMN_PROPID</span></span>|<span data-ttu-id="5ecb6-526">Int64</span><span class="sxs-lookup"><span data-stu-id="5ecb6-526">Int64</span></span>|  
|<span data-ttu-id="5ecb6-527">HARMANLAMA</span><span class="sxs-lookup"><span data-stu-id="5ecb6-527">COLLATION</span></span>|<span data-ttu-id="5ecb6-528">Int16</span><span class="sxs-lookup"><span data-stu-id="5ecb6-528">Int16</span></span>|  
|<span data-ttu-id="5ecb6-529">ÖNEM DÜZEYİ</span><span class="sxs-lookup"><span data-stu-id="5ecb6-529">CARDINALITY</span></span>|<span data-ttu-id="5ecb6-530">Ondalık</span><span class="sxs-lookup"><span data-stu-id="5ecb6-530">Decimal</span></span>|  
|<span data-ttu-id="5ecb6-531">SAYFALARI</span><span class="sxs-lookup"><span data-stu-id="5ecb6-531">PAGES</span></span>|<span data-ttu-id="5ecb6-532">Int32</span><span class="sxs-lookup"><span data-stu-id="5ecb6-532">Int32</span></span>|  
|<span data-ttu-id="5ecb6-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="5ecb6-533">FILTER_CONDITION</span></span>|<span data-ttu-id="5ecb6-534">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-534">String</span></span>|  
|<span data-ttu-id="5ecb6-535">TÜMLEŞİK</span><span class="sxs-lookup"><span data-stu-id="5ecb6-535">INTEGRATED</span></span>|<span data-ttu-id="5ecb6-536">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="5ecb6-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="5ecb6-537">Microsoft Jet OLE DB sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="5ecb6-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="5ecb6-538">Microsoft Jet OLE DB sürücüsü aşağıdaki özel şema koleksiyonları ortak şema koleksiyonları yanı sıra destekler:</span><span class="sxs-lookup"><span data-stu-id="5ecb6-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="5ecb6-539">Tabloları</span><span class="sxs-lookup"><span data-stu-id="5ecb6-539">Tables</span></span>  
  
- <span data-ttu-id="5ecb6-540">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="5ecb6-540">Columns</span></span>  
  
- <span data-ttu-id="5ecb6-541">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="5ecb6-541">Procedures</span></span>  
  
- <span data-ttu-id="5ecb6-542">Görünümler</span><span class="sxs-lookup"><span data-stu-id="5ecb6-542">Views</span></span>  
  
- <span data-ttu-id="5ecb6-543">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="5ecb6-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="5ecb6-544">Tabloları</span><span class="sxs-lookup"><span data-stu-id="5ecb6-544">Tables</span></span>  
  
|<span data-ttu-id="5ecb6-545">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5ecb6-545">ColumnName</span></span>|<span data-ttu-id="5ecb6-546">DataType</span><span class="sxs-lookup"><span data-stu-id="5ecb6-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5ecb6-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5ecb6-547">TABLE_CATALOG</span></span>|<span data-ttu-id="5ecb6-548">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-548">String</span></span>|  
|<span data-ttu-id="5ecb6-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5ecb6-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="5ecb6-550">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-550">String</span></span>|  
|<span data-ttu-id="5ecb6-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5ecb6-551">TABLE_NAME</span></span>|<span data-ttu-id="5ecb6-552">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-552">String</span></span>|  
|<span data-ttu-id="5ecb6-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="5ecb6-553">TABLE_TYPE</span></span>|<span data-ttu-id="5ecb6-554">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-554">String</span></span>|  
|<span data-ttu-id="5ecb6-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="5ecb6-555">TABLE_GUID</span></span>|<span data-ttu-id="5ecb6-556">Guid</span><span class="sxs-lookup"><span data-stu-id="5ecb6-556">Guid</span></span>|  
|<span data-ttu-id="5ecb6-557">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="5ecb6-557">DESCRIPTION</span></span>|<span data-ttu-id="5ecb6-558">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-558">String</span></span>|  
|<span data-ttu-id="5ecb6-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="5ecb6-559">TABLE_PROPID</span></span>|<span data-ttu-id="5ecb6-560">Int64</span><span class="sxs-lookup"><span data-stu-id="5ecb6-560">Int64</span></span>|  
|<span data-ttu-id="5ecb6-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="5ecb6-561">DATE_CREATED</span></span>|<span data-ttu-id="5ecb6-562">DateTime</span><span class="sxs-lookup"><span data-stu-id="5ecb6-562">DateTime</span></span>|  
|<span data-ttu-id="5ecb6-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="5ecb6-563">DATE_MODIFIED</span></span>|<span data-ttu-id="5ecb6-564">DateTime</span><span class="sxs-lookup"><span data-stu-id="5ecb6-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="5ecb6-565">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="5ecb6-565">Columns</span></span>  
  
|<span data-ttu-id="5ecb6-566">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5ecb6-566">ColumnName</span></span>|<span data-ttu-id="5ecb6-567">DataType</span><span class="sxs-lookup"><span data-stu-id="5ecb6-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5ecb6-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5ecb6-568">TABLE_CATALOG</span></span>|<span data-ttu-id="5ecb6-569">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-569">String</span></span>|  
|<span data-ttu-id="5ecb6-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5ecb6-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="5ecb6-571">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-571">String</span></span>|  
|<span data-ttu-id="5ecb6-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5ecb6-572">TABLE_NAME</span></span>|<span data-ttu-id="5ecb6-573">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-573">String</span></span>|  
|<span data-ttu-id="5ecb6-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="5ecb6-574">COLUMN_NAME</span></span>|<span data-ttu-id="5ecb6-575">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-575">String</span></span>|  
|<span data-ttu-id="5ecb6-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="5ecb6-576">COLUMN_GUID</span></span>|<span data-ttu-id="5ecb6-577">Guid</span><span class="sxs-lookup"><span data-stu-id="5ecb6-577">Guid</span></span>|  
|<span data-ttu-id="5ecb6-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="5ecb6-578">COLUMN_PROPID</span></span>|<span data-ttu-id="5ecb6-579">Int64</span><span class="sxs-lookup"><span data-stu-id="5ecb6-579">Int64</span></span>|  
|<span data-ttu-id="5ecb6-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="5ecb6-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="5ecb6-581">Int64</span><span class="sxs-lookup"><span data-stu-id="5ecb6-581">Int64</span></span>|  
|<span data-ttu-id="5ecb6-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="5ecb6-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="5ecb6-583">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="5ecb6-583">Boolean</span></span>|  
|<span data-ttu-id="5ecb6-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="5ecb6-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="5ecb6-585">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-585">String</span></span>|  
|<span data-ttu-id="5ecb6-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="5ecb6-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="5ecb6-587">Int64</span><span class="sxs-lookup"><span data-stu-id="5ecb6-587">Int64</span></span>|  
|<span data-ttu-id="5ecb6-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="5ecb6-588">IS_NULLABLE</span></span>|<span data-ttu-id="5ecb6-589">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="5ecb6-589">Boolean</span></span>|  
|<span data-ttu-id="5ecb6-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="5ecb6-590">DATA_TYPE</span></span>|<span data-ttu-id="5ecb6-591">Int32</span><span class="sxs-lookup"><span data-stu-id="5ecb6-591">Int32</span></span>|  
|<span data-ttu-id="5ecb6-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="5ecb6-592">TYPE_GUID</span></span>|<span data-ttu-id="5ecb6-593">Guid</span><span class="sxs-lookup"><span data-stu-id="5ecb6-593">Guid</span></span>|  
|<span data-ttu-id="5ecb6-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="5ecb6-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="5ecb6-595">Int64</span><span class="sxs-lookup"><span data-stu-id="5ecb6-595">Int64</span></span>|  
|<span data-ttu-id="5ecb6-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="5ecb6-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="5ecb6-597">Int64</span><span class="sxs-lookup"><span data-stu-id="5ecb6-597">Int64</span></span>|  
|<span data-ttu-id="5ecb6-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="5ecb6-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="5ecb6-599">Int32</span><span class="sxs-lookup"><span data-stu-id="5ecb6-599">Int32</span></span>|  
|<span data-ttu-id="5ecb6-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="5ecb6-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="5ecb6-601">Int16</span><span class="sxs-lookup"><span data-stu-id="5ecb6-601">Int16</span></span>|  
|<span data-ttu-id="5ecb6-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="5ecb6-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="5ecb6-603">Int64</span><span class="sxs-lookup"><span data-stu-id="5ecb6-603">Int64</span></span>|  
|<span data-ttu-id="5ecb6-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5ecb6-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="5ecb6-605">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-605">String</span></span>|  
|<span data-ttu-id="5ecb6-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5ecb6-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="5ecb6-607">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-607">String</span></span>|  
|<span data-ttu-id="5ecb6-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="5ecb6-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="5ecb6-609">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-609">String</span></span>|  
|<span data-ttu-id="5ecb6-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5ecb6-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="5ecb6-611">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-611">String</span></span>|  
|<span data-ttu-id="5ecb6-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5ecb6-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="5ecb6-613">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-613">String</span></span>|  
|<span data-ttu-id="5ecb6-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="5ecb6-614">COLLATION_NAME</span></span>|<span data-ttu-id="5ecb6-615">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-615">String</span></span>|  
|<span data-ttu-id="5ecb6-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5ecb6-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="5ecb6-617">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-617">String</span></span>|  
|<span data-ttu-id="5ecb6-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5ecb6-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="5ecb6-619">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-619">String</span></span>|  
|<span data-ttu-id="5ecb6-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="5ecb6-620">DOMAIN_NAME</span></span>|<span data-ttu-id="5ecb6-621">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-621">String</span></span>|  
|<span data-ttu-id="5ecb6-622">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="5ecb6-622">DESCRIPTION</span></span>|<span data-ttu-id="5ecb6-623">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="5ecb6-624">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="5ecb6-624">Procedures</span></span>  
  
|<span data-ttu-id="5ecb6-625">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5ecb6-625">ColumnName</span></span>|<span data-ttu-id="5ecb6-626">DataType</span><span class="sxs-lookup"><span data-stu-id="5ecb6-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5ecb6-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5ecb6-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="5ecb6-628">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-628">String</span></span>|  
|<span data-ttu-id="5ecb6-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5ecb6-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="5ecb6-630">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-630">String</span></span>|  
|<span data-ttu-id="5ecb6-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="5ecb6-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="5ecb6-632">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-632">String</span></span>|  
|<span data-ttu-id="5ecb6-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="5ecb6-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="5ecb6-634">Int16</span><span class="sxs-lookup"><span data-stu-id="5ecb6-634">Int16</span></span>|  
|<span data-ttu-id="5ecb6-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="5ecb6-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="5ecb6-636">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-636">String</span></span>|  
|<span data-ttu-id="5ecb6-637">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="5ecb6-637">DESCRIPTION</span></span>|<span data-ttu-id="5ecb6-638">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-638">String</span></span>|  
|<span data-ttu-id="5ecb6-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="5ecb6-639">DATE_CREATED</span></span>|<span data-ttu-id="5ecb6-640">DateTime</span><span class="sxs-lookup"><span data-stu-id="5ecb6-640">DateTime</span></span>|  
|<span data-ttu-id="5ecb6-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="5ecb6-641">DATE_MODIFIED</span></span>|<span data-ttu-id="5ecb6-642">DateTime</span><span class="sxs-lookup"><span data-stu-id="5ecb6-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="5ecb6-643">Görünümler</span><span class="sxs-lookup"><span data-stu-id="5ecb6-643">Views</span></span>  
  
|<span data-ttu-id="5ecb6-644">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5ecb6-644">ColumnName</span></span>|<span data-ttu-id="5ecb6-645">DataType</span><span class="sxs-lookup"><span data-stu-id="5ecb6-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5ecb6-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5ecb6-646">TABLE_CATALOG</span></span>|<span data-ttu-id="5ecb6-647">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-647">String</span></span>|  
|<span data-ttu-id="5ecb6-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5ecb6-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="5ecb6-649">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-649">String</span></span>|  
|<span data-ttu-id="5ecb6-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5ecb6-650">TABLE_NAME</span></span>|<span data-ttu-id="5ecb6-651">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-651">String</span></span>|  
|<span data-ttu-id="5ecb6-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="5ecb6-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="5ecb6-653">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-653">String</span></span>|  
|<span data-ttu-id="5ecb6-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="5ecb6-654">CHECK_OPTION</span></span>|<span data-ttu-id="5ecb6-655">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="5ecb6-655">Boolean</span></span>|  
|<span data-ttu-id="5ecb6-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="5ecb6-656">IS_UPDATABLE</span></span>|<span data-ttu-id="5ecb6-657">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="5ecb6-657">Boolean</span></span>|  
|<span data-ttu-id="5ecb6-658">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="5ecb6-658">DESCRIPTION</span></span>|<span data-ttu-id="5ecb6-659">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-659">String</span></span>|  
|<span data-ttu-id="5ecb6-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="5ecb6-660">DATE_CREATED</span></span>|<span data-ttu-id="5ecb6-661">DateTime</span><span class="sxs-lookup"><span data-stu-id="5ecb6-661">DateTime</span></span>|  
|<span data-ttu-id="5ecb6-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="5ecb6-662">DATE_MODIFIED</span></span>|<span data-ttu-id="5ecb6-663">DateTime</span><span class="sxs-lookup"><span data-stu-id="5ecb6-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="5ecb6-664">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="5ecb6-664">Indexes</span></span>  
  
|<span data-ttu-id="5ecb6-665">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5ecb6-665">ColumnName</span></span>|<span data-ttu-id="5ecb6-666">DataType</span><span class="sxs-lookup"><span data-stu-id="5ecb6-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5ecb6-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5ecb6-667">TABLE_CATALOG</span></span>|<span data-ttu-id="5ecb6-668">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-668">String</span></span>|  
|<span data-ttu-id="5ecb6-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5ecb6-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="5ecb6-670">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-670">String</span></span>|  
|<span data-ttu-id="5ecb6-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5ecb6-671">TABLE_NAME</span></span>|<span data-ttu-id="5ecb6-672">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-672">String</span></span>|  
|<span data-ttu-id="5ecb6-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5ecb6-673">INDEX_CATALOG</span></span>|<span data-ttu-id="5ecb6-674">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-674">String</span></span>|  
|<span data-ttu-id="5ecb6-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5ecb6-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="5ecb6-676">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-676">String</span></span>|  
|<span data-ttu-id="5ecb6-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="5ecb6-677">INDEX_NAME</span></span>|<span data-ttu-id="5ecb6-678">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-678">String</span></span>|  
|<span data-ttu-id="5ecb6-679">İŞLEM</span><span class="sxs-lookup"><span data-stu-id="5ecb6-679">PRIMARY_KEY</span></span>|<span data-ttu-id="5ecb6-680">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="5ecb6-680">Boolean</span></span>|  
|<span data-ttu-id="5ecb6-681">BENZERSİZ</span><span class="sxs-lookup"><span data-stu-id="5ecb6-681">UNIQUE</span></span>|<span data-ttu-id="5ecb6-682">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="5ecb6-682">Boolean</span></span>|  
|<span data-ttu-id="5ecb6-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="5ecb6-683">CLUSTERED</span></span>|<span data-ttu-id="5ecb6-684">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="5ecb6-684">Boolean</span></span>|  
|<span data-ttu-id="5ecb6-685">TÜRÜ</span><span class="sxs-lookup"><span data-stu-id="5ecb6-685">TYPE</span></span>|<span data-ttu-id="5ecb6-686">Int32</span><span class="sxs-lookup"><span data-stu-id="5ecb6-686">Int32</span></span>|  
|<span data-ttu-id="5ecb6-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="5ecb6-687">FILL_FACTOR</span></span>|<span data-ttu-id="5ecb6-688">Int32</span><span class="sxs-lookup"><span data-stu-id="5ecb6-688">Int32</span></span>|  
|<span data-ttu-id="5ecb6-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="5ecb6-689">INITIAL_SIZE</span></span>|<span data-ttu-id="5ecb6-690">Int32</span><span class="sxs-lookup"><span data-stu-id="5ecb6-690">Int32</span></span>|  
|<span data-ttu-id="5ecb6-691">NULLS</span><span class="sxs-lookup"><span data-stu-id="5ecb6-691">NULLS</span></span>|<span data-ttu-id="5ecb6-692">Int32</span><span class="sxs-lookup"><span data-stu-id="5ecb6-692">Int32</span></span>|  
|<span data-ttu-id="5ecb6-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="5ecb6-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="5ecb6-694">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="5ecb6-694">Boolean</span></span>|  
|<span data-ttu-id="5ecb6-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="5ecb6-695">AUTO_UPDATE</span></span>|<span data-ttu-id="5ecb6-696">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="5ecb6-696">Boolean</span></span>|  
|<span data-ttu-id="5ecb6-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="5ecb6-697">NULL_COLLATION</span></span>|<span data-ttu-id="5ecb6-698">Int32</span><span class="sxs-lookup"><span data-stu-id="5ecb6-698">Int32</span></span>|  
|<span data-ttu-id="5ecb6-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="5ecb6-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="5ecb6-700">Int64</span><span class="sxs-lookup"><span data-stu-id="5ecb6-700">Int64</span></span>|  
|<span data-ttu-id="5ecb6-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="5ecb6-701">COLUMN_NAME</span></span>|<span data-ttu-id="5ecb6-702">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-702">String</span></span>|  
|<span data-ttu-id="5ecb6-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="5ecb6-703">COLUMN_GUID</span></span>|<span data-ttu-id="5ecb6-704">Guid</span><span class="sxs-lookup"><span data-stu-id="5ecb6-704">Guid</span></span>|  
|<span data-ttu-id="5ecb6-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="5ecb6-705">COLUMN_PROPID</span></span>|<span data-ttu-id="5ecb6-706">Int64</span><span class="sxs-lookup"><span data-stu-id="5ecb6-706">Int64</span></span>|  
|<span data-ttu-id="5ecb6-707">HARMANLAMA</span><span class="sxs-lookup"><span data-stu-id="5ecb6-707">COLLATION</span></span>|<span data-ttu-id="5ecb6-708">Int16</span><span class="sxs-lookup"><span data-stu-id="5ecb6-708">Int16</span></span>|  
|<span data-ttu-id="5ecb6-709">ÖNEM DÜZEYİ</span><span class="sxs-lookup"><span data-stu-id="5ecb6-709">CARDINALITY</span></span>|<span data-ttu-id="5ecb6-710">Ondalık</span><span class="sxs-lookup"><span data-stu-id="5ecb6-710">Decimal</span></span>|  
|<span data-ttu-id="5ecb6-711">SAYFALARI</span><span class="sxs-lookup"><span data-stu-id="5ecb6-711">PAGES</span></span>|<span data-ttu-id="5ecb6-712">Int32</span><span class="sxs-lookup"><span data-stu-id="5ecb6-712">Int32</span></span>|  
|<span data-ttu-id="5ecb6-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="5ecb6-713">FILTER_CONDITION</span></span>|<span data-ttu-id="5ecb6-714">Dize</span><span class="sxs-lookup"><span data-stu-id="5ecb6-714">String</span></span>|  
|<span data-ttu-id="5ecb6-715">TÜMLEŞİK</span><span class="sxs-lookup"><span data-stu-id="5ecb6-715">INTEGRATED</span></span>|<span data-ttu-id="5ecb6-716">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="5ecb6-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5ecb6-717">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ecb6-717">See also</span></span>

- [<span data-ttu-id="5ecb6-718">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="5ecb6-718">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
