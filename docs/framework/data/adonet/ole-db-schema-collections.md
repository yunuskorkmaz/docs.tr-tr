---
title: OLE DB Şema Koleksiyonları
ms.date: 03/30/2017
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
ms.openlocfilehash: 6dc187b0a876d9e167a74f2381db156dde2764fe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772001"
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="3131c-102">OLE DB Şema Koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="3131c-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="3131c-103">Bu bölümde, Microsoft SQL Server, Oracle ve Microsoft Jet OLE DB sağlayıcıları için şema koleksiyonu desteğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="3131c-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="3131c-104">Microsoft SQL Server'ı OLE DB sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="3131c-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="3131c-105">Microsoft SQL Server OLE DB sürücüsü aşağıdaki özel şema koleksiyonları ortak şema koleksiyonları yanı sıra destekler:</span><span class="sxs-lookup"><span data-stu-id="3131c-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="3131c-106">Tabloları</span><span class="sxs-lookup"><span data-stu-id="3131c-106">Tables</span></span>  
  
- <span data-ttu-id="3131c-107">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="3131c-107">Columns</span></span>  
  
- <span data-ttu-id="3131c-108">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="3131c-108">Procedures</span></span>  
  
- <span data-ttu-id="3131c-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="3131c-109">ProcedureParameters</span></span>  
  
- <span data-ttu-id="3131c-110">Katalog</span><span class="sxs-lookup"><span data-stu-id="3131c-110">Catalog</span></span>  
  
- <span data-ttu-id="3131c-111">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="3131c-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="3131c-112">Tabloları</span><span class="sxs-lookup"><span data-stu-id="3131c-112">Tables</span></span>  
  
|<span data-ttu-id="3131c-113">ColumnName</span><span class="sxs-lookup"><span data-stu-id="3131c-113">ColumnName</span></span>|<span data-ttu-id="3131c-114">DataType</span><span class="sxs-lookup"><span data-stu-id="3131c-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="3131c-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3131c-115">TABLE_CATALOG</span></span>|<span data-ttu-id="3131c-116">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-116">String</span></span>|  
|<span data-ttu-id="3131c-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3131c-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="3131c-118">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-118">String</span></span>|  
|<span data-ttu-id="3131c-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="3131c-119">TABLE_NAME</span></span>|<span data-ttu-id="3131c-120">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-120">String</span></span>|  
|<span data-ttu-id="3131c-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="3131c-121">TABLE_TYPE</span></span>|<span data-ttu-id="3131c-122">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-122">String</span></span>|  
|<span data-ttu-id="3131c-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="3131c-123">TABLE_GUID</span></span>|<span data-ttu-id="3131c-124">Guid</span><span class="sxs-lookup"><span data-stu-id="3131c-124">Guid</span></span>|  
|<span data-ttu-id="3131c-125">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="3131c-125">DESCRIPTION</span></span>|<span data-ttu-id="3131c-126">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-126">String</span></span>|  
|<span data-ttu-id="3131c-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="3131c-127">TABLE_PROPID</span></span>|<span data-ttu-id="3131c-128">Int64</span><span class="sxs-lookup"><span data-stu-id="3131c-128">Int64</span></span>|  
|<span data-ttu-id="3131c-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="3131c-129">DATE_CREATED</span></span>|<span data-ttu-id="3131c-130">DateTime</span><span class="sxs-lookup"><span data-stu-id="3131c-130">DateTime</span></span>|  
|<span data-ttu-id="3131c-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="3131c-131">DATE_MODIFIED</span></span>|<span data-ttu-id="3131c-132">DateTime</span><span class="sxs-lookup"><span data-stu-id="3131c-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="3131c-133">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="3131c-133">Columns</span></span>  
  
|<span data-ttu-id="3131c-134">ColumnName</span><span class="sxs-lookup"><span data-stu-id="3131c-134">ColumnName</span></span>|<span data-ttu-id="3131c-135">DataType</span><span class="sxs-lookup"><span data-stu-id="3131c-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="3131c-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3131c-136">TABLE_CATALOG</span></span>|<span data-ttu-id="3131c-137">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-137">String</span></span>|  
|<span data-ttu-id="3131c-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3131c-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="3131c-139">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-139">String</span></span>|  
|<span data-ttu-id="3131c-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="3131c-140">TABLE_NAME</span></span>|<span data-ttu-id="3131c-141">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-141">String</span></span>|  
|<span data-ttu-id="3131c-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="3131c-142">COLUMN_NAME</span></span>|<span data-ttu-id="3131c-143">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-143">String</span></span>|  
|<span data-ttu-id="3131c-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="3131c-144">COLUMN_GUID</span></span>|<span data-ttu-id="3131c-145">Guid</span><span class="sxs-lookup"><span data-stu-id="3131c-145">Guid</span></span>|  
|<span data-ttu-id="3131c-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="3131c-146">COLUMN_PROPID</span></span>|<span data-ttu-id="3131c-147">Int64</span><span class="sxs-lookup"><span data-stu-id="3131c-147">Int64</span></span>|  
|<span data-ttu-id="3131c-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="3131c-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="3131c-149">Int64</span><span class="sxs-lookup"><span data-stu-id="3131c-149">Int64</span></span>|  
|<span data-ttu-id="3131c-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="3131c-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="3131c-151">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="3131c-151">Boolean</span></span>|  
|<span data-ttu-id="3131c-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="3131c-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="3131c-153">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-153">String</span></span>|  
|<span data-ttu-id="3131c-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="3131c-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="3131c-155">Int64</span><span class="sxs-lookup"><span data-stu-id="3131c-155">Int64</span></span>|  
|<span data-ttu-id="3131c-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="3131c-156">IS_NULLABLE</span></span>|<span data-ttu-id="3131c-157">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="3131c-157">Boolean</span></span>|  
|<span data-ttu-id="3131c-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="3131c-158">DATA_TYPE</span></span>|<span data-ttu-id="3131c-159">Int32</span><span class="sxs-lookup"><span data-stu-id="3131c-159">Int32</span></span>|  
|<span data-ttu-id="3131c-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="3131c-160">TYPE_GUID</span></span>|<span data-ttu-id="3131c-161">Guid</span><span class="sxs-lookup"><span data-stu-id="3131c-161">Guid</span></span>|  
|<span data-ttu-id="3131c-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="3131c-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="3131c-163">Int64</span><span class="sxs-lookup"><span data-stu-id="3131c-163">Int64</span></span>|  
|<span data-ttu-id="3131c-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="3131c-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="3131c-165">Int64</span><span class="sxs-lookup"><span data-stu-id="3131c-165">Int64</span></span>|  
|<span data-ttu-id="3131c-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="3131c-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="3131c-167">Int32</span><span class="sxs-lookup"><span data-stu-id="3131c-167">Int32</span></span>|  
|<span data-ttu-id="3131c-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="3131c-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="3131c-169">Int16</span><span class="sxs-lookup"><span data-stu-id="3131c-169">Int16</span></span>|  
|<span data-ttu-id="3131c-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="3131c-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="3131c-171">Int64</span><span class="sxs-lookup"><span data-stu-id="3131c-171">Int64</span></span>|  
|<span data-ttu-id="3131c-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3131c-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="3131c-173">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-173">String</span></span>|  
|<span data-ttu-id="3131c-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3131c-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="3131c-175">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-175">String</span></span>|  
|<span data-ttu-id="3131c-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="3131c-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="3131c-177">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-177">String</span></span>|  
|<span data-ttu-id="3131c-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3131c-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="3131c-179">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-179">String</span></span>|  
|<span data-ttu-id="3131c-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3131c-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="3131c-181">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-181">String</span></span>|  
|<span data-ttu-id="3131c-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="3131c-182">COLLATION_NAME</span></span>|<span data-ttu-id="3131c-183">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-183">String</span></span>|  
|<span data-ttu-id="3131c-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3131c-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="3131c-185">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-185">String</span></span>|  
|<span data-ttu-id="3131c-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3131c-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="3131c-187">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-187">String</span></span>|  
|<span data-ttu-id="3131c-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="3131c-188">DOMAIN_NAME</span></span>|<span data-ttu-id="3131c-189">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-189">String</span></span>|  
|<span data-ttu-id="3131c-190">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="3131c-190">DESCRIPTION</span></span>|<span data-ttu-id="3131c-191">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-191">String</span></span>|  
|<span data-ttu-id="3131c-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="3131c-192">COLUMN_LCID</span></span>|<span data-ttu-id="3131c-193">Int32</span><span class="sxs-lookup"><span data-stu-id="3131c-193">Int32</span></span>|  
|<span data-ttu-id="3131c-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="3131c-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="3131c-195">Int32</span><span class="sxs-lookup"><span data-stu-id="3131c-195">Int32</span></span>|  
|<span data-ttu-id="3131c-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="3131c-196">COLUMN_SORTID</span></span>|<span data-ttu-id="3131c-197">Int32</span><span class="sxs-lookup"><span data-stu-id="3131c-197">Int32</span></span>|  
|<span data-ttu-id="3131c-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="3131c-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="3131c-199">Byte[]</span><span class="sxs-lookup"><span data-stu-id="3131c-199">Byte[]</span></span>|  
|<span data-ttu-id="3131c-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="3131c-200">IS_COMPUTED</span></span>|<span data-ttu-id="3131c-201">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="3131c-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="3131c-202">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="3131c-202">Procedures</span></span>  
  
