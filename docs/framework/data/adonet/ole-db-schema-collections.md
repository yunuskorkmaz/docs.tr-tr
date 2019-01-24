---
title: OLE DB şema koleksiyonları
ms.date: 03/30/2017
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
ms.openlocfilehash: f753f35aab0a0200da5de463a73abb9813253d11
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54658461"
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="f71b5-102">OLE DB şema koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="f71b5-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="f71b5-103">Bu bölümde, Microsoft SQL Server, Oracle ve Microsoft Jet OLE DB sağlayıcıları için şema koleksiyonu desteğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="f71b5-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="f71b5-104">Microsoft SQL Server'ı OLE DB sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="f71b5-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="f71b5-105">Microsoft SQL Server OLE DB sürücüsü aşağıdaki özel şema koleksiyonları ortak şema koleksiyonları yanı sıra destekler:</span><span class="sxs-lookup"><span data-stu-id="f71b5-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="f71b5-106">Tabloları</span><span class="sxs-lookup"><span data-stu-id="f71b5-106">Tables</span></span>  
  
-   <span data-ttu-id="f71b5-107">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="f71b5-107">Columns</span></span>  
  
-   <span data-ttu-id="f71b5-108">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="f71b5-108">Procedures</span></span>  
  
-   <span data-ttu-id="f71b5-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="f71b5-109">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="f71b5-110">Kataloğu</span><span class="sxs-lookup"><span data-stu-id="f71b5-110">Catalog</span></span>  
  
-   <span data-ttu-id="f71b5-111">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="f71b5-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="f71b5-112">Tabloları</span><span class="sxs-lookup"><span data-stu-id="f71b5-112">Tables</span></span>  
  
|<span data-ttu-id="f71b5-113">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f71b5-113">ColumnName</span></span>|<span data-ttu-id="f71b5-114">DataType</span><span class="sxs-lookup"><span data-stu-id="f71b5-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f71b5-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f71b5-115">TABLE_CATALOG</span></span>|<span data-ttu-id="f71b5-116">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-116">String</span></span>|  
|<span data-ttu-id="f71b5-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f71b5-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="f71b5-118">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-118">String</span></span>|  
|<span data-ttu-id="f71b5-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f71b5-119">TABLE_NAME</span></span>|<span data-ttu-id="f71b5-120">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-120">String</span></span>|  
|<span data-ttu-id="f71b5-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f71b5-121">TABLE_TYPE</span></span>|<span data-ttu-id="f71b5-122">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-122">String</span></span>|  
|<span data-ttu-id="f71b5-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="f71b5-123">TABLE_GUID</span></span>|<span data-ttu-id="f71b5-124">Guid</span><span class="sxs-lookup"><span data-stu-id="f71b5-124">Guid</span></span>|  
|<span data-ttu-id="f71b5-125">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="f71b5-125">DESCRIPTION</span></span>|<span data-ttu-id="f71b5-126">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-126">String</span></span>|  
|<span data-ttu-id="f71b5-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="f71b5-127">TABLE_PROPID</span></span>|<span data-ttu-id="f71b5-128">Int64</span><span class="sxs-lookup"><span data-stu-id="f71b5-128">Int64</span></span>|  
|<span data-ttu-id="f71b5-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="f71b5-129">DATE_CREATED</span></span>|<span data-ttu-id="f71b5-130">DateTime</span><span class="sxs-lookup"><span data-stu-id="f71b5-130">DateTime</span></span>|  
|<span data-ttu-id="f71b5-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="f71b5-131">DATE_MODIFIED</span></span>|<span data-ttu-id="f71b5-132">DateTime</span><span class="sxs-lookup"><span data-stu-id="f71b5-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="f71b5-133">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="f71b5-133">Columns</span></span>  
  
|<span data-ttu-id="f71b5-134">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f71b5-134">ColumnName</span></span>|<span data-ttu-id="f71b5-135">DataType</span><span class="sxs-lookup"><span data-stu-id="f71b5-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f71b5-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f71b5-136">TABLE_CATALOG</span></span>|<span data-ttu-id="f71b5-137">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-137">String</span></span>|  
|<span data-ttu-id="f71b5-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f71b5-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="f71b5-139">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-139">String</span></span>|  
|<span data-ttu-id="f71b5-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f71b5-140">TABLE_NAME</span></span>|<span data-ttu-id="f71b5-141">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-141">String</span></span>|  
|<span data-ttu-id="f71b5-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f71b5-142">COLUMN_NAME</span></span>|<span data-ttu-id="f71b5-143">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-143">String</span></span>|  
|<span data-ttu-id="f71b5-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="f71b5-144">COLUMN_GUID</span></span>|<span data-ttu-id="f71b5-145">Guid</span><span class="sxs-lookup"><span data-stu-id="f71b5-145">Guid</span></span>|  
|<span data-ttu-id="f71b5-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="f71b5-146">COLUMN_PROPID</span></span>|<span data-ttu-id="f71b5-147">Int64</span><span class="sxs-lookup"><span data-stu-id="f71b5-147">Int64</span></span>|  
|<span data-ttu-id="f71b5-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f71b5-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="f71b5-149">Int64</span><span class="sxs-lookup"><span data-stu-id="f71b5-149">Int64</span></span>|  
|<span data-ttu-id="f71b5-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="f71b5-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="f71b5-151">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="f71b5-151">Boolean</span></span>|  
|<span data-ttu-id="f71b5-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="f71b5-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="f71b5-153">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-153">String</span></span>|  
|<span data-ttu-id="f71b5-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="f71b5-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="f71b5-155">Int64</span><span class="sxs-lookup"><span data-stu-id="f71b5-155">Int64</span></span>|  
|<span data-ttu-id="f71b5-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f71b5-156">IS_NULLABLE</span></span>|<span data-ttu-id="f71b5-157">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="f71b5-157">Boolean</span></span>|  
|<span data-ttu-id="f71b5-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f71b5-158">DATA_TYPE</span></span>|<span data-ttu-id="f71b5-159">Int32</span><span class="sxs-lookup"><span data-stu-id="f71b5-159">Int32</span></span>|  
|<span data-ttu-id="f71b5-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="f71b5-160">TYPE_GUID</span></span>|<span data-ttu-id="f71b5-161">Guid</span><span class="sxs-lookup"><span data-stu-id="f71b5-161">Guid</span></span>|  
|<span data-ttu-id="f71b5-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f71b5-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="f71b5-163">Int64</span><span class="sxs-lookup"><span data-stu-id="f71b5-163">Int64</span></span>|  
|<span data-ttu-id="f71b5-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f71b5-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="f71b5-165">Int64</span><span class="sxs-lookup"><span data-stu-id="f71b5-165">Int64</span></span>|  
|<span data-ttu-id="f71b5-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="f71b5-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="f71b5-167">Int32</span><span class="sxs-lookup"><span data-stu-id="f71b5-167">Int32</span></span>|  
|<span data-ttu-id="f71b5-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="f71b5-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="f71b5-169">Int16</span><span class="sxs-lookup"><span data-stu-id="f71b5-169">Int16</span></span>|  
|<span data-ttu-id="f71b5-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="f71b5-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="f71b5-171">Int64</span><span class="sxs-lookup"><span data-stu-id="f71b5-171">Int64</span></span>|  
|<span data-ttu-id="f71b5-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f71b5-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="f71b5-173">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-173">String</span></span>|  
|<span data-ttu-id="f71b5-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f71b5-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="f71b5-175">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-175">String</span></span>|  
|<span data-ttu-id="f71b5-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="f71b5-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="f71b5-177">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-177">String</span></span>|  
|<span data-ttu-id="f71b5-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f71b5-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="f71b5-179">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-179">String</span></span>|  
|<span data-ttu-id="f71b5-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f71b5-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="f71b5-181">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-181">String</span></span>|  
|<span data-ttu-id="f71b5-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="f71b5-182">COLLATION_NAME</span></span>|<span data-ttu-id="f71b5-183">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-183">String</span></span>|  
|<span data-ttu-id="f71b5-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f71b5-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="f71b5-185">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-185">String</span></span>|  
|<span data-ttu-id="f71b5-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f71b5-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="f71b5-187">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-187">String</span></span>|  
|<span data-ttu-id="f71b5-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="f71b5-188">DOMAIN_NAME</span></span>|<span data-ttu-id="f71b5-189">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-189">String</span></span>|  
|<span data-ttu-id="f71b5-190">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="f71b5-190">DESCRIPTION</span></span>|<span data-ttu-id="f71b5-191">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-191">String</span></span>|  
|<span data-ttu-id="f71b5-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="f71b5-192">COLUMN_LCID</span></span>|<span data-ttu-id="f71b5-193">Int32</span><span class="sxs-lookup"><span data-stu-id="f71b5-193">Int32</span></span>|  
|<span data-ttu-id="f71b5-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="f71b5-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="f71b5-195">Int32</span><span class="sxs-lookup"><span data-stu-id="f71b5-195">Int32</span></span>|  
|<span data-ttu-id="f71b5-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="f71b5-196">COLUMN_SORTID</span></span>|<span data-ttu-id="f71b5-197">Int32</span><span class="sxs-lookup"><span data-stu-id="f71b5-197">Int32</span></span>|  
|<span data-ttu-id="f71b5-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="f71b5-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="f71b5-199">Bayt]</span><span class="sxs-lookup"><span data-stu-id="f71b5-199">Byte[]</span></span>|  
|<span data-ttu-id="f71b5-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="f71b5-200">IS_COMPUTED</span></span>|<span data-ttu-id="f71b5-201">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="f71b5-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="f71b5-202">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="f71b5-202">Procedures</span></span>  
  
|<span data-ttu-id="f71b5-203">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f71b5-203">ColumnName</span></span>|<span data-ttu-id="f71b5-204">DataType</span><span class="sxs-lookup"><span data-stu-id="f71b5-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f71b5-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f71b5-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="f71b5-206">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-206">String</span></span>|  
|<span data-ttu-id="f71b5-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f71b5-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="f71b5-208">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-208">String</span></span>|  
|<span data-ttu-id="f71b5-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f71b5-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="f71b5-210">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-210">String</span></span>|  
|<span data-ttu-id="f71b5-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f71b5-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="f71b5-212">Int16</span><span class="sxs-lookup"><span data-stu-id="f71b5-212">Int16</span></span>|  
|<span data-ttu-id="f71b5-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="f71b5-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="f71b5-214">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-214">String</span></span>|  
|<span data-ttu-id="f71b5-215">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="f71b5-215">DESCRIPTION</span></span>|<span data-ttu-id="f71b5-216">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-216">String</span></span>|  
|<span data-ttu-id="f71b5-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="f71b5-217">DATE_CREATED</span></span>|<span data-ttu-id="f71b5-218">DateTime</span><span class="sxs-lookup"><span data-stu-id="f71b5-218">DateTime</span></span>|  
|<span data-ttu-id="f71b5-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="f71b5-219">DATE_MODIFIED</span></span>|<span data-ttu-id="f71b5-220">DateTime</span><span class="sxs-lookup"><span data-stu-id="f71b5-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="f71b5-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="f71b5-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="f71b5-222">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f71b5-222">ColumnName</span></span>|<span data-ttu-id="f71b5-223">DataType</span><span class="sxs-lookup"><span data-stu-id="f71b5-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f71b5-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f71b5-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="f71b5-225">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-225">String</span></span>|  
|<span data-ttu-id="f71b5-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f71b5-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="f71b5-227">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-227">String</span></span>|  
|<span data-ttu-id="f71b5-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f71b5-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="f71b5-229">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-229">String</span></span>|  
|<span data-ttu-id="f71b5-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="f71b5-230">PARAMETER_NAME</span></span>|<span data-ttu-id="f71b5-231">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-231">String</span></span>|  
|<span data-ttu-id="f71b5-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f71b5-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="f71b5-233">Int32</span><span class="sxs-lookup"><span data-stu-id="f71b5-233">Int32</span></span>|  
|<span data-ttu-id="f71b5-234">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="f71b5-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="f71b5-235">Int32</span><span class="sxs-lookup"><span data-stu-id="f71b5-235">Int32</span></span>|  
|<span data-ttu-id="f71b5-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="f71b5-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="f71b5-237">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="f71b5-237">Boolean</span></span>|  
|<span data-ttu-id="f71b5-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="f71b5-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="f71b5-239">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-239">String</span></span>|  
|<span data-ttu-id="f71b5-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f71b5-240">IS_NULLABLE</span></span>|<span data-ttu-id="f71b5-241">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="f71b5-241">Boolean</span></span>|  
|<span data-ttu-id="f71b5-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f71b5-242">DATA_TYPE</span></span>|<span data-ttu-id="f71b5-243">Int32</span><span class="sxs-lookup"><span data-stu-id="f71b5-243">Int32</span></span>|  
|<span data-ttu-id="f71b5-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f71b5-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="f71b5-245">Int64</span><span class="sxs-lookup"><span data-stu-id="f71b5-245">Int64</span></span>|  
|<span data-ttu-id="f71b5-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f71b5-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="f71b5-247">Int64</span><span class="sxs-lookup"><span data-stu-id="f71b5-247">Int64</span></span>|  
|<span data-ttu-id="f71b5-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="f71b5-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="f71b5-249">Int32</span><span class="sxs-lookup"><span data-stu-id="f71b5-249">Int32</span></span>|  
|<span data-ttu-id="f71b5-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="f71b5-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="f71b5-251">Int16</span><span class="sxs-lookup"><span data-stu-id="f71b5-251">Int16</span></span>|  
|<span data-ttu-id="f71b5-252">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="f71b5-252">DESCRIPTION</span></span>|<span data-ttu-id="f71b5-253">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-253">String</span></span>|  
|<span data-ttu-id="f71b5-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="f71b5-254">TYPE_NAME</span></span>|<span data-ttu-id="f71b5-255">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-255">String</span></span>|  
|<span data-ttu-id="f71b5-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="f71b5-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="f71b5-257">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="f71b5-258">Kataloğu</span><span class="sxs-lookup"><span data-stu-id="f71b5-258">Catalog</span></span>  
  
|<span data-ttu-id="f71b5-259">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f71b5-259">ColumnName</span></span>|<span data-ttu-id="f71b5-260">DataType</span><span class="sxs-lookup"><span data-stu-id="f71b5-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f71b5-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="f71b5-261">CATALOG_NAME</span></span>|<span data-ttu-id="f71b5-262">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-262">String</span></span>|  
|<span data-ttu-id="f71b5-263">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="f71b5-263">DESCRIPTION</span></span>|<span data-ttu-id="f71b5-264">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="f71b5-265">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="f71b5-265">Indexes</span></span>  
  