|<span data-ttu-id="3131c-203">ColumnName</span><span class="sxs-lookup"><span data-stu-id="3131c-203">ColumnName</span></span>|<span data-ttu-id="3131c-204">DataType</span><span class="sxs-lookup"><span data-stu-id="3131c-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="3131c-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3131c-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="3131c-206">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-206">String</span></span>|  
|<span data-ttu-id="3131c-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3131c-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="3131c-208">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-208">String</span></span>|  
|<span data-ttu-id="3131c-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="3131c-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="3131c-210">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-210">String</span></span>|  
|<span data-ttu-id="3131c-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="3131c-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="3131c-212">Int16</span><span class="sxs-lookup"><span data-stu-id="3131c-212">Int16</span></span>|  
|<span data-ttu-id="3131c-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="3131c-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="3131c-214">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-214">String</span></span>|  
|<span data-ttu-id="3131c-215">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="3131c-215">DESCRIPTION</span></span>|<span data-ttu-id="3131c-216">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-216">String</span></span>|  
|<span data-ttu-id="3131c-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="3131c-217">DATE_CREATED</span></span>|<span data-ttu-id="3131c-218">DateTime</span><span class="sxs-lookup"><span data-stu-id="3131c-218">DateTime</span></span>|  
|<span data-ttu-id="3131c-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="3131c-219">DATE_MODIFIED</span></span>|<span data-ttu-id="3131c-220">DateTime</span><span class="sxs-lookup"><span data-stu-id="3131c-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="3131c-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="3131c-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="3131c-222">ColumnName</span><span class="sxs-lookup"><span data-stu-id="3131c-222">ColumnName</span></span>|<span data-ttu-id="3131c-223">DataType</span><span class="sxs-lookup"><span data-stu-id="3131c-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="3131c-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3131c-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="3131c-225">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-225">String</span></span>|  
|<span data-ttu-id="3131c-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3131c-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="3131c-227">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-227">String</span></span>|  
|<span data-ttu-id="3131c-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="3131c-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="3131c-229">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-229">String</span></span>|  
|<span data-ttu-id="3131c-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="3131c-230">PARAMETER_NAME</span></span>|<span data-ttu-id="3131c-231">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-231">String</span></span>|  
|<span data-ttu-id="3131c-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="3131c-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="3131c-233">Int32</span><span class="sxs-lookup"><span data-stu-id="3131c-233">Int32</span></span>|  
|<span data-ttu-id="3131c-234">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="3131c-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="3131c-235">Int32</span><span class="sxs-lookup"><span data-stu-id="3131c-235">Int32</span></span>|  
|<span data-ttu-id="3131c-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="3131c-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="3131c-237">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="3131c-237">Boolean</span></span>|  
|<span data-ttu-id="3131c-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="3131c-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="3131c-239">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-239">String</span></span>|  
|<span data-ttu-id="3131c-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="3131c-240">IS_NULLABLE</span></span>|<span data-ttu-id="3131c-241">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="3131c-241">Boolean</span></span>|  
|<span data-ttu-id="3131c-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="3131c-242">DATA_TYPE</span></span>|<span data-ttu-id="3131c-243">Int32</span><span class="sxs-lookup"><span data-stu-id="3131c-243">Int32</span></span>|  
|<span data-ttu-id="3131c-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="3131c-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="3131c-245">Int64</span><span class="sxs-lookup"><span data-stu-id="3131c-245">Int64</span></span>|  
|<span data-ttu-id="3131c-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="3131c-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="3131c-247">Int64</span><span class="sxs-lookup"><span data-stu-id="3131c-247">Int64</span></span>|  
|<span data-ttu-id="3131c-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="3131c-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="3131c-249">Int32</span><span class="sxs-lookup"><span data-stu-id="3131c-249">Int32</span></span>|  
|<span data-ttu-id="3131c-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="3131c-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="3131c-251">Int16</span><span class="sxs-lookup"><span data-stu-id="3131c-251">Int16</span></span>|  
|<span data-ttu-id="3131c-252">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="3131c-252">DESCRIPTION</span></span>|<span data-ttu-id="3131c-253">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-253">String</span></span>|  
|<span data-ttu-id="3131c-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="3131c-254">TYPE_NAME</span></span>|<span data-ttu-id="3131c-255">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-255">String</span></span>|  
|<span data-ttu-id="3131c-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="3131c-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="3131c-257">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="3131c-258">Katalog</span><span class="sxs-lookup"><span data-stu-id="3131c-258">Catalog</span></span>  
  
|<span data-ttu-id="3131c-259">ColumnName</span><span class="sxs-lookup"><span data-stu-id="3131c-259">ColumnName</span></span>|<span data-ttu-id="3131c-260">DataType</span><span class="sxs-lookup"><span data-stu-id="3131c-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="3131c-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="3131c-261">CATALOG_NAME</span></span>|<span data-ttu-id="3131c-262">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-262">String</span></span>|  
|<span data-ttu-id="3131c-263">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="3131c-263">DESCRIPTION</span></span>|<span data-ttu-id="3131c-264">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="3131c-265">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="3131c-265">Indexes</span></span>  
  
|<span data-ttu-id="3131c-266">ColumnName</span><span class="sxs-lookup"><span data-stu-id="3131c-266">ColumnName</span></span>|<span data-ttu-id="3131c-267">DataType</span><span class="sxs-lookup"><span data-stu-id="3131c-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="3131c-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3131c-268">TABLE_CATALOG</span></span>|<span data-ttu-id="3131c-269">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-269">String</span></span>|  
|<span data-ttu-id="3131c-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3131c-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="3131c-271">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-271">String</span></span>|  
|<span data-ttu-id="3131c-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="3131c-272">TABLE_NAME</span></span>|<span data-ttu-id="3131c-273">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-273">String</span></span>|  
|<span data-ttu-id="3131c-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3131c-274">INDEX_CATALOG</span></span>|<span data-ttu-id="3131c-275">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-275">String</span></span>|  
|<span data-ttu-id="3131c-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3131c-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="3131c-277">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-277">String</span></span>|  
|<span data-ttu-id="3131c-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="3131c-278">INDEX_NAME</span></span>|<span data-ttu-id="3131c-279">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-279">String</span></span>|  
|<span data-ttu-id="3131c-280">İŞLEM</span><span class="sxs-lookup"><span data-stu-id="3131c-280">PRIMARY_KEY</span></span>|<span data-ttu-id="3131c-281">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="3131c-281">Boolean</span></span>|  
|<span data-ttu-id="3131c-282">BENZERSİZ</span><span class="sxs-lookup"><span data-stu-id="3131c-282">UNIQUE</span></span>|<span data-ttu-id="3131c-283">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="3131c-283">Boolean</span></span>|  
|<span data-ttu-id="3131c-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="3131c-284">CLUSTERED</span></span>|<span data-ttu-id="3131c-285">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="3131c-285">Boolean</span></span>|  
|<span data-ttu-id="3131c-286">TÜRÜ</span><span class="sxs-lookup"><span data-stu-id="3131c-286">TYPE</span></span>|<span data-ttu-id="3131c-287">Int32</span><span class="sxs-lookup"><span data-stu-id="3131c-287">Int32</span></span>|  
|<span data-ttu-id="3131c-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="3131c-288">FILL_FACTOR</span></span>|<span data-ttu-id="3131c-289">Int32</span><span class="sxs-lookup"><span data-stu-id="3131c-289">Int32</span></span>|  
|<span data-ttu-id="3131c-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="3131c-290">INITIAL_SIZE</span></span>|<span data-ttu-id="3131c-291">Int32</span><span class="sxs-lookup"><span data-stu-id="3131c-291">Int32</span></span>|  
|<span data-ttu-id="3131c-292">NULLS</span><span class="sxs-lookup"><span data-stu-id="3131c-292">NULLS</span></span>|<span data-ttu-id="3131c-293">Int32</span><span class="sxs-lookup"><span data-stu-id="3131c-293">Int32</span></span>|  
|<span data-ttu-id="3131c-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="3131c-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="3131c-295">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="3131c-295">Boolean</span></span>|  
|<span data-ttu-id="3131c-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="3131c-296">AUTO_UPDATE</span></span>|<span data-ttu-id="3131c-297">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="3131c-297">Boolean</span></span>|  
|<span data-ttu-id="3131c-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="3131c-298">NULL_COLLATION</span></span>|<span data-ttu-id="3131c-299">Int32</span><span class="sxs-lookup"><span data-stu-id="3131c-299">Int32</span></span>|  
|<span data-ttu-id="3131c-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="3131c-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="3131c-301">Int64</span><span class="sxs-lookup"><span data-stu-id="3131c-301">Int64</span></span>|  
|<span data-ttu-id="3131c-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="3131c-302">COLUMN_NAME</span></span>|<span data-ttu-id="3131c-303">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-303">String</span></span>|  
|<span data-ttu-id="3131c-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="3131c-304">COLUMN_GUID</span></span>|<span data-ttu-id="3131c-305">Guid</span><span class="sxs-lookup"><span data-stu-id="3131c-305">Guid</span></span>|  
|<span data-ttu-id="3131c-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="3131c-306">COLUMN_PROPID</span></span>|<span data-ttu-id="3131c-307">Int64</span><span class="sxs-lookup"><span data-stu-id="3131c-307">Int64</span></span>|  
|<span data-ttu-id="3131c-308">HARMANLAMA</span><span class="sxs-lookup"><span data-stu-id="3131c-308">COLLATION</span></span>|<span data-ttu-id="3131c-309">Int16</span><span class="sxs-lookup"><span data-stu-id="3131c-309">Int16</span></span>|  
|<span data-ttu-id="3131c-310">ÖNEM DÜZEYİ</span><span class="sxs-lookup"><span data-stu-id="3131c-310">CARDINALITY</span></span>|<span data-ttu-id="3131c-311">Ondalık</span><span class="sxs-lookup"><span data-stu-id="3131c-311">Decimal</span></span>|  
|<span data-ttu-id="3131c-312">SAYFALARI</span><span class="sxs-lookup"><span data-stu-id="3131c-312">PAGES</span></span>|<span data-ttu-id="3131c-313">Int32</span><span class="sxs-lookup"><span data-stu-id="3131c-313">Int32</span></span>|  
|<span data-ttu-id="3131c-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="3131c-314">FILTER_CONDITION</span></span>|<span data-ttu-id="3131c-315">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-315">String</span></span>|  
|<span data-ttu-id="3131c-316">TÜMLEŞİK</span><span class="sxs-lookup"><span data-stu-id="3131c-316">INTEGRATED</span></span>|<span data-ttu-id="3131c-317">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="3131c-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="3131c-318">Microsoft Oracle OLE DB sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="3131c-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="3131c-319">Microsoft Oracle OLE DB sürücüsü aşağıdaki özel şema koleksiyonları ortak şema koleksiyonları yanı sıra destekler:</span><span class="sxs-lookup"><span data-stu-id="3131c-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="3131c-320">Tabloları</span><span class="sxs-lookup"><span data-stu-id="3131c-320">Tables</span></span>  
  
- <span data-ttu-id="3131c-321">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="3131c-321">Columns</span></span>  
  
- <span data-ttu-id="3131c-322">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="3131c-322">Procedures</span></span>  
  
- <span data-ttu-id="3131c-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="3131c-323">ProcedureColumns</span></span>  
  
- <span data-ttu-id="3131c-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="3131c-324">ProcedureParameters</span></span>  
  
- <span data-ttu-id="3131c-325">Görünümler</span><span class="sxs-lookup"><span data-stu-id="3131c-325">Views</span></span>  
  
- <span data-ttu-id="3131c-326">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="3131c-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="3131c-327">Tabloları</span><span class="sxs-lookup"><span data-stu-id="3131c-327">Tables</span></span>  
  