|<span data-ttu-id="f71b5-266">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f71b5-266">ColumnName</span></span>|<span data-ttu-id="f71b5-267">DataType</span><span class="sxs-lookup"><span data-stu-id="f71b5-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f71b5-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f71b5-268">TABLE_CATALOG</span></span>|<span data-ttu-id="f71b5-269">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-269">String</span></span>|  
|<span data-ttu-id="f71b5-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f71b5-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="f71b5-271">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-271">String</span></span>|  
|<span data-ttu-id="f71b5-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f71b5-272">TABLE_NAME</span></span>|<span data-ttu-id="f71b5-273">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-273">String</span></span>|  
|<span data-ttu-id="f71b5-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f71b5-274">INDEX_CATALOG</span></span>|<span data-ttu-id="f71b5-275">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-275">String</span></span>|  
|<span data-ttu-id="f71b5-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f71b5-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="f71b5-277">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-277">String</span></span>|  
|<span data-ttu-id="f71b5-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="f71b5-278">INDEX_NAME</span></span>|<span data-ttu-id="f71b5-279">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-279">String</span></span>|  
|<span data-ttu-id="f71b5-280">İŞLEM</span><span class="sxs-lookup"><span data-stu-id="f71b5-280">PRIMARY_KEY</span></span>|<span data-ttu-id="f71b5-281">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="f71b5-281">Boolean</span></span>|  
|<span data-ttu-id="f71b5-282">BENZERSİZ</span><span class="sxs-lookup"><span data-stu-id="f71b5-282">UNIQUE</span></span>|<span data-ttu-id="f71b5-283">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="f71b5-283">Boolean</span></span>|  
|<span data-ttu-id="f71b5-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="f71b5-284">CLUSTERED</span></span>|<span data-ttu-id="f71b5-285">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="f71b5-285">Boolean</span></span>|  
|<span data-ttu-id="f71b5-286">TÜRÜ</span><span class="sxs-lookup"><span data-stu-id="f71b5-286">TYPE</span></span>|<span data-ttu-id="f71b5-287">Int32</span><span class="sxs-lookup"><span data-stu-id="f71b5-287">Int32</span></span>|  
|<span data-ttu-id="f71b5-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="f71b5-288">FILL_FACTOR</span></span>|<span data-ttu-id="f71b5-289">Int32</span><span class="sxs-lookup"><span data-stu-id="f71b5-289">Int32</span></span>|  
|<span data-ttu-id="f71b5-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="f71b5-290">INITIAL_SIZE</span></span>|<span data-ttu-id="f71b5-291">Int32</span><span class="sxs-lookup"><span data-stu-id="f71b5-291">Int32</span></span>|  
|<span data-ttu-id="f71b5-292">NULLS</span><span class="sxs-lookup"><span data-stu-id="f71b5-292">NULLS</span></span>|<span data-ttu-id="f71b5-293">Int32</span><span class="sxs-lookup"><span data-stu-id="f71b5-293">Int32</span></span>|  
|<span data-ttu-id="f71b5-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="f71b5-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="f71b5-295">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="f71b5-295">Boolean</span></span>|  
|<span data-ttu-id="f71b5-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="f71b5-296">AUTO_UPDATE</span></span>|<span data-ttu-id="f71b5-297">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="f71b5-297">Boolean</span></span>|  
|<span data-ttu-id="f71b5-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="f71b5-298">NULL_COLLATION</span></span>|<span data-ttu-id="f71b5-299">Int32</span><span class="sxs-lookup"><span data-stu-id="f71b5-299">Int32</span></span>|  
|<span data-ttu-id="f71b5-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f71b5-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="f71b5-301">Int64</span><span class="sxs-lookup"><span data-stu-id="f71b5-301">Int64</span></span>|  
|<span data-ttu-id="f71b5-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f71b5-302">COLUMN_NAME</span></span>|<span data-ttu-id="f71b5-303">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-303">String</span></span>|  
|<span data-ttu-id="f71b5-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="f71b5-304">COLUMN_GUID</span></span>|<span data-ttu-id="f71b5-305">Guid</span><span class="sxs-lookup"><span data-stu-id="f71b5-305">Guid</span></span>|  
|<span data-ttu-id="f71b5-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="f71b5-306">COLUMN_PROPID</span></span>|<span data-ttu-id="f71b5-307">Int64</span><span class="sxs-lookup"><span data-stu-id="f71b5-307">Int64</span></span>|  
|<span data-ttu-id="f71b5-308">HARMANLAMA</span><span class="sxs-lookup"><span data-stu-id="f71b5-308">COLLATION</span></span>|<span data-ttu-id="f71b5-309">Int16</span><span class="sxs-lookup"><span data-stu-id="f71b5-309">Int16</span></span>|  
|<span data-ttu-id="f71b5-310">ÖNEM DÜZEYİ</span><span class="sxs-lookup"><span data-stu-id="f71b5-310">CARDINALITY</span></span>|<span data-ttu-id="f71b5-311">Ondalık</span><span class="sxs-lookup"><span data-stu-id="f71b5-311">Decimal</span></span>|  
|<span data-ttu-id="f71b5-312">SAYFALARI</span><span class="sxs-lookup"><span data-stu-id="f71b5-312">PAGES</span></span>|<span data-ttu-id="f71b5-313">Int32</span><span class="sxs-lookup"><span data-stu-id="f71b5-313">Int32</span></span>|  
|<span data-ttu-id="f71b5-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="f71b5-314">FILTER_CONDITION</span></span>|<span data-ttu-id="f71b5-315">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-315">String</span></span>|  
|<span data-ttu-id="f71b5-316">TÜMLEŞİK</span><span class="sxs-lookup"><span data-stu-id="f71b5-316">INTEGRATED</span></span>|<span data-ttu-id="f71b5-317">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="f71b5-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="f71b5-318">Microsoft Oracle OLE DB sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="f71b5-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="f71b5-319">Microsoft Oracle OLE DB sürücüsü aşağıdaki özel şema koleksiyonları ortak şema koleksiyonları yanı sıra destekler:</span><span class="sxs-lookup"><span data-stu-id="f71b5-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="f71b5-320">Tabloları</span><span class="sxs-lookup"><span data-stu-id="f71b5-320">Tables</span></span>  
  
-   <span data-ttu-id="f71b5-321">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="f71b5-321">Columns</span></span>  
  
-   <span data-ttu-id="f71b5-322">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="f71b5-322">Procedures</span></span>  
  
-   <span data-ttu-id="f71b5-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="f71b5-323">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="f71b5-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="f71b5-324">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="f71b5-325">Görünümler</span><span class="sxs-lookup"><span data-stu-id="f71b5-325">Views</span></span>  
  
-   <span data-ttu-id="f71b5-326">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="f71b5-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="f71b5-327">Tabloları</span><span class="sxs-lookup"><span data-stu-id="f71b5-327">Tables</span></span>  
  