|<span data-ttu-id="3131c-328">ColumnName</span><span class="sxs-lookup"><span data-stu-id="3131c-328">ColumnName</span></span>|<span data-ttu-id="3131c-329">DataType</span><span class="sxs-lookup"><span data-stu-id="3131c-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="3131c-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3131c-330">TABLE_CATALOG</span></span>|<span data-ttu-id="3131c-331">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-331">String</span></span>|  
|<span data-ttu-id="3131c-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3131c-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="3131c-333">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-333">String</span></span>|  
|<span data-ttu-id="3131c-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="3131c-334">TABLE_NAME</span></span>|<span data-ttu-id="3131c-335">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-335">String</span></span>|  
|<span data-ttu-id="3131c-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="3131c-336">TABLE_TYPE</span></span>|<span data-ttu-id="3131c-337">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-337">String</span></span>|  
|<span data-ttu-id="3131c-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="3131c-338">TABLE_GUID</span></span>|<span data-ttu-id="3131c-339">Guid</span><span class="sxs-lookup"><span data-stu-id="3131c-339">Guid</span></span>|  
|<span data-ttu-id="3131c-340">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="3131c-340">DESCRIPTION</span></span>|<span data-ttu-id="3131c-341">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-341">String</span></span>|  
|<span data-ttu-id="3131c-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="3131c-342">TABLE_PROPID</span></span>|<span data-ttu-id="3131c-343">Int64</span><span class="sxs-lookup"><span data-stu-id="3131c-343">Int64</span></span>|  
|<span data-ttu-id="3131c-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="3131c-344">DATE_CREATED</span></span>|<span data-ttu-id="3131c-345">DateTime</span><span class="sxs-lookup"><span data-stu-id="3131c-345">DateTime</span></span>|  
|<span data-ttu-id="3131c-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="3131c-346">DATE_MODIFIED</span></span>|<span data-ttu-id="3131c-347">DateTime</span><span class="sxs-lookup"><span data-stu-id="3131c-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="3131c-348">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="3131c-348">Columns</span></span>  
  
|<span data-ttu-id="3131c-349">ColumnName</span><span class="sxs-lookup"><span data-stu-id="3131c-349">ColumnName</span></span>|<span data-ttu-id="3131c-350">DataType</span><span class="sxs-lookup"><span data-stu-id="3131c-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="3131c-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3131c-351">TABLE_CATALOG</span></span>|<span data-ttu-id="3131c-352">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-352">String</span></span>|  
|<span data-ttu-id="3131c-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3131c-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="3131c-354">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-354">String</span></span>|  
|<span data-ttu-id="3131c-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="3131c-355">TABLE_NAME</span></span>|<span data-ttu-id="3131c-356">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-356">String</span></span>|  
|<span data-ttu-id="3131c-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="3131c-357">COLUMN_NAME</span></span>|<span data-ttu-id="3131c-358">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-358">String</span></span>|  
|<span data-ttu-id="3131c-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="3131c-359">COLUMN_GUID</span></span>|<span data-ttu-id="3131c-360">Guid</span><span class="sxs-lookup"><span data-stu-id="3131c-360">Guid</span></span>|  
|<span data-ttu-id="3131c-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="3131c-361">COLUMN_PROPID</span></span>|<span data-ttu-id="3131c-362">Int64</span><span class="sxs-lookup"><span data-stu-id="3131c-362">Int64</span></span>|  
|<span data-ttu-id="3131c-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="3131c-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="3131c-364">Int64</span><span class="sxs-lookup"><span data-stu-id="3131c-364">Int64</span></span>|  
|<span data-ttu-id="3131c-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="3131c-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="3131c-366">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="3131c-366">Boolean</span></span>|  
|<span data-ttu-id="3131c-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="3131c-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="3131c-368">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-368">String</span></span>|  
|<span data-ttu-id="3131c-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="3131c-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="3131c-370">Int64</span><span class="sxs-lookup"><span data-stu-id="3131c-370">Int64</span></span>|  
|<span data-ttu-id="3131c-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="3131c-371">IS_NULLABLE</span></span>|<span data-ttu-id="3131c-372">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="3131c-372">Boolean</span></span>|  
|<span data-ttu-id="3131c-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="3131c-373">DATA_TYPE</span></span>|<span data-ttu-id="3131c-374">Int32</span><span class="sxs-lookup"><span data-stu-id="3131c-374">Int32</span></span>|  
|<span data-ttu-id="3131c-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="3131c-375">TYPE_GUID</span></span>|<span data-ttu-id="3131c-376">Guid</span><span class="sxs-lookup"><span data-stu-id="3131c-376">Guid</span></span>|  
|<span data-ttu-id="3131c-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="3131c-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="3131c-378">Int64</span><span class="sxs-lookup"><span data-stu-id="3131c-378">Int64</span></span>|  
|<span data-ttu-id="3131c-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="3131c-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="3131c-380">Int64</span><span class="sxs-lookup"><span data-stu-id="3131c-380">Int64</span></span>|  
|<span data-ttu-id="3131c-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="3131c-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="3131c-382">Int32</span><span class="sxs-lookup"><span data-stu-id="3131c-382">Int32</span></span>|  
|<span data-ttu-id="3131c-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="3131c-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="3131c-384">Int16</span><span class="sxs-lookup"><span data-stu-id="3131c-384">Int16</span></span>|  
|<span data-ttu-id="3131c-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="3131c-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="3131c-386">Int64</span><span class="sxs-lookup"><span data-stu-id="3131c-386">Int64</span></span>|  
|<span data-ttu-id="3131c-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3131c-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="3131c-388">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-388">String</span></span>|  
|<span data-ttu-id="3131c-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3131c-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="3131c-390">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-390">String</span></span>|  
|<span data-ttu-id="3131c-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="3131c-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="3131c-392">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-392">String</span></span>|  
|<span data-ttu-id="3131c-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3131c-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="3131c-394">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-394">String</span></span>|  
|<span data-ttu-id="3131c-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3131c-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="3131c-396">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-396">String</span></span>|  
|<span data-ttu-id="3131c-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="3131c-397">COLLATION_NAME</span></span>|<span data-ttu-id="3131c-398">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-398">String</span></span>|  
|<span data-ttu-id="3131c-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3131c-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="3131c-400">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-400">String</span></span>|  
|<span data-ttu-id="3131c-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3131c-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="3131c-402">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-402">String</span></span>|  
|<span data-ttu-id="3131c-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="3131c-403">DOMAIN_NAME</span></span>|<span data-ttu-id="3131c-404">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-404">String</span></span>|  
|<span data-ttu-id="3131c-405">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="3131c-405">DESCRIPTION</span></span>|<span data-ttu-id="3131c-406">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="3131c-407">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="3131c-407">Procedures</span></span>  
  
|<span data-ttu-id="3131c-408">ColumnName</span><span class="sxs-lookup"><span data-stu-id="3131c-408">ColumnName</span></span>|<span data-ttu-id="3131c-409">DataType</span><span class="sxs-lookup"><span data-stu-id="3131c-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="3131c-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3131c-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="3131c-411">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-411">String</span></span>|  
|<span data-ttu-id="3131c-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3131c-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="3131c-413">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-413">String</span></span>|  
|<span data-ttu-id="3131c-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="3131c-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="3131c-415">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-415">String</span></span>|  
|<span data-ttu-id="3131c-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="3131c-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="3131c-417">Int16</span><span class="sxs-lookup"><span data-stu-id="3131c-417">Int16</span></span>|  
|<span data-ttu-id="3131c-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="3131c-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="3131c-419">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-419">String</span></span>|  
|<span data-ttu-id="3131c-420">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="3131c-420">DESCRIPTION</span></span>|<span data-ttu-id="3131c-421">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-421">String</span></span>|  
|<span data-ttu-id="3131c-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="3131c-422">DATE_CREATED</span></span>|<span data-ttu-id="3131c-423">DateTime</span><span class="sxs-lookup"><span data-stu-id="3131c-423">DateTime</span></span>|  
|<span data-ttu-id="3131c-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="3131c-424">DATE_MODIFIED</span></span>|<span data-ttu-id="3131c-425">DateTime</span><span class="sxs-lookup"><span data-stu-id="3131c-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="3131c-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="3131c-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="3131c-427">ColumnName</span><span class="sxs-lookup"><span data-stu-id="3131c-427">ColumnName</span></span>|<span data-ttu-id="3131c-428">DataType</span><span class="sxs-lookup"><span data-stu-id="3131c-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="3131c-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3131c-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="3131c-430">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-430">String</span></span>|  
|<span data-ttu-id="3131c-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3131c-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="3131c-432">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-432">String</span></span>|  
|<span data-ttu-id="3131c-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="3131c-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="3131c-434">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-434">String</span></span>|  
|<span data-ttu-id="3131c-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="3131c-435">COLUMN_NAME</span></span>|<span data-ttu-id="3131c-436">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-436">String</span></span>|  
|<span data-ttu-id="3131c-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="3131c-437">COLUMN_GUID</span></span>|<span data-ttu-id="3131c-438">Guid</span><span class="sxs-lookup"><span data-stu-id="3131c-438">Guid</span></span>|  
|<span data-ttu-id="3131c-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="3131c-439">COLUMN_PROPID</span></span>|<span data-ttu-id="3131c-440">Int64</span><span class="sxs-lookup"><span data-stu-id="3131c-440">Int64</span></span>|  
|<span data-ttu-id="3131c-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="3131c-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="3131c-442">Int64</span><span class="sxs-lookup"><span data-stu-id="3131c-442">Int64</span></span>|  
|<span data-ttu-id="3131c-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="3131c-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="3131c-444">Int64</span><span class="sxs-lookup"><span data-stu-id="3131c-444">Int64</span></span>|  
|<span data-ttu-id="3131c-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="3131c-445">IS_NULLABLE</span></span>|<span data-ttu-id="3131c-446">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="3131c-446">Boolean</span></span>|  
|<span data-ttu-id="3131c-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="3131c-447">DATA_TYPE</span></span>|<span data-ttu-id="3131c-448">Int32</span><span class="sxs-lookup"><span data-stu-id="3131c-448">Int32</span></span>|  
|<span data-ttu-id="3131c-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="3131c-449">TYPE_GUID</span></span>|<span data-ttu-id="3131c-450">Guid</span><span class="sxs-lookup"><span data-stu-id="3131c-450">Guid</span></span>|  
|<span data-ttu-id="3131c-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="3131c-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="3131c-452">Int64</span><span class="sxs-lookup"><span data-stu-id="3131c-452">Int64</span></span>|  
|<span data-ttu-id="3131c-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="3131c-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="3131c-454">Int64</span><span class="sxs-lookup"><span data-stu-id="3131c-454">Int64</span></span>|  
|<span data-ttu-id="3131c-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="3131c-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="3131c-456">Int32</span><span class="sxs-lookup"><span data-stu-id="3131c-456">Int32</span></span>|  
|<span data-ttu-id="3131c-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="3131c-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="3131c-458">Int16</span><span class="sxs-lookup"><span data-stu-id="3131c-458">Int16</span></span>|  
|<span data-ttu-id="3131c-459">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="3131c-459">DESCRIPTION</span></span>|<span data-ttu-id="3131c-460">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-460">String</span></span>|  
|<span data-ttu-id="3131c-461">AŞIRI YÜKLEME</span><span class="sxs-lookup"><span data-stu-id="3131c-461">OVERLOAD</span></span>|<span data-ttu-id="3131c-462">Int16</span><span class="sxs-lookup"><span data-stu-id="3131c-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="3131c-463">Görünümler</span><span class="sxs-lookup"><span data-stu-id="3131c-463">Views</span></span>  
  
|<span data-ttu-id="3131c-464">ColumnName</span><span class="sxs-lookup"><span data-stu-id="3131c-464">ColumnName</span></span>|<span data-ttu-id="3131c-465">DataType</span><span class="sxs-lookup"><span data-stu-id="3131c-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="3131c-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3131c-466">TABLE_CATALOG</span></span>|<span data-ttu-id="3131c-467">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-467">String</span></span>|  
|<span data-ttu-id="3131c-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3131c-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="3131c-469">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-469">String</span></span>|  
|<span data-ttu-id="3131c-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="3131c-470">TABLE_NAME</span></span>|<span data-ttu-id="3131c-471">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-471">String</span></span>|  
|<span data-ttu-id="3131c-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="3131c-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="3131c-473">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-473">String</span></span>|  
|<span data-ttu-id="3131c-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="3131c-474">CHECK_OPTION</span></span>|<span data-ttu-id="3131c-475">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="3131c-475">Boolean</span></span>|  
|<span data-ttu-id="3131c-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="3131c-476">IS_UPDATABLE</span></span>|<span data-ttu-id="3131c-477">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="3131c-477">Boolean</span></span>|  
|<span data-ttu-id="3131c-478">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="3131c-478">DESCRIPTION</span></span>|<span data-ttu-id="3131c-479">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-479">String</span></span>|  
|<span data-ttu-id="3131c-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="3131c-480">DATE_CREATED</span></span>|<span data-ttu-id="3131c-481">DateTime</span><span class="sxs-lookup"><span data-stu-id="3131c-481">DateTime</span></span>|  
|<span data-ttu-id="3131c-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="3131c-482">DATE_MODIFIED</span></span>|<span data-ttu-id="3131c-483">DateTime</span><span class="sxs-lookup"><span data-stu-id="3131c-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="3131c-484">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="3131c-484">Indexes</span></span>  
  