|<span data-ttu-id="f71b5-328">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f71b5-328">ColumnName</span></span>|<span data-ttu-id="f71b5-329">DataType</span><span class="sxs-lookup"><span data-stu-id="f71b5-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f71b5-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f71b5-330">TABLE_CATALOG</span></span>|<span data-ttu-id="f71b5-331">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-331">String</span></span>|  
|<span data-ttu-id="f71b5-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f71b5-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="f71b5-333">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-333">String</span></span>|  
|<span data-ttu-id="f71b5-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f71b5-334">TABLE_NAME</span></span>|<span data-ttu-id="f71b5-335">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-335">String</span></span>|  
|<span data-ttu-id="f71b5-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f71b5-336">TABLE_TYPE</span></span>|<span data-ttu-id="f71b5-337">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-337">String</span></span>|  
|<span data-ttu-id="f71b5-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="f71b5-338">TABLE_GUID</span></span>|<span data-ttu-id="f71b5-339">Guid</span><span class="sxs-lookup"><span data-stu-id="f71b5-339">Guid</span></span>|  
|<span data-ttu-id="f71b5-340">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="f71b5-340">DESCRIPTION</span></span>|<span data-ttu-id="f71b5-341">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-341">String</span></span>|  
|<span data-ttu-id="f71b5-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="f71b5-342">TABLE_PROPID</span></span>|<span data-ttu-id="f71b5-343">Int64</span><span class="sxs-lookup"><span data-stu-id="f71b5-343">Int64</span></span>|  
|<span data-ttu-id="f71b5-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="f71b5-344">DATE_CREATED</span></span>|<span data-ttu-id="f71b5-345">DateTime</span><span class="sxs-lookup"><span data-stu-id="f71b5-345">DateTime</span></span>|  
|<span data-ttu-id="f71b5-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="f71b5-346">DATE_MODIFIED</span></span>|<span data-ttu-id="f71b5-347">DateTime</span><span class="sxs-lookup"><span data-stu-id="f71b5-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="f71b5-348">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="f71b5-348">Columns</span></span>  
  
|<span data-ttu-id="f71b5-349">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f71b5-349">ColumnName</span></span>|<span data-ttu-id="f71b5-350">DataType</span><span class="sxs-lookup"><span data-stu-id="f71b5-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f71b5-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f71b5-351">TABLE_CATALOG</span></span>|<span data-ttu-id="f71b5-352">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-352">String</span></span>|  
|<span data-ttu-id="f71b5-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f71b5-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="f71b5-354">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-354">String</span></span>|  
|<span data-ttu-id="f71b5-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f71b5-355">TABLE_NAME</span></span>|<span data-ttu-id="f71b5-356">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-356">String</span></span>|  
|<span data-ttu-id="f71b5-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f71b5-357">COLUMN_NAME</span></span>|<span data-ttu-id="f71b5-358">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-358">String</span></span>|  
|<span data-ttu-id="f71b5-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="f71b5-359">COLUMN_GUID</span></span>|<span data-ttu-id="f71b5-360">Guid</span><span class="sxs-lookup"><span data-stu-id="f71b5-360">Guid</span></span>|  
|<span data-ttu-id="f71b5-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="f71b5-361">COLUMN_PROPID</span></span>|<span data-ttu-id="f71b5-362">Int64</span><span class="sxs-lookup"><span data-stu-id="f71b5-362">Int64</span></span>|  
|<span data-ttu-id="f71b5-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f71b5-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="f71b5-364">Int64</span><span class="sxs-lookup"><span data-stu-id="f71b5-364">Int64</span></span>|  
|<span data-ttu-id="f71b5-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="f71b5-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="f71b5-366">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="f71b5-366">Boolean</span></span>|  
|<span data-ttu-id="f71b5-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="f71b5-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="f71b5-368">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-368">String</span></span>|  
|<span data-ttu-id="f71b5-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="f71b5-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="f71b5-370">Int64</span><span class="sxs-lookup"><span data-stu-id="f71b5-370">Int64</span></span>|  
|<span data-ttu-id="f71b5-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f71b5-371">IS_NULLABLE</span></span>|<span data-ttu-id="f71b5-372">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="f71b5-372">Boolean</span></span>|  
|<span data-ttu-id="f71b5-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f71b5-373">DATA_TYPE</span></span>|<span data-ttu-id="f71b5-374">Int32</span><span class="sxs-lookup"><span data-stu-id="f71b5-374">Int32</span></span>|  
|<span data-ttu-id="f71b5-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="f71b5-375">TYPE_GUID</span></span>|<span data-ttu-id="f71b5-376">Guid</span><span class="sxs-lookup"><span data-stu-id="f71b5-376">Guid</span></span>|  
|<span data-ttu-id="f71b5-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f71b5-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="f71b5-378">Int64</span><span class="sxs-lookup"><span data-stu-id="f71b5-378">Int64</span></span>|  
|<span data-ttu-id="f71b5-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f71b5-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="f71b5-380">Int64</span><span class="sxs-lookup"><span data-stu-id="f71b5-380">Int64</span></span>|  
|<span data-ttu-id="f71b5-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="f71b5-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="f71b5-382">Int32</span><span class="sxs-lookup"><span data-stu-id="f71b5-382">Int32</span></span>|  
|<span data-ttu-id="f71b5-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="f71b5-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="f71b5-384">Int16</span><span class="sxs-lookup"><span data-stu-id="f71b5-384">Int16</span></span>|  
|<span data-ttu-id="f71b5-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="f71b5-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="f71b5-386">Int64</span><span class="sxs-lookup"><span data-stu-id="f71b5-386">Int64</span></span>|  
|<span data-ttu-id="f71b5-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f71b5-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="f71b5-388">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-388">String</span></span>|  
|<span data-ttu-id="f71b5-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f71b5-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="f71b5-390">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-390">String</span></span>|  
|<span data-ttu-id="f71b5-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="f71b5-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="f71b5-392">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-392">String</span></span>|  
|<span data-ttu-id="f71b5-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f71b5-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="f71b5-394">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-394">String</span></span>|  
|<span data-ttu-id="f71b5-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f71b5-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="f71b5-396">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-396">String</span></span>|  
|<span data-ttu-id="f71b5-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="f71b5-397">COLLATION_NAME</span></span>|<span data-ttu-id="f71b5-398">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-398">String</span></span>|  
|<span data-ttu-id="f71b5-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f71b5-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="f71b5-400">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-400">String</span></span>|  
|<span data-ttu-id="f71b5-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f71b5-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="f71b5-402">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-402">String</span></span>|  
|<span data-ttu-id="f71b5-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="f71b5-403">DOMAIN_NAME</span></span>|<span data-ttu-id="f71b5-404">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-404">String</span></span>|  
|<span data-ttu-id="f71b5-405">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="f71b5-405">DESCRIPTION</span></span>|<span data-ttu-id="f71b5-406">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="f71b5-407">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="f71b5-407">Procedures</span></span>  
  