|<span data-ttu-id="3131c-485">ColumnName</span><span class="sxs-lookup"><span data-stu-id="3131c-485">ColumnName</span></span>|<span data-ttu-id="3131c-486">DataType</span><span class="sxs-lookup"><span data-stu-id="3131c-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="3131c-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3131c-487">TABLE_CATALOG</span></span>|<span data-ttu-id="3131c-488">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-488">String</span></span>|  
|<span data-ttu-id="3131c-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3131c-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="3131c-490">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-490">String</span></span>|  
|<span data-ttu-id="3131c-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="3131c-491">TABLE_NAME</span></span>|<span data-ttu-id="3131c-492">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-492">String</span></span>|  
|<span data-ttu-id="3131c-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3131c-493">INDEX_CATALOG</span></span>|<span data-ttu-id="3131c-494">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-494">String</span></span>|  
|<span data-ttu-id="3131c-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3131c-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="3131c-496">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-496">String</span></span>|  
|<span data-ttu-id="3131c-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="3131c-497">INDEX_NAME</span></span>|<span data-ttu-id="3131c-498">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-498">String</span></span>|  
|<span data-ttu-id="3131c-499">İŞLEM</span><span class="sxs-lookup"><span data-stu-id="3131c-499">PRIMARY_KEY</span></span>|<span data-ttu-id="3131c-500">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="3131c-500">Boolean</span></span>|  
|<span data-ttu-id="3131c-501">BENZERSİZ</span><span class="sxs-lookup"><span data-stu-id="3131c-501">UNIQUE</span></span>|<span data-ttu-id="3131c-502">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="3131c-502">Boolean</span></span>|  
|<span data-ttu-id="3131c-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="3131c-503">CLUSTERED</span></span>|<span data-ttu-id="3131c-504">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="3131c-504">Boolean</span></span>|  
|<span data-ttu-id="3131c-505">TÜRÜ</span><span class="sxs-lookup"><span data-stu-id="3131c-505">TYPE</span></span>|<span data-ttu-id="3131c-506">Int32</span><span class="sxs-lookup"><span data-stu-id="3131c-506">Int32</span></span>|  
|<span data-ttu-id="3131c-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="3131c-507">FILL_FACTOR</span></span>|<span data-ttu-id="3131c-508">Int32</span><span class="sxs-lookup"><span data-stu-id="3131c-508">Int32</span></span>|  
|<span data-ttu-id="3131c-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="3131c-509">INITIAL_SIZE</span></span>|<span data-ttu-id="3131c-510">Int32</span><span class="sxs-lookup"><span data-stu-id="3131c-510">Int32</span></span>|  
|<span data-ttu-id="3131c-511">NULLS</span><span class="sxs-lookup"><span data-stu-id="3131c-511">NULLS</span></span>|<span data-ttu-id="3131c-512">Int32</span><span class="sxs-lookup"><span data-stu-id="3131c-512">Int32</span></span>|  
|<span data-ttu-id="3131c-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="3131c-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="3131c-514">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="3131c-514">Boolean</span></span>|  
|<span data-ttu-id="3131c-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="3131c-515">AUTO_UPDATE</span></span>|<span data-ttu-id="3131c-516">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="3131c-516">Boolean</span></span>|  
|<span data-ttu-id="3131c-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="3131c-517">NULL_COLLATION</span></span>|<span data-ttu-id="3131c-518">Int32</span><span class="sxs-lookup"><span data-stu-id="3131c-518">Int32</span></span>|  
|<span data-ttu-id="3131c-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="3131c-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="3131c-520">Int64</span><span class="sxs-lookup"><span data-stu-id="3131c-520">Int64</span></span>|  
|<span data-ttu-id="3131c-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="3131c-521">COLUMN_NAME</span></span>|<span data-ttu-id="3131c-522">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-522">String</span></span>|  
|<span data-ttu-id="3131c-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="3131c-523">COLUMN_GUID</span></span>|<span data-ttu-id="3131c-524">Guid</span><span class="sxs-lookup"><span data-stu-id="3131c-524">Guid</span></span>|  
|<span data-ttu-id="3131c-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="3131c-525">COLUMN_PROPID</span></span>|<span data-ttu-id="3131c-526">Int64</span><span class="sxs-lookup"><span data-stu-id="3131c-526">Int64</span></span>|  
|<span data-ttu-id="3131c-527">HARMANLAMA</span><span class="sxs-lookup"><span data-stu-id="3131c-527">COLLATION</span></span>|<span data-ttu-id="3131c-528">Int16</span><span class="sxs-lookup"><span data-stu-id="3131c-528">Int16</span></span>|  
|<span data-ttu-id="3131c-529">ÖNEM DÜZEYİ</span><span class="sxs-lookup"><span data-stu-id="3131c-529">CARDINALITY</span></span>|<span data-ttu-id="3131c-530">Ondalık</span><span class="sxs-lookup"><span data-stu-id="3131c-530">Decimal</span></span>|  
|<span data-ttu-id="3131c-531">SAYFALARI</span><span class="sxs-lookup"><span data-stu-id="3131c-531">PAGES</span></span>|<span data-ttu-id="3131c-532">Int32</span><span class="sxs-lookup"><span data-stu-id="3131c-532">Int32</span></span>|  
|<span data-ttu-id="3131c-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="3131c-533">FILTER_CONDITION</span></span>|<span data-ttu-id="3131c-534">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-534">String</span></span>|  
|<span data-ttu-id="3131c-535">TÜMLEŞİK</span><span class="sxs-lookup"><span data-stu-id="3131c-535">INTEGRATED</span></span>|<span data-ttu-id="3131c-536">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="3131c-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="3131c-537">Microsoft Jet OLE DB sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="3131c-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="3131c-538">Microsoft Jet OLE DB sürücüsü aşağıdaki özel şema koleksiyonları ortak şema koleksiyonları yanı sıra destekler:</span><span class="sxs-lookup"><span data-stu-id="3131c-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="3131c-539">Tabloları</span><span class="sxs-lookup"><span data-stu-id="3131c-539">Tables</span></span>  
  
- <span data-ttu-id="3131c-540">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="3131c-540">Columns</span></span>  
  
- <span data-ttu-id="3131c-541">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="3131c-541">Procedures</span></span>  
  
- <span data-ttu-id="3131c-542">Görünümler</span><span class="sxs-lookup"><span data-stu-id="3131c-542">Views</span></span>  
  
- <span data-ttu-id="3131c-543">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="3131c-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="3131c-544">Tabloları</span><span class="sxs-lookup"><span data-stu-id="3131c-544">Tables</span></span>  
  
|<span data-ttu-id="3131c-545">ColumnName</span><span class="sxs-lookup"><span data-stu-id="3131c-545">ColumnName</span></span>|<span data-ttu-id="3131c-546">DataType</span><span class="sxs-lookup"><span data-stu-id="3131c-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="3131c-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3131c-547">TABLE_CATALOG</span></span>|<span data-ttu-id="3131c-548">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-548">String</span></span>|  
|<span data-ttu-id="3131c-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3131c-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="3131c-550">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-550">String</span></span>|  
|<span data-ttu-id="3131c-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="3131c-551">TABLE_NAME</span></span>|<span data-ttu-id="3131c-552">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-552">String</span></span>|  
|<span data-ttu-id="3131c-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="3131c-553">TABLE_TYPE</span></span>|<span data-ttu-id="3131c-554">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-554">String</span></span>|  
|<span data-ttu-id="3131c-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="3131c-555">TABLE_GUID</span></span>|<span data-ttu-id="3131c-556">Guid</span><span class="sxs-lookup"><span data-stu-id="3131c-556">Guid</span></span>|  
|<span data-ttu-id="3131c-557">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="3131c-557">DESCRIPTION</span></span>|<span data-ttu-id="3131c-558">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-558">String</span></span>|  
|<span data-ttu-id="3131c-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="3131c-559">TABLE_PROPID</span></span>|<span data-ttu-id="3131c-560">Int64</span><span class="sxs-lookup"><span data-stu-id="3131c-560">Int64</span></span>|  
|<span data-ttu-id="3131c-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="3131c-561">DATE_CREATED</span></span>|<span data-ttu-id="3131c-562">DateTime</span><span class="sxs-lookup"><span data-stu-id="3131c-562">DateTime</span></span>|  
|<span data-ttu-id="3131c-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="3131c-563">DATE_MODIFIED</span></span>|<span data-ttu-id="3131c-564">DateTime</span><span class="sxs-lookup"><span data-stu-id="3131c-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="3131c-565">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="3131c-565">Columns</span></span>  
  