|<span data-ttu-id="f71b5-408">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f71b5-408">ColumnName</span></span>|<span data-ttu-id="f71b5-409">DataType</span><span class="sxs-lookup"><span data-stu-id="f71b5-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f71b5-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f71b5-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="f71b5-411">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-411">String</span></span>|  
|<span data-ttu-id="f71b5-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f71b5-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="f71b5-413">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-413">String</span></span>|  
|<span data-ttu-id="f71b5-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f71b5-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="f71b5-415">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-415">String</span></span>|  
|<span data-ttu-id="f71b5-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f71b5-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="f71b5-417">Int16</span><span class="sxs-lookup"><span data-stu-id="f71b5-417">Int16</span></span>|  
|<span data-ttu-id="f71b5-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="f71b5-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="f71b5-419">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-419">String</span></span>|  
|<span data-ttu-id="f71b5-420">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="f71b5-420">DESCRIPTION</span></span>|<span data-ttu-id="f71b5-421">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-421">String</span></span>|  
|<span data-ttu-id="f71b5-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="f71b5-422">DATE_CREATED</span></span>|<span data-ttu-id="f71b5-423">DateTime</span><span class="sxs-lookup"><span data-stu-id="f71b5-423">DateTime</span></span>|  
|<span data-ttu-id="f71b5-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="f71b5-424">DATE_MODIFIED</span></span>|<span data-ttu-id="f71b5-425">DateTime</span><span class="sxs-lookup"><span data-stu-id="f71b5-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="f71b5-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="f71b5-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="f71b5-427">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f71b5-427">ColumnName</span></span>|<span data-ttu-id="f71b5-428">DataType</span><span class="sxs-lookup"><span data-stu-id="f71b5-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f71b5-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f71b5-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="f71b5-430">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-430">String</span></span>|  
|<span data-ttu-id="f71b5-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f71b5-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="f71b5-432">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-432">String</span></span>|  
|<span data-ttu-id="f71b5-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f71b5-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="f71b5-434">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-434">String</span></span>|  
|<span data-ttu-id="f71b5-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f71b5-435">COLUMN_NAME</span></span>|<span data-ttu-id="f71b5-436">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-436">String</span></span>|  
|<span data-ttu-id="f71b5-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="f71b5-437">COLUMN_GUID</span></span>|<span data-ttu-id="f71b5-438">Guid</span><span class="sxs-lookup"><span data-stu-id="f71b5-438">Guid</span></span>|  
|<span data-ttu-id="f71b5-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="f71b5-439">COLUMN_PROPID</span></span>|<span data-ttu-id="f71b5-440">Int64</span><span class="sxs-lookup"><span data-stu-id="f71b5-440">Int64</span></span>|  
|<span data-ttu-id="f71b5-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="f71b5-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="f71b5-442">Int64</span><span class="sxs-lookup"><span data-stu-id="f71b5-442">Int64</span></span>|  
|<span data-ttu-id="f71b5-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f71b5-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="f71b5-444">Int64</span><span class="sxs-lookup"><span data-stu-id="f71b5-444">Int64</span></span>|  
|<span data-ttu-id="f71b5-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f71b5-445">IS_NULLABLE</span></span>|<span data-ttu-id="f71b5-446">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="f71b5-446">Boolean</span></span>|  
|<span data-ttu-id="f71b5-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f71b5-447">DATA_TYPE</span></span>|<span data-ttu-id="f71b5-448">Int32</span><span class="sxs-lookup"><span data-stu-id="f71b5-448">Int32</span></span>|  
|<span data-ttu-id="f71b5-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="f71b5-449">TYPE_GUID</span></span>|<span data-ttu-id="f71b5-450">Guid</span><span class="sxs-lookup"><span data-stu-id="f71b5-450">Guid</span></span>|  
|<span data-ttu-id="f71b5-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f71b5-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="f71b5-452">Int64</span><span class="sxs-lookup"><span data-stu-id="f71b5-452">Int64</span></span>|  
|<span data-ttu-id="f71b5-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f71b5-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="f71b5-454">Int64</span><span class="sxs-lookup"><span data-stu-id="f71b5-454">Int64</span></span>|  
|<span data-ttu-id="f71b5-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="f71b5-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="f71b5-456">Int32</span><span class="sxs-lookup"><span data-stu-id="f71b5-456">Int32</span></span>|  
|<span data-ttu-id="f71b5-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="f71b5-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="f71b5-458">Int16</span><span class="sxs-lookup"><span data-stu-id="f71b5-458">Int16</span></span>|  
|<span data-ttu-id="f71b5-459">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="f71b5-459">DESCRIPTION</span></span>|<span data-ttu-id="f71b5-460">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-460">String</span></span>|  
|<span data-ttu-id="f71b5-461">AŞIRI YÜKLEME</span><span class="sxs-lookup"><span data-stu-id="f71b5-461">OVERLOAD</span></span>|<span data-ttu-id="f71b5-462">Int16</span><span class="sxs-lookup"><span data-stu-id="f71b5-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="f71b5-463">Görünümler</span><span class="sxs-lookup"><span data-stu-id="f71b5-463">Views</span></span>  
  
|<span data-ttu-id="f71b5-464">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f71b5-464">ColumnName</span></span>|<span data-ttu-id="f71b5-465">DataType</span><span class="sxs-lookup"><span data-stu-id="f71b5-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f71b5-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f71b5-466">TABLE_CATALOG</span></span>|<span data-ttu-id="f71b5-467">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-467">String</span></span>|  
|<span data-ttu-id="f71b5-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f71b5-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="f71b5-469">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-469">String</span></span>|  
|<span data-ttu-id="f71b5-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f71b5-470">TABLE_NAME</span></span>|<span data-ttu-id="f71b5-471">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-471">String</span></span>|  
|<span data-ttu-id="f71b5-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="f71b5-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="f71b5-473">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-473">String</span></span>|  
|<span data-ttu-id="f71b5-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="f71b5-474">CHECK_OPTION</span></span>|<span data-ttu-id="f71b5-475">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="f71b5-475">Boolean</span></span>|  
|<span data-ttu-id="f71b5-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="f71b5-476">IS_UPDATABLE</span></span>|<span data-ttu-id="f71b5-477">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="f71b5-477">Boolean</span></span>|  
|<span data-ttu-id="f71b5-478">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="f71b5-478">DESCRIPTION</span></span>|<span data-ttu-id="f71b5-479">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-479">String</span></span>|  
|<span data-ttu-id="f71b5-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="f71b5-480">DATE_CREATED</span></span>|<span data-ttu-id="f71b5-481">DateTime</span><span class="sxs-lookup"><span data-stu-id="f71b5-481">DateTime</span></span>|  
|<span data-ttu-id="f71b5-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="f71b5-482">DATE_MODIFIED</span></span>|<span data-ttu-id="f71b5-483">DateTime</span><span class="sxs-lookup"><span data-stu-id="f71b5-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="f71b5-484">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="f71b5-484">Indexes</span></span>  
  
|<span data-ttu-id="f71b5-485">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f71b5-485">ColumnName</span></span>|<span data-ttu-id="f71b5-486">DataType</span><span class="sxs-lookup"><span data-stu-id="f71b5-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f71b5-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f71b5-487">TABLE_CATALOG</span></span>|<span data-ttu-id="f71b5-488">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-488">String</span></span>|  
|<span data-ttu-id="f71b5-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f71b5-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="f71b5-490">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-490">String</span></span>|  
|<span data-ttu-id="f71b5-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f71b5-491">TABLE_NAME</span></span>|<span data-ttu-id="f71b5-492">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-492">String</span></span>|  
|<span data-ttu-id="f71b5-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f71b5-493">INDEX_CATALOG</span></span>|<span data-ttu-id="f71b5-494">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-494">String</span></span>|  
|<span data-ttu-id="f71b5-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f71b5-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="f71b5-496">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-496">String</span></span>|  
|<span data-ttu-id="f71b5-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="f71b5-497">INDEX_NAME</span></span>|<span data-ttu-id="f71b5-498">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-498">String</span></span>|  
|<span data-ttu-id="f71b5-499">İŞLEM</span><span class="sxs-lookup"><span data-stu-id="f71b5-499">PRIMARY_KEY</span></span>|<span data-ttu-id="f71b5-500">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="f71b5-500">Boolean</span></span>|  
|<span data-ttu-id="f71b5-501">BENZERSİZ</span><span class="sxs-lookup"><span data-stu-id="f71b5-501">UNIQUE</span></span>|<span data-ttu-id="f71b5-502">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="f71b5-502">Boolean</span></span>|  
|<span data-ttu-id="f71b5-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="f71b5-503">CLUSTERED</span></span>|<span data-ttu-id="f71b5-504">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="f71b5-504">Boolean</span></span>|  
|<span data-ttu-id="f71b5-505">TÜRÜ</span><span class="sxs-lookup"><span data-stu-id="f71b5-505">TYPE</span></span>|<span data-ttu-id="f71b5-506">Int32</span><span class="sxs-lookup"><span data-stu-id="f71b5-506">Int32</span></span>|  
|<span data-ttu-id="f71b5-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="f71b5-507">FILL_FACTOR</span></span>|<span data-ttu-id="f71b5-508">Int32</span><span class="sxs-lookup"><span data-stu-id="f71b5-508">Int32</span></span>|  
|<span data-ttu-id="f71b5-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="f71b5-509">INITIAL_SIZE</span></span>|<span data-ttu-id="f71b5-510">Int32</span><span class="sxs-lookup"><span data-stu-id="f71b5-510">Int32</span></span>|  
|<span data-ttu-id="f71b5-511">NULLS</span><span class="sxs-lookup"><span data-stu-id="f71b5-511">NULLS</span></span>|<span data-ttu-id="f71b5-512">Int32</span><span class="sxs-lookup"><span data-stu-id="f71b5-512">Int32</span></span>|  
|<span data-ttu-id="f71b5-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="f71b5-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="f71b5-514">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="f71b5-514">Boolean</span></span>|  
|<span data-ttu-id="f71b5-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="f71b5-515">AUTO_UPDATE</span></span>|<span data-ttu-id="f71b5-516">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="f71b5-516">Boolean</span></span>|  
|<span data-ttu-id="f71b5-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="f71b5-517">NULL_COLLATION</span></span>|<span data-ttu-id="f71b5-518">Int32</span><span class="sxs-lookup"><span data-stu-id="f71b5-518">Int32</span></span>|  
|<span data-ttu-id="f71b5-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f71b5-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="f71b5-520">Int64</span><span class="sxs-lookup"><span data-stu-id="f71b5-520">Int64</span></span>|  
|<span data-ttu-id="f71b5-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f71b5-521">COLUMN_NAME</span></span>|<span data-ttu-id="f71b5-522">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-522">String</span></span>|  
|<span data-ttu-id="f71b5-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="f71b5-523">COLUMN_GUID</span></span>|<span data-ttu-id="f71b5-524">Guid</span><span class="sxs-lookup"><span data-stu-id="f71b5-524">Guid</span></span>|  
|<span data-ttu-id="f71b5-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="f71b5-525">COLUMN_PROPID</span></span>|<span data-ttu-id="f71b5-526">Int64</span><span class="sxs-lookup"><span data-stu-id="f71b5-526">Int64</span></span>|  
|<span data-ttu-id="f71b5-527">HARMANLAMA</span><span class="sxs-lookup"><span data-stu-id="f71b5-527">COLLATION</span></span>|<span data-ttu-id="f71b5-528">Int16</span><span class="sxs-lookup"><span data-stu-id="f71b5-528">Int16</span></span>|  
|<span data-ttu-id="f71b5-529">ÖNEM DÜZEYİ</span><span class="sxs-lookup"><span data-stu-id="f71b5-529">CARDINALITY</span></span>|<span data-ttu-id="f71b5-530">Ondalık</span><span class="sxs-lookup"><span data-stu-id="f71b5-530">Decimal</span></span>|  
|<span data-ttu-id="f71b5-531">SAYFALARI</span><span class="sxs-lookup"><span data-stu-id="f71b5-531">PAGES</span></span>|<span data-ttu-id="f71b5-532">Int32</span><span class="sxs-lookup"><span data-stu-id="f71b5-532">Int32</span></span>|  
|<span data-ttu-id="f71b5-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="f71b5-533">FILTER_CONDITION</span></span>|<span data-ttu-id="f71b5-534">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-534">String</span></span>|  
|<span data-ttu-id="f71b5-535">TÜMLEŞİK</span><span class="sxs-lookup"><span data-stu-id="f71b5-535">INTEGRATED</span></span>|<span data-ttu-id="f71b5-536">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="f71b5-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="f71b5-537">Microsoft Jet OLE DB sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="f71b5-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="f71b5-538">Microsoft Jet OLE DB sürücüsü aşağıdaki özel şema koleksiyonları ortak şema koleksiyonları yanı sıra destekler:</span><span class="sxs-lookup"><span data-stu-id="f71b5-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="f71b5-539">Tabloları</span><span class="sxs-lookup"><span data-stu-id="f71b5-539">Tables</span></span>  
  
-   <span data-ttu-id="f71b5-540">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="f71b5-540">Columns</span></span>  
  
-   <span data-ttu-id="f71b5-541">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="f71b5-541">Procedures</span></span>  
  
-   <span data-ttu-id="f71b5-542">Görünümler</span><span class="sxs-lookup"><span data-stu-id="f71b5-542">Views</span></span>  
  
-   <span data-ttu-id="f71b5-543">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="f71b5-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="f71b5-544">Tabloları</span><span class="sxs-lookup"><span data-stu-id="f71b5-544">Tables</span></span>  
  
|<span data-ttu-id="f71b5-545">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f71b5-545">ColumnName</span></span>|<span data-ttu-id="f71b5-546">DataType</span><span class="sxs-lookup"><span data-stu-id="f71b5-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f71b5-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f71b5-547">TABLE_CATALOG</span></span>|<span data-ttu-id="f71b5-548">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-548">String</span></span>|  
|<span data-ttu-id="f71b5-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f71b5-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="f71b5-550">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-550">String</span></span>|  
|<span data-ttu-id="f71b5-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f71b5-551">TABLE_NAME</span></span>|<span data-ttu-id="f71b5-552">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-552">String</span></span>|  
|<span data-ttu-id="f71b5-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f71b5-553">TABLE_TYPE</span></span>|<span data-ttu-id="f71b5-554">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-554">String</span></span>|  
|<span data-ttu-id="f71b5-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="f71b5-555">TABLE_GUID</span></span>|<span data-ttu-id="f71b5-556">Guid</span><span class="sxs-lookup"><span data-stu-id="f71b5-556">Guid</span></span>|  
|<span data-ttu-id="f71b5-557">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="f71b5-557">DESCRIPTION</span></span>|<span data-ttu-id="f71b5-558">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-558">String</span></span>|  
|<span data-ttu-id="f71b5-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="f71b5-559">TABLE_PROPID</span></span>|<span data-ttu-id="f71b5-560">Int64</span><span class="sxs-lookup"><span data-stu-id="f71b5-560">Int64</span></span>|  
|<span data-ttu-id="f71b5-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="f71b5-561">DATE_CREATED</span></span>|<span data-ttu-id="f71b5-562">DateTime</span><span class="sxs-lookup"><span data-stu-id="f71b5-562">DateTime</span></span>|  
|<span data-ttu-id="f71b5-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="f71b5-563">DATE_MODIFIED</span></span>|<span data-ttu-id="f71b5-564">DateTime</span><span class="sxs-lookup"><span data-stu-id="f71b5-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="f71b5-565">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="f71b5-565">Columns</span></span>  
  