|<span data-ttu-id="3131c-566">ColumnName</span><span class="sxs-lookup"><span data-stu-id="3131c-566">ColumnName</span></span>|<span data-ttu-id="3131c-567">DataType</span><span class="sxs-lookup"><span data-stu-id="3131c-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="3131c-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3131c-568">TABLE_CATALOG</span></span>|<span data-ttu-id="3131c-569">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-569">String</span></span>|  
|<span data-ttu-id="3131c-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3131c-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="3131c-571">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-571">String</span></span>|  
|<span data-ttu-id="3131c-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="3131c-572">TABLE_NAME</span></span>|<span data-ttu-id="3131c-573">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-573">String</span></span>|  
|<span data-ttu-id="3131c-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="3131c-574">COLUMN_NAME</span></span>|<span data-ttu-id="3131c-575">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-575">String</span></span>|  
|<span data-ttu-id="3131c-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="3131c-576">COLUMN_GUID</span></span>|<span data-ttu-id="3131c-577">Guid</span><span class="sxs-lookup"><span data-stu-id="3131c-577">Guid</span></span>|  
|<span data-ttu-id="3131c-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="3131c-578">COLUMN_PROPID</span></span>|<span data-ttu-id="3131c-579">Int64</span><span class="sxs-lookup"><span data-stu-id="3131c-579">Int64</span></span>|  
|<span data-ttu-id="3131c-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="3131c-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="3131c-581">Int64</span><span class="sxs-lookup"><span data-stu-id="3131c-581">Int64</span></span>|  
|<span data-ttu-id="3131c-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="3131c-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="3131c-583">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="3131c-583">Boolean</span></span>|  
|<span data-ttu-id="3131c-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="3131c-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="3131c-585">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-585">String</span></span>|  
|<span data-ttu-id="3131c-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="3131c-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="3131c-587">Int64</span><span class="sxs-lookup"><span data-stu-id="3131c-587">Int64</span></span>|  
|<span data-ttu-id="3131c-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="3131c-588">IS_NULLABLE</span></span>|<span data-ttu-id="3131c-589">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="3131c-589">Boolean</span></span>|  
|<span data-ttu-id="3131c-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="3131c-590">DATA_TYPE</span></span>|<span data-ttu-id="3131c-591">Int32</span><span class="sxs-lookup"><span data-stu-id="3131c-591">Int32</span></span>|  
|<span data-ttu-id="3131c-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="3131c-592">TYPE_GUID</span></span>|<span data-ttu-id="3131c-593">Guid</span><span class="sxs-lookup"><span data-stu-id="3131c-593">Guid</span></span>|  
|<span data-ttu-id="3131c-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="3131c-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="3131c-595">Int64</span><span class="sxs-lookup"><span data-stu-id="3131c-595">Int64</span></span>|  
|<span data-ttu-id="3131c-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="3131c-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="3131c-597">Int64</span><span class="sxs-lookup"><span data-stu-id="3131c-597">Int64</span></span>|  
|<span data-ttu-id="3131c-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="3131c-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="3131c-599">Int32</span><span class="sxs-lookup"><span data-stu-id="3131c-599">Int32</span></span>|  
|<span data-ttu-id="3131c-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="3131c-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="3131c-601">Int16</span><span class="sxs-lookup"><span data-stu-id="3131c-601">Int16</span></span>|  
|<span data-ttu-id="3131c-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="3131c-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="3131c-603">Int64</span><span class="sxs-lookup"><span data-stu-id="3131c-603">Int64</span></span>|  
|<span data-ttu-id="3131c-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3131c-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="3131c-605">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-605">String</span></span>|  
|<span data-ttu-id="3131c-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3131c-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="3131c-607">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-607">String</span></span>|  
|<span data-ttu-id="3131c-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="3131c-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="3131c-609">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-609">String</span></span>|  
|<span data-ttu-id="3131c-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3131c-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="3131c-611">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-611">String</span></span>|  
|<span data-ttu-id="3131c-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3131c-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="3131c-613">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-613">String</span></span>|  
|<span data-ttu-id="3131c-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="3131c-614">COLLATION_NAME</span></span>|<span data-ttu-id="3131c-615">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-615">String</span></span>|  
|<span data-ttu-id="3131c-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3131c-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="3131c-617">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-617">String</span></span>|  
|<span data-ttu-id="3131c-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3131c-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="3131c-619">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-619">String</span></span>|  
|<span data-ttu-id="3131c-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="3131c-620">DOMAIN_NAME</span></span>|<span data-ttu-id="3131c-621">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-621">String</span></span>|  
|<span data-ttu-id="3131c-622">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="3131c-622">DESCRIPTION</span></span>|<span data-ttu-id="3131c-623">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="3131c-624">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="3131c-624">Procedures</span></span>  
  
|<span data-ttu-id="3131c-625">ColumnName</span><span class="sxs-lookup"><span data-stu-id="3131c-625">ColumnName</span></span>|<span data-ttu-id="3131c-626">DataType</span><span class="sxs-lookup"><span data-stu-id="3131c-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="3131c-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3131c-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="3131c-628">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-628">String</span></span>|  
|<span data-ttu-id="3131c-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3131c-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="3131c-630">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-630">String</span></span>|  
|<span data-ttu-id="3131c-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="3131c-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="3131c-632">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-632">String</span></span>|  
|<span data-ttu-id="3131c-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="3131c-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="3131c-634">Int16</span><span class="sxs-lookup"><span data-stu-id="3131c-634">Int16</span></span>|  
|<span data-ttu-id="3131c-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="3131c-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="3131c-636">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-636">String</span></span>|  
|<span data-ttu-id="3131c-637">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="3131c-637">DESCRIPTION</span></span>|<span data-ttu-id="3131c-638">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-638">String</span></span>|  
|<span data-ttu-id="3131c-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="3131c-639">DATE_CREATED</span></span>|<span data-ttu-id="3131c-640">DateTime</span><span class="sxs-lookup"><span data-stu-id="3131c-640">DateTime</span></span>|  
|<span data-ttu-id="3131c-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="3131c-641">DATE_MODIFIED</span></span>|<span data-ttu-id="3131c-642">DateTime</span><span class="sxs-lookup"><span data-stu-id="3131c-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="3131c-643">Görünümler</span><span class="sxs-lookup"><span data-stu-id="3131c-643">Views</span></span>  
  