|<span data-ttu-id="f71b5-566">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f71b5-566">ColumnName</span></span>|<span data-ttu-id="f71b5-567">DataType</span><span class="sxs-lookup"><span data-stu-id="f71b5-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f71b5-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f71b5-568">TABLE_CATALOG</span></span>|<span data-ttu-id="f71b5-569">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-569">String</span></span>|  
|<span data-ttu-id="f71b5-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f71b5-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="f71b5-571">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-571">String</span></span>|  
|<span data-ttu-id="f71b5-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f71b5-572">TABLE_NAME</span></span>|<span data-ttu-id="f71b5-573">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-573">String</span></span>|  
|<span data-ttu-id="f71b5-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f71b5-574">COLUMN_NAME</span></span>|<span data-ttu-id="f71b5-575">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-575">String</span></span>|  
|<span data-ttu-id="f71b5-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="f71b5-576">COLUMN_GUID</span></span>|<span data-ttu-id="f71b5-577">Guid</span><span class="sxs-lookup"><span data-stu-id="f71b5-577">Guid</span></span>|  
|<span data-ttu-id="f71b5-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="f71b5-578">COLUMN_PROPID</span></span>|<span data-ttu-id="f71b5-579">Int64</span><span class="sxs-lookup"><span data-stu-id="f71b5-579">Int64</span></span>|  
|<span data-ttu-id="f71b5-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f71b5-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="f71b5-581">Int64</span><span class="sxs-lookup"><span data-stu-id="f71b5-581">Int64</span></span>|  
|<span data-ttu-id="f71b5-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="f71b5-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="f71b5-583">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="f71b5-583">Boolean</span></span>|  
|<span data-ttu-id="f71b5-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="f71b5-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="f71b5-585">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-585">String</span></span>|  
|<span data-ttu-id="f71b5-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="f71b5-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="f71b5-587">Int64</span><span class="sxs-lookup"><span data-stu-id="f71b5-587">Int64</span></span>|  
|<span data-ttu-id="f71b5-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f71b5-588">IS_NULLABLE</span></span>|<span data-ttu-id="f71b5-589">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="f71b5-589">Boolean</span></span>|  
|<span data-ttu-id="f71b5-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f71b5-590">DATA_TYPE</span></span>|<span data-ttu-id="f71b5-591">Int32</span><span class="sxs-lookup"><span data-stu-id="f71b5-591">Int32</span></span>|  
|<span data-ttu-id="f71b5-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="f71b5-592">TYPE_GUID</span></span>|<span data-ttu-id="f71b5-593">Guid</span><span class="sxs-lookup"><span data-stu-id="f71b5-593">Guid</span></span>|  
|<span data-ttu-id="f71b5-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f71b5-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="f71b5-595">Int64</span><span class="sxs-lookup"><span data-stu-id="f71b5-595">Int64</span></span>|  
|<span data-ttu-id="f71b5-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f71b5-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="f71b5-597">Int64</span><span class="sxs-lookup"><span data-stu-id="f71b5-597">Int64</span></span>|  
|<span data-ttu-id="f71b5-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="f71b5-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="f71b5-599">Int32</span><span class="sxs-lookup"><span data-stu-id="f71b5-599">Int32</span></span>|  
|<span data-ttu-id="f71b5-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="f71b5-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="f71b5-601">Int16</span><span class="sxs-lookup"><span data-stu-id="f71b5-601">Int16</span></span>|  
|<span data-ttu-id="f71b5-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="f71b5-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="f71b5-603">Int64</span><span class="sxs-lookup"><span data-stu-id="f71b5-603">Int64</span></span>|  
|<span data-ttu-id="f71b5-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f71b5-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="f71b5-605">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-605">String</span></span>|  
|<span data-ttu-id="f71b5-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f71b5-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="f71b5-607">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-607">String</span></span>|  
|<span data-ttu-id="f71b5-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="f71b5-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="f71b5-609">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-609">String</span></span>|  
|<span data-ttu-id="f71b5-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f71b5-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="f71b5-611">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-611">String</span></span>|  
|<span data-ttu-id="f71b5-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f71b5-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="f71b5-613">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-613">String</span></span>|  
|<span data-ttu-id="f71b5-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="f71b5-614">COLLATION_NAME</span></span>|<span data-ttu-id="f71b5-615">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-615">String</span></span>|  
|<span data-ttu-id="f71b5-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f71b5-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="f71b5-617">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-617">String</span></span>|  
|<span data-ttu-id="f71b5-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f71b5-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="f71b5-619">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-619">String</span></span>|  
|<span data-ttu-id="f71b5-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="f71b5-620">DOMAIN_NAME</span></span>|<span data-ttu-id="f71b5-621">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-621">String</span></span>|  
|<span data-ttu-id="f71b5-622">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="f71b5-622">DESCRIPTION</span></span>|<span data-ttu-id="f71b5-623">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="f71b5-624">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="f71b5-624">Procedures</span></span>  
  
|<span data-ttu-id="f71b5-625">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f71b5-625">ColumnName</span></span>|<span data-ttu-id="f71b5-626">DataType</span><span class="sxs-lookup"><span data-stu-id="f71b5-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f71b5-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f71b5-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="f71b5-628">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-628">String</span></span>|  
|<span data-ttu-id="f71b5-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f71b5-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="f71b5-630">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-630">String</span></span>|  
|<span data-ttu-id="f71b5-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f71b5-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="f71b5-632">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-632">String</span></span>|  
|<span data-ttu-id="f71b5-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f71b5-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="f71b5-634">Int16</span><span class="sxs-lookup"><span data-stu-id="f71b5-634">Int16</span></span>|  
|<span data-ttu-id="f71b5-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="f71b5-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="f71b5-636">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-636">String</span></span>|  
|<span data-ttu-id="f71b5-637">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="f71b5-637">DESCRIPTION</span></span>|<span data-ttu-id="f71b5-638">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-638">String</span></span>|  
|<span data-ttu-id="f71b5-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="f71b5-639">DATE_CREATED</span></span>|<span data-ttu-id="f71b5-640">DateTime</span><span class="sxs-lookup"><span data-stu-id="f71b5-640">DateTime</span></span>|  
|<span data-ttu-id="f71b5-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="f71b5-641">DATE_MODIFIED</span></span>|<span data-ttu-id="f71b5-642">DateTime</span><span class="sxs-lookup"><span data-stu-id="f71b5-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="f71b5-643">Görünümler</span><span class="sxs-lookup"><span data-stu-id="f71b5-643">Views</span></span>  
  
|<span data-ttu-id="f71b5-644">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f71b5-644">ColumnName</span></span>|<span data-ttu-id="f71b5-645">DataType</span><span class="sxs-lookup"><span data-stu-id="f71b5-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f71b5-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f71b5-646">TABLE_CATALOG</span></span>|<span data-ttu-id="f71b5-647">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-647">String</span></span>|  
|<span data-ttu-id="f71b5-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f71b5-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="f71b5-649">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-649">String</span></span>|  
|<span data-ttu-id="f71b5-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f71b5-650">TABLE_NAME</span></span>|<span data-ttu-id="f71b5-651">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-651">String</span></span>|  
|<span data-ttu-id="f71b5-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="f71b5-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="f71b5-653">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-653">String</span></span>|  
|<span data-ttu-id="f71b5-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="f71b5-654">CHECK_OPTION</span></span>|<span data-ttu-id="f71b5-655">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="f71b5-655">Boolean</span></span>|  
|<span data-ttu-id="f71b5-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="f71b5-656">IS_UPDATABLE</span></span>|<span data-ttu-id="f71b5-657">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="f71b5-657">Boolean</span></span>|  
|<span data-ttu-id="f71b5-658">AÇIKLAMASI</span><span class="sxs-lookup"><span data-stu-id="f71b5-658">DESCRIPTION</span></span>|<span data-ttu-id="f71b5-659">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-659">String</span></span>|  
|<span data-ttu-id="f71b5-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="f71b5-660">DATE_CREATED</span></span>|<span data-ttu-id="f71b5-661">DateTime</span><span class="sxs-lookup"><span data-stu-id="f71b5-661">DateTime</span></span>|  
|<span data-ttu-id="f71b5-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="f71b5-662">DATE_MODIFIED</span></span>|<span data-ttu-id="f71b5-663">DateTime</span><span class="sxs-lookup"><span data-stu-id="f71b5-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="f71b5-664">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="f71b5-664">Indexes</span></span>  
  
|<span data-ttu-id="f71b5-665">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f71b5-665">ColumnName</span></span>|<span data-ttu-id="f71b5-666">DataType</span><span class="sxs-lookup"><span data-stu-id="f71b5-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f71b5-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f71b5-667">TABLE_CATALOG</span></span>|<span data-ttu-id="f71b5-668">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-668">String</span></span>|  
|<span data-ttu-id="f71b5-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f71b5-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="f71b5-670">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-670">String</span></span>|  
|<span data-ttu-id="f71b5-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f71b5-671">TABLE_NAME</span></span>|<span data-ttu-id="f71b5-672">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-672">String</span></span>|  
|<span data-ttu-id="f71b5-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f71b5-673">INDEX_CATALOG</span></span>|<span data-ttu-id="f71b5-674">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-674">String</span></span>|  
|<span data-ttu-id="f71b5-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f71b5-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="f71b5-676">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-676">String</span></span>|  
|<span data-ttu-id="f71b5-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="f71b5-677">INDEX_NAME</span></span>|<span data-ttu-id="f71b5-678">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-678">String</span></span>|  
|<span data-ttu-id="f71b5-679">İŞLEM</span><span class="sxs-lookup"><span data-stu-id="f71b5-679">PRIMARY_KEY</span></span>|<span data-ttu-id="f71b5-680">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="f71b5-680">Boolean</span></span>|  
|<span data-ttu-id="f71b5-681">BENZERSİZ</span><span class="sxs-lookup"><span data-stu-id="f71b5-681">UNIQUE</span></span>|<span data-ttu-id="f71b5-682">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="f71b5-682">Boolean</span></span>|  
|<span data-ttu-id="f71b5-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="f71b5-683">CLUSTERED</span></span>|<span data-ttu-id="f71b5-684">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="f71b5-684">Boolean</span></span>|  
|<span data-ttu-id="f71b5-685">TÜRÜ</span><span class="sxs-lookup"><span data-stu-id="f71b5-685">TYPE</span></span>|<span data-ttu-id="f71b5-686">Int32</span><span class="sxs-lookup"><span data-stu-id="f71b5-686">Int32</span></span>|  
|<span data-ttu-id="f71b5-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="f71b5-687">FILL_FACTOR</span></span>|<span data-ttu-id="f71b5-688">Int32</span><span class="sxs-lookup"><span data-stu-id="f71b5-688">Int32</span></span>|  
|<span data-ttu-id="f71b5-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="f71b5-689">INITIAL_SIZE</span></span>|<span data-ttu-id="f71b5-690">Int32</span><span class="sxs-lookup"><span data-stu-id="f71b5-690">Int32</span></span>|  
|<span data-ttu-id="f71b5-691">NULLS</span><span class="sxs-lookup"><span data-stu-id="f71b5-691">NULLS</span></span>|<span data-ttu-id="f71b5-692">Int32</span><span class="sxs-lookup"><span data-stu-id="f71b5-692">Int32</span></span>|  
|<span data-ttu-id="f71b5-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="f71b5-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="f71b5-694">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="f71b5-694">Boolean</span></span>|  
|<span data-ttu-id="f71b5-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="f71b5-695">AUTO_UPDATE</span></span>|<span data-ttu-id="f71b5-696">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="f71b5-696">Boolean</span></span>|  
|<span data-ttu-id="f71b5-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="f71b5-697">NULL_COLLATION</span></span>|<span data-ttu-id="f71b5-698">Int32</span><span class="sxs-lookup"><span data-stu-id="f71b5-698">Int32</span></span>|  
|<span data-ttu-id="f71b5-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f71b5-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="f71b5-700">Int64</span><span class="sxs-lookup"><span data-stu-id="f71b5-700">Int64</span></span>|  
|<span data-ttu-id="f71b5-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f71b5-701">COLUMN_NAME</span></span>|<span data-ttu-id="f71b5-702">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-702">String</span></span>|  
|<span data-ttu-id="f71b5-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="f71b5-703">COLUMN_GUID</span></span>|<span data-ttu-id="f71b5-704">Guid</span><span class="sxs-lookup"><span data-stu-id="f71b5-704">Guid</span></span>|  
|<span data-ttu-id="f71b5-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="f71b5-705">COLUMN_PROPID</span></span>|<span data-ttu-id="f71b5-706">Int64</span><span class="sxs-lookup"><span data-stu-id="f71b5-706">Int64</span></span>|  
|<span data-ttu-id="f71b5-707">HARMANLAMA</span><span class="sxs-lookup"><span data-stu-id="f71b5-707">COLLATION</span></span>|<span data-ttu-id="f71b5-708">Int16</span><span class="sxs-lookup"><span data-stu-id="f71b5-708">Int16</span></span>|  
|<span data-ttu-id="f71b5-709">ÖNEM DÜZEYİ</span><span class="sxs-lookup"><span data-stu-id="f71b5-709">CARDINALITY</span></span>|<span data-ttu-id="f71b5-710">Ondalık</span><span class="sxs-lookup"><span data-stu-id="f71b5-710">Decimal</span></span>|  
|<span data-ttu-id="f71b5-711">SAYFALARI</span><span class="sxs-lookup"><span data-stu-id="f71b5-711">PAGES</span></span>|<span data-ttu-id="f71b5-712">Int32</span><span class="sxs-lookup"><span data-stu-id="f71b5-712">Int32</span></span>|  
|<span data-ttu-id="f71b5-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="f71b5-713">FILTER_CONDITION</span></span>|<span data-ttu-id="f71b5-714">Dize</span><span class="sxs-lookup"><span data-stu-id="f71b5-714">String</span></span>|  
|<span data-ttu-id="f71b5-715">TÜMLEŞİK</span><span class="sxs-lookup"><span data-stu-id="f71b5-715">INTEGRATED</span></span>|<span data-ttu-id="f71b5-716">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="f71b5-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f71b5-717">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f71b5-717">See also</span></span>
- [<span data-ttu-id="f71b5-718">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="f71b5-718">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