|<span data-ttu-id="3131c-644">ColumnName</span><span class="sxs-lookup"><span data-stu-id="3131c-644">ColumnName</span></span>|<span data-ttu-id="3131c-645">DataType</span><span class="sxs-lookup"><span data-stu-id="3131c-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="3131c-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3131c-646">TABLE_CATALOG</span></span>|<span data-ttu-id="3131c-647">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-647">String</span></span>|  
|<span data-ttu-id="3131c-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3131c-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="3131c-649">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-649">String</span></span>|  
|<span data-ttu-id="3131c-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="3131c-650">TABLE_NAME</span></span>|<span data-ttu-id="3131c-651">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-651">String</span></span>|  
|<span data-ttu-id="3131c-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="3131c-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="3131c-653">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-653">String</span></span>|  
|<span data-ttu-id="3131c-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="3131c-654">CHECK_OPTION</span></span>|<span data-ttu-id="3131c-655">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="3131c-655">Boolean</span></span>|  
|<span data-ttu-id="3131c-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="3131c-656">IS_UPDATABLE</span></span>|<span data-ttu-id="3131c-657">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="3131c-657">Boolean</span></span>|  
|<span data-ttu-id="3131c-658">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="3131c-658">DESCRIPTION</span></span>|<span data-ttu-id="3131c-659">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-659">String</span></span>|  
|<span data-ttu-id="3131c-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="3131c-660">DATE_CREATED</span></span>|<span data-ttu-id="3131c-661">DateTime</span><span class="sxs-lookup"><span data-stu-id="3131c-661">DateTime</span></span>|  
|<span data-ttu-id="3131c-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="3131c-662">DATE_MODIFIED</span></span>|<span data-ttu-id="3131c-663">DateTime</span><span class="sxs-lookup"><span data-stu-id="3131c-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="3131c-664">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="3131c-664">Indexes</span></span>  
  
|<span data-ttu-id="3131c-665">ColumnName</span><span class="sxs-lookup"><span data-stu-id="3131c-665">ColumnName</span></span>|<span data-ttu-id="3131c-666">DataType</span><span class="sxs-lookup"><span data-stu-id="3131c-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="3131c-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3131c-667">TABLE_CATALOG</span></span>|<span data-ttu-id="3131c-668">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-668">String</span></span>|  
|<span data-ttu-id="3131c-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3131c-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="3131c-670">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-670">String</span></span>|  
|<span data-ttu-id="3131c-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="3131c-671">TABLE_NAME</span></span>|<span data-ttu-id="3131c-672">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-672">String</span></span>|  
|<span data-ttu-id="3131c-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3131c-673">INDEX_CATALOG</span></span>|<span data-ttu-id="3131c-674">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-674">String</span></span>|  
|<span data-ttu-id="3131c-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3131c-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="3131c-676">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-676">String</span></span>|  
|<span data-ttu-id="3131c-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="3131c-677">INDEX_NAME</span></span>|<span data-ttu-id="3131c-678">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-678">String</span></span>|  
|<span data-ttu-id="3131c-679">İŞLEM</span><span class="sxs-lookup"><span data-stu-id="3131c-679">PRIMARY_KEY</span></span>|<span data-ttu-id="3131c-680">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="3131c-680">Boolean</span></span>|  
|<span data-ttu-id="3131c-681">BENZERSİZ</span><span class="sxs-lookup"><span data-stu-id="3131c-681">UNIQUE</span></span>|<span data-ttu-id="3131c-682">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="3131c-682">Boolean</span></span>|  
|<span data-ttu-id="3131c-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="3131c-683">CLUSTERED</span></span>|<span data-ttu-id="3131c-684">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="3131c-684">Boolean</span></span>|  
|<span data-ttu-id="3131c-685">TÜRÜ</span><span class="sxs-lookup"><span data-stu-id="3131c-685">TYPE</span></span>|<span data-ttu-id="3131c-686">Int32</span><span class="sxs-lookup"><span data-stu-id="3131c-686">Int32</span></span>|  
|<span data-ttu-id="3131c-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="3131c-687">FILL_FACTOR</span></span>|<span data-ttu-id="3131c-688">Int32</span><span class="sxs-lookup"><span data-stu-id="3131c-688">Int32</span></span>|  
|<span data-ttu-id="3131c-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="3131c-689">INITIAL_SIZE</span></span>|<span data-ttu-id="3131c-690">Int32</span><span class="sxs-lookup"><span data-stu-id="3131c-690">Int32</span></span>|  
|<span data-ttu-id="3131c-691">NULLS</span><span class="sxs-lookup"><span data-stu-id="3131c-691">NULLS</span></span>|<span data-ttu-id="3131c-692">Int32</span><span class="sxs-lookup"><span data-stu-id="3131c-692">Int32</span></span>|  
|<span data-ttu-id="3131c-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="3131c-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="3131c-694">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="3131c-694">Boolean</span></span>|  
|<span data-ttu-id="3131c-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="3131c-695">AUTO_UPDATE</span></span>|<span data-ttu-id="3131c-696">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="3131c-696">Boolean</span></span>|  
|<span data-ttu-id="3131c-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="3131c-697">NULL_COLLATION</span></span>|<span data-ttu-id="3131c-698">Int32</span><span class="sxs-lookup"><span data-stu-id="3131c-698">Int32</span></span>|  
|<span data-ttu-id="3131c-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="3131c-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="3131c-700">Int64</span><span class="sxs-lookup"><span data-stu-id="3131c-700">Int64</span></span>|  
|<span data-ttu-id="3131c-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="3131c-701">COLUMN_NAME</span></span>|<span data-ttu-id="3131c-702">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-702">String</span></span>|  
|<span data-ttu-id="3131c-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="3131c-703">COLUMN_GUID</span></span>|<span data-ttu-id="3131c-704">Guid</span><span class="sxs-lookup"><span data-stu-id="3131c-704">Guid</span></span>|  
|<span data-ttu-id="3131c-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="3131c-705">COLUMN_PROPID</span></span>|<span data-ttu-id="3131c-706">Int64</span><span class="sxs-lookup"><span data-stu-id="3131c-706">Int64</span></span>|  
|<span data-ttu-id="3131c-707">HARMANLAMA</span><span class="sxs-lookup"><span data-stu-id="3131c-707">COLLATION</span></span>|<span data-ttu-id="3131c-708">Int16</span><span class="sxs-lookup"><span data-stu-id="3131c-708">Int16</span></span>|  
|<span data-ttu-id="3131c-709">ÖNEM DÜZEYİ</span><span class="sxs-lookup"><span data-stu-id="3131c-709">CARDINALITY</span></span>|<span data-ttu-id="3131c-710">Ondalık</span><span class="sxs-lookup"><span data-stu-id="3131c-710">Decimal</span></span>|  
|<span data-ttu-id="3131c-711">SAYFALARI</span><span class="sxs-lookup"><span data-stu-id="3131c-711">PAGES</span></span>|<span data-ttu-id="3131c-712">Int32</span><span class="sxs-lookup"><span data-stu-id="3131c-712">Int32</span></span>|  
|<span data-ttu-id="3131c-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="3131c-713">FILTER_CONDITION</span></span>|<span data-ttu-id="3131c-714">Dize</span><span class="sxs-lookup"><span data-stu-id="3131c-714">String</span></span>|  
|<span data-ttu-id="3131c-715">TÜMLEŞİK</span><span class="sxs-lookup"><span data-stu-id="3131c-715">INTEGRATED</span></span>|<span data-ttu-id="3131c-716">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="3131c-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3131c-717">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3131c-717">See also</span></span>

- [<span data-ttu-id="3131c-718">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="3131c-718">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
