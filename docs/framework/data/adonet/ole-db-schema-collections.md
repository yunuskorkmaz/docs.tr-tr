---
title: OLE DB şeması koleksiyonları
ms.date: 03/30/2017
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
ms.openlocfilehash: f1cb5e1fe967088b44fa4045dfe50c1c57d963eb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="11ac6-102">OLE DB şeması koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="11ac6-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="11ac6-103">Bu bölümde, Microsoft SQL Server, Oracle ve Microsoft Jet için OLE DB sağlayıcıları şema koleksiyonu desteği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="11ac6-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="11ac6-104">Microsoft SQL Server OLE DB sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="11ac6-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="11ac6-105">Microsoft SQL Server OLE DB sürücüsü ortak şeması koleksiyonları ek olarak aşağıdaki belirli şeması koleksiyonları destekler:</span><span class="sxs-lookup"><span data-stu-id="11ac6-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="11ac6-106">tabloları</span><span class="sxs-lookup"><span data-stu-id="11ac6-106">Tables</span></span>  
  
-   <span data-ttu-id="11ac6-107">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="11ac6-107">Columns</span></span>  
  
-   <span data-ttu-id="11ac6-108">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="11ac6-108">Procedures</span></span>  
  
-   <span data-ttu-id="11ac6-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="11ac6-109">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="11ac6-110">Katalog</span><span class="sxs-lookup"><span data-stu-id="11ac6-110">Catalog</span></span>  
  
-   <span data-ttu-id="11ac6-111">Dizinler</span><span class="sxs-lookup"><span data-stu-id="11ac6-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="11ac6-112">tabloları</span><span class="sxs-lookup"><span data-stu-id="11ac6-112">Tables</span></span>  
  
|<span data-ttu-id="11ac6-113">columnName</span><span class="sxs-lookup"><span data-stu-id="11ac6-113">ColumnName</span></span>|<span data-ttu-id="11ac6-114">Veri türü</span><span class="sxs-lookup"><span data-stu-id="11ac6-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="11ac6-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="11ac6-115">TABLE_CATALOG</span></span>|<span data-ttu-id="11ac6-116">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-116">String</span></span>|  
|<span data-ttu-id="11ac6-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="11ac6-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="11ac6-118">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-118">String</span></span>|  
|<span data-ttu-id="11ac6-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="11ac6-119">TABLE_NAME</span></span>|<span data-ttu-id="11ac6-120">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-120">String</span></span>|  
|<span data-ttu-id="11ac6-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="11ac6-121">TABLE_TYPE</span></span>|<span data-ttu-id="11ac6-122">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-122">String</span></span>|  
|<span data-ttu-id="11ac6-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="11ac6-123">TABLE_GUID</span></span>|<span data-ttu-id="11ac6-124">Guid</span><span class="sxs-lookup"><span data-stu-id="11ac6-124">Guid</span></span>|  
|<span data-ttu-id="11ac6-125">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="11ac6-125">DESCRIPTION</span></span>|<span data-ttu-id="11ac6-126">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-126">String</span></span>|  
|<span data-ttu-id="11ac6-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="11ac6-127">TABLE_PROPID</span></span>|<span data-ttu-id="11ac6-128">Int64</span><span class="sxs-lookup"><span data-stu-id="11ac6-128">Int64</span></span>|  
|<span data-ttu-id="11ac6-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="11ac6-129">DATE_CREATED</span></span>|<span data-ttu-id="11ac6-130">DateTime</span><span class="sxs-lookup"><span data-stu-id="11ac6-130">DateTime</span></span>|  
|<span data-ttu-id="11ac6-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="11ac6-131">DATE_MODIFIED</span></span>|<span data-ttu-id="11ac6-132">DateTime</span><span class="sxs-lookup"><span data-stu-id="11ac6-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="11ac6-133">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="11ac6-133">Columns</span></span>  
  
|<span data-ttu-id="11ac6-134">columnName</span><span class="sxs-lookup"><span data-stu-id="11ac6-134">ColumnName</span></span>|<span data-ttu-id="11ac6-135">Veri türü</span><span class="sxs-lookup"><span data-stu-id="11ac6-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="11ac6-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="11ac6-136">TABLE_CATALOG</span></span>|<span data-ttu-id="11ac6-137">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-137">String</span></span>|  
|<span data-ttu-id="11ac6-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="11ac6-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="11ac6-139">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-139">String</span></span>|  
|<span data-ttu-id="11ac6-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="11ac6-140">TABLE_NAME</span></span>|<span data-ttu-id="11ac6-141">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-141">String</span></span>|  
|<span data-ttu-id="11ac6-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="11ac6-142">COLUMN_NAME</span></span>|<span data-ttu-id="11ac6-143">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-143">String</span></span>|  
|<span data-ttu-id="11ac6-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="11ac6-144">COLUMN_GUID</span></span>|<span data-ttu-id="11ac6-145">Guid</span><span class="sxs-lookup"><span data-stu-id="11ac6-145">Guid</span></span>|  
|<span data-ttu-id="11ac6-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="11ac6-146">COLUMN_PROPID</span></span>|<span data-ttu-id="11ac6-147">Int64</span><span class="sxs-lookup"><span data-stu-id="11ac6-147">Int64</span></span>|  
|<span data-ttu-id="11ac6-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="11ac6-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="11ac6-149">Int64</span><span class="sxs-lookup"><span data-stu-id="11ac6-149">Int64</span></span>|  
|<span data-ttu-id="11ac6-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="11ac6-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="11ac6-151">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="11ac6-151">Boolean</span></span>|  
|<span data-ttu-id="11ac6-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="11ac6-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="11ac6-153">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-153">String</span></span>|  
|<span data-ttu-id="11ac6-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="11ac6-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="11ac6-155">Int64</span><span class="sxs-lookup"><span data-stu-id="11ac6-155">Int64</span></span>|  
|<span data-ttu-id="11ac6-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="11ac6-156">IS_NULLABLE</span></span>|<span data-ttu-id="11ac6-157">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="11ac6-157">Boolean</span></span>|  
|<span data-ttu-id="11ac6-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="11ac6-158">DATA_TYPE</span></span>|<span data-ttu-id="11ac6-159">Int32</span><span class="sxs-lookup"><span data-stu-id="11ac6-159">Int32</span></span>|  
|<span data-ttu-id="11ac6-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="11ac6-160">TYPE_GUID</span></span>|<span data-ttu-id="11ac6-161">Guid</span><span class="sxs-lookup"><span data-stu-id="11ac6-161">Guid</span></span>|  
|<span data-ttu-id="11ac6-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="11ac6-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="11ac6-163">Int64</span><span class="sxs-lookup"><span data-stu-id="11ac6-163">Int64</span></span>|  
|<span data-ttu-id="11ac6-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="11ac6-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="11ac6-165">Int64</span><span class="sxs-lookup"><span data-stu-id="11ac6-165">Int64</span></span>|  
|<span data-ttu-id="11ac6-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="11ac6-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="11ac6-167">Int32</span><span class="sxs-lookup"><span data-stu-id="11ac6-167">Int32</span></span>|  
|<span data-ttu-id="11ac6-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="11ac6-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="11ac6-169">Int16</span><span class="sxs-lookup"><span data-stu-id="11ac6-169">Int16</span></span>|  
|<span data-ttu-id="11ac6-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="11ac6-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="11ac6-171">Int64</span><span class="sxs-lookup"><span data-stu-id="11ac6-171">Int64</span></span>|  
|<span data-ttu-id="11ac6-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="11ac6-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="11ac6-173">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-173">String</span></span>|  
|<span data-ttu-id="11ac6-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="11ac6-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="11ac6-175">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-175">String</span></span>|  
|<span data-ttu-id="11ac6-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="11ac6-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="11ac6-177">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-177">String</span></span>|  
|<span data-ttu-id="11ac6-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="11ac6-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="11ac6-179">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-179">String</span></span>|  
|<span data-ttu-id="11ac6-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="11ac6-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="11ac6-181">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-181">String</span></span>|  
|<span data-ttu-id="11ac6-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="11ac6-182">COLLATION_NAME</span></span>|<span data-ttu-id="11ac6-183">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-183">String</span></span>|  
|<span data-ttu-id="11ac6-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="11ac6-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="11ac6-185">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-185">String</span></span>|  
|<span data-ttu-id="11ac6-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="11ac6-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="11ac6-187">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-187">String</span></span>|  
|<span data-ttu-id="11ac6-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="11ac6-188">DOMAIN_NAME</span></span>|<span data-ttu-id="11ac6-189">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-189">String</span></span>|  
|<span data-ttu-id="11ac6-190">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="11ac6-190">DESCRIPTION</span></span>|<span data-ttu-id="11ac6-191">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-191">String</span></span>|  
|<span data-ttu-id="11ac6-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="11ac6-192">COLUMN_LCID</span></span>|<span data-ttu-id="11ac6-193">Int32</span><span class="sxs-lookup"><span data-stu-id="11ac6-193">Int32</span></span>|  
|<span data-ttu-id="11ac6-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="11ac6-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="11ac6-195">Int32</span><span class="sxs-lookup"><span data-stu-id="11ac6-195">Int32</span></span>|  
|<span data-ttu-id="11ac6-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="11ac6-196">COLUMN_SORTID</span></span>|<span data-ttu-id="11ac6-197">Int32</span><span class="sxs-lookup"><span data-stu-id="11ac6-197">Int32</span></span>|  
|<span data-ttu-id="11ac6-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="11ac6-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="11ac6-199">Byte]</span><span class="sxs-lookup"><span data-stu-id="11ac6-199">Byte[]</span></span>|  
|<span data-ttu-id="11ac6-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="11ac6-200">IS_COMPUTED</span></span>|<span data-ttu-id="11ac6-201">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="11ac6-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="11ac6-202">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="11ac6-202">Procedures</span></span>  
  
|<span data-ttu-id="11ac6-203">columnName</span><span class="sxs-lookup"><span data-stu-id="11ac6-203">ColumnName</span></span>|<span data-ttu-id="11ac6-204">Veri türü</span><span class="sxs-lookup"><span data-stu-id="11ac6-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="11ac6-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="11ac6-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="11ac6-206">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-206">String</span></span>|  
|<span data-ttu-id="11ac6-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="11ac6-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="11ac6-208">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-208">String</span></span>|  
|<span data-ttu-id="11ac6-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="11ac6-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="11ac6-210">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-210">String</span></span>|  
|<span data-ttu-id="11ac6-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="11ac6-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="11ac6-212">Int16</span><span class="sxs-lookup"><span data-stu-id="11ac6-212">Int16</span></span>|  
|<span data-ttu-id="11ac6-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="11ac6-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="11ac6-214">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-214">String</span></span>|  
|<span data-ttu-id="11ac6-215">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="11ac6-215">DESCRIPTION</span></span>|<span data-ttu-id="11ac6-216">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-216">String</span></span>|  
|<span data-ttu-id="11ac6-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="11ac6-217">DATE_CREATED</span></span>|<span data-ttu-id="11ac6-218">DateTime</span><span class="sxs-lookup"><span data-stu-id="11ac6-218">DateTime</span></span>|  
|<span data-ttu-id="11ac6-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="11ac6-219">DATE_MODIFIED</span></span>|<span data-ttu-id="11ac6-220">DateTime</span><span class="sxs-lookup"><span data-stu-id="11ac6-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="11ac6-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="11ac6-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="11ac6-222">columnName</span><span class="sxs-lookup"><span data-stu-id="11ac6-222">ColumnName</span></span>|<span data-ttu-id="11ac6-223">Veri türü</span><span class="sxs-lookup"><span data-stu-id="11ac6-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="11ac6-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="11ac6-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="11ac6-225">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-225">String</span></span>|  
|<span data-ttu-id="11ac6-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="11ac6-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="11ac6-227">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-227">String</span></span>|  
|<span data-ttu-id="11ac6-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="11ac6-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="11ac6-229">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-229">String</span></span>|  
|<span data-ttu-id="11ac6-230">PARAMETRE_ADÝ</span><span class="sxs-lookup"><span data-stu-id="11ac6-230">PARAMETER_NAME</span></span>|<span data-ttu-id="11ac6-231">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-231">String</span></span>|  
|<span data-ttu-id="11ac6-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="11ac6-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="11ac6-233">Int32</span><span class="sxs-lookup"><span data-stu-id="11ac6-233">Int32</span></span>|  
|<span data-ttu-id="11ac6-234">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="11ac6-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="11ac6-235">Int32</span><span class="sxs-lookup"><span data-stu-id="11ac6-235">Int32</span></span>|  
|<span data-ttu-id="11ac6-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="11ac6-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="11ac6-237">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="11ac6-237">Boolean</span></span>|  
|<span data-ttu-id="11ac6-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="11ac6-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="11ac6-239">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-239">String</span></span>|  
|<span data-ttu-id="11ac6-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="11ac6-240">IS_NULLABLE</span></span>|<span data-ttu-id="11ac6-241">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="11ac6-241">Boolean</span></span>|  
|<span data-ttu-id="11ac6-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="11ac6-242">DATA_TYPE</span></span>|<span data-ttu-id="11ac6-243">Int32</span><span class="sxs-lookup"><span data-stu-id="11ac6-243">Int32</span></span>|  
|<span data-ttu-id="11ac6-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="11ac6-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="11ac6-245">Int64</span><span class="sxs-lookup"><span data-stu-id="11ac6-245">Int64</span></span>|  
|<span data-ttu-id="11ac6-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="11ac6-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="11ac6-247">Int64</span><span class="sxs-lookup"><span data-stu-id="11ac6-247">Int64</span></span>|  
|<span data-ttu-id="11ac6-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="11ac6-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="11ac6-249">Int32</span><span class="sxs-lookup"><span data-stu-id="11ac6-249">Int32</span></span>|  
|<span data-ttu-id="11ac6-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="11ac6-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="11ac6-251">Int16</span><span class="sxs-lookup"><span data-stu-id="11ac6-251">Int16</span></span>|  
|<span data-ttu-id="11ac6-252">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="11ac6-252">DESCRIPTION</span></span>|<span data-ttu-id="11ac6-253">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-253">String</span></span>|  
|<span data-ttu-id="11ac6-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="11ac6-254">TYPE_NAME</span></span>|<span data-ttu-id="11ac6-255">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-255">String</span></span>|  
|<span data-ttu-id="11ac6-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="11ac6-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="11ac6-257">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="11ac6-258">Katalog</span><span class="sxs-lookup"><span data-stu-id="11ac6-258">Catalog</span></span>  
  
|<span data-ttu-id="11ac6-259">columnName</span><span class="sxs-lookup"><span data-stu-id="11ac6-259">ColumnName</span></span>|<span data-ttu-id="11ac6-260">Veri türü</span><span class="sxs-lookup"><span data-stu-id="11ac6-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="11ac6-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="11ac6-261">CATALOG_NAME</span></span>|<span data-ttu-id="11ac6-262">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-262">String</span></span>|  
|<span data-ttu-id="11ac6-263">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="11ac6-263">DESCRIPTION</span></span>|<span data-ttu-id="11ac6-264">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="11ac6-265">Dizinler</span><span class="sxs-lookup"><span data-stu-id="11ac6-265">Indexes</span></span>  
  
|<span data-ttu-id="11ac6-266">columnName</span><span class="sxs-lookup"><span data-stu-id="11ac6-266">ColumnName</span></span>|<span data-ttu-id="11ac6-267">Veri türü</span><span class="sxs-lookup"><span data-stu-id="11ac6-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="11ac6-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="11ac6-268">TABLE_CATALOG</span></span>|<span data-ttu-id="11ac6-269">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-269">String</span></span>|  
|<span data-ttu-id="11ac6-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="11ac6-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="11ac6-271">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-271">String</span></span>|  
|<span data-ttu-id="11ac6-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="11ac6-272">TABLE_NAME</span></span>|<span data-ttu-id="11ac6-273">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-273">String</span></span>|  
|<span data-ttu-id="11ac6-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="11ac6-274">INDEX_CATALOG</span></span>|<span data-ttu-id="11ac6-275">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-275">String</span></span>|  
|<span data-ttu-id="11ac6-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="11ac6-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="11ac6-277">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-277">String</span></span>|  
|<span data-ttu-id="11ac6-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="11ac6-278">INDEX_NAME</span></span>|<span data-ttu-id="11ac6-279">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-279">String</span></span>|  
|<span data-ttu-id="11ac6-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="11ac6-280">PRIMARY_KEY</span></span>|<span data-ttu-id="11ac6-281">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="11ac6-281">Boolean</span></span>|  
|<span data-ttu-id="11ac6-282">BENZERSİZ</span><span class="sxs-lookup"><span data-stu-id="11ac6-282">UNIQUE</span></span>|<span data-ttu-id="11ac6-283">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="11ac6-283">Boolean</span></span>|  
|<span data-ttu-id="11ac6-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="11ac6-284">CLUSTERED</span></span>|<span data-ttu-id="11ac6-285">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="11ac6-285">Boolean</span></span>|  
|<span data-ttu-id="11ac6-286">TÜRÜ</span><span class="sxs-lookup"><span data-stu-id="11ac6-286">TYPE</span></span>|<span data-ttu-id="11ac6-287">Int32</span><span class="sxs-lookup"><span data-stu-id="11ac6-287">Int32</span></span>|  
|<span data-ttu-id="11ac6-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="11ac6-288">FILL_FACTOR</span></span>|<span data-ttu-id="11ac6-289">Int32</span><span class="sxs-lookup"><span data-stu-id="11ac6-289">Int32</span></span>|  
|<span data-ttu-id="11ac6-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="11ac6-290">INITIAL_SIZE</span></span>|<span data-ttu-id="11ac6-291">Int32</span><span class="sxs-lookup"><span data-stu-id="11ac6-291">Int32</span></span>|  
|<span data-ttu-id="11ac6-292">NULLS</span><span class="sxs-lookup"><span data-stu-id="11ac6-292">NULLS</span></span>|<span data-ttu-id="11ac6-293">Int32</span><span class="sxs-lookup"><span data-stu-id="11ac6-293">Int32</span></span>|  
|<span data-ttu-id="11ac6-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="11ac6-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="11ac6-295">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="11ac6-295">Boolean</span></span>|  
|<span data-ttu-id="11ac6-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="11ac6-296">AUTO_UPDATE</span></span>|<span data-ttu-id="11ac6-297">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="11ac6-297">Boolean</span></span>|  
|<span data-ttu-id="11ac6-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="11ac6-298">NULL_COLLATION</span></span>|<span data-ttu-id="11ac6-299">Int32</span><span class="sxs-lookup"><span data-stu-id="11ac6-299">Int32</span></span>|  
|<span data-ttu-id="11ac6-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="11ac6-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="11ac6-301">Int64</span><span class="sxs-lookup"><span data-stu-id="11ac6-301">Int64</span></span>|  
|<span data-ttu-id="11ac6-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="11ac6-302">COLUMN_NAME</span></span>|<span data-ttu-id="11ac6-303">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-303">String</span></span>|  
|<span data-ttu-id="11ac6-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="11ac6-304">COLUMN_GUID</span></span>|<span data-ttu-id="11ac6-305">Guid</span><span class="sxs-lookup"><span data-stu-id="11ac6-305">Guid</span></span>|  
|<span data-ttu-id="11ac6-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="11ac6-306">COLUMN_PROPID</span></span>|<span data-ttu-id="11ac6-307">Int64</span><span class="sxs-lookup"><span data-stu-id="11ac6-307">Int64</span></span>|  
|<span data-ttu-id="11ac6-308">HARMANLAMA</span><span class="sxs-lookup"><span data-stu-id="11ac6-308">COLLATION</span></span>|<span data-ttu-id="11ac6-309">Int16</span><span class="sxs-lookup"><span data-stu-id="11ac6-309">Int16</span></span>|  
|<span data-ttu-id="11ac6-310">ÖNEM DÜZEYİ</span><span class="sxs-lookup"><span data-stu-id="11ac6-310">CARDINALITY</span></span>|<span data-ttu-id="11ac6-311">Ondalık</span><span class="sxs-lookup"><span data-stu-id="11ac6-311">Decimal</span></span>|  
|<span data-ttu-id="11ac6-312">SAYFALARI</span><span class="sxs-lookup"><span data-stu-id="11ac6-312">PAGES</span></span>|<span data-ttu-id="11ac6-313">Int32</span><span class="sxs-lookup"><span data-stu-id="11ac6-313">Int32</span></span>|  
|<span data-ttu-id="11ac6-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="11ac6-314">FILTER_CONDITION</span></span>|<span data-ttu-id="11ac6-315">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-315">String</span></span>|  
|<span data-ttu-id="11ac6-316">TÜMLEŞİK</span><span class="sxs-lookup"><span data-stu-id="11ac6-316">INTEGRATED</span></span>|<span data-ttu-id="11ac6-317">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="11ac6-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="11ac6-318">Microsoft Oracle OLE DB sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="11ac6-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="11ac6-319">Microsoft Oracle OLE DB sürücü ortak şeması koleksiyonları ek olarak aşağıdaki belirli şeması koleksiyonları destekler:</span><span class="sxs-lookup"><span data-stu-id="11ac6-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="11ac6-320">tabloları</span><span class="sxs-lookup"><span data-stu-id="11ac6-320">Tables</span></span>  
  
-   <span data-ttu-id="11ac6-321">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="11ac6-321">Columns</span></span>  
  
-   <span data-ttu-id="11ac6-322">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="11ac6-322">Procedures</span></span>  
  
-   <span data-ttu-id="11ac6-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="11ac6-323">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="11ac6-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="11ac6-324">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="11ac6-325">Görünümler</span><span class="sxs-lookup"><span data-stu-id="11ac6-325">Views</span></span>  
  
-   <span data-ttu-id="11ac6-326">Dizinler</span><span class="sxs-lookup"><span data-stu-id="11ac6-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="11ac6-327">tabloları</span><span class="sxs-lookup"><span data-stu-id="11ac6-327">Tables</span></span>  
  
|<span data-ttu-id="11ac6-328">columnName</span><span class="sxs-lookup"><span data-stu-id="11ac6-328">ColumnName</span></span>|<span data-ttu-id="11ac6-329">Veri türü</span><span class="sxs-lookup"><span data-stu-id="11ac6-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="11ac6-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="11ac6-330">TABLE_CATALOG</span></span>|<span data-ttu-id="11ac6-331">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-331">String</span></span>|  
|<span data-ttu-id="11ac6-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="11ac6-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="11ac6-333">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-333">String</span></span>|  
|<span data-ttu-id="11ac6-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="11ac6-334">TABLE_NAME</span></span>|<span data-ttu-id="11ac6-335">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-335">String</span></span>|  
|<span data-ttu-id="11ac6-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="11ac6-336">TABLE_TYPE</span></span>|<span data-ttu-id="11ac6-337">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-337">String</span></span>|  
|<span data-ttu-id="11ac6-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="11ac6-338">TABLE_GUID</span></span>|<span data-ttu-id="11ac6-339">Guid</span><span class="sxs-lookup"><span data-stu-id="11ac6-339">Guid</span></span>|  
|<span data-ttu-id="11ac6-340">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="11ac6-340">DESCRIPTION</span></span>|<span data-ttu-id="11ac6-341">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-341">String</span></span>|  
|<span data-ttu-id="11ac6-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="11ac6-342">TABLE_PROPID</span></span>|<span data-ttu-id="11ac6-343">Int64</span><span class="sxs-lookup"><span data-stu-id="11ac6-343">Int64</span></span>|  
|<span data-ttu-id="11ac6-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="11ac6-344">DATE_CREATED</span></span>|<span data-ttu-id="11ac6-345">DateTime</span><span class="sxs-lookup"><span data-stu-id="11ac6-345">DateTime</span></span>|  
|<span data-ttu-id="11ac6-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="11ac6-346">DATE_MODIFIED</span></span>|<span data-ttu-id="11ac6-347">DateTime</span><span class="sxs-lookup"><span data-stu-id="11ac6-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="11ac6-348">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="11ac6-348">Columns</span></span>  
  
|<span data-ttu-id="11ac6-349">columnName</span><span class="sxs-lookup"><span data-stu-id="11ac6-349">ColumnName</span></span>|<span data-ttu-id="11ac6-350">Veri türü</span><span class="sxs-lookup"><span data-stu-id="11ac6-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="11ac6-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="11ac6-351">TABLE_CATALOG</span></span>|<span data-ttu-id="11ac6-352">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-352">String</span></span>|  
|<span data-ttu-id="11ac6-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="11ac6-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="11ac6-354">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-354">String</span></span>|  
|<span data-ttu-id="11ac6-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="11ac6-355">TABLE_NAME</span></span>|<span data-ttu-id="11ac6-356">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-356">String</span></span>|  
|<span data-ttu-id="11ac6-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="11ac6-357">COLUMN_NAME</span></span>|<span data-ttu-id="11ac6-358">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-358">String</span></span>|  
|<span data-ttu-id="11ac6-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="11ac6-359">COLUMN_GUID</span></span>|<span data-ttu-id="11ac6-360">Guid</span><span class="sxs-lookup"><span data-stu-id="11ac6-360">Guid</span></span>|  
|<span data-ttu-id="11ac6-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="11ac6-361">COLUMN_PROPID</span></span>|<span data-ttu-id="11ac6-362">Int64</span><span class="sxs-lookup"><span data-stu-id="11ac6-362">Int64</span></span>|  
|<span data-ttu-id="11ac6-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="11ac6-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="11ac6-364">Int64</span><span class="sxs-lookup"><span data-stu-id="11ac6-364">Int64</span></span>|  
|<span data-ttu-id="11ac6-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="11ac6-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="11ac6-366">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="11ac6-366">Boolean</span></span>|  
|<span data-ttu-id="11ac6-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="11ac6-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="11ac6-368">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-368">String</span></span>|  
|<span data-ttu-id="11ac6-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="11ac6-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="11ac6-370">Int64</span><span class="sxs-lookup"><span data-stu-id="11ac6-370">Int64</span></span>|  
|<span data-ttu-id="11ac6-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="11ac6-371">IS_NULLABLE</span></span>|<span data-ttu-id="11ac6-372">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="11ac6-372">Boolean</span></span>|  
|<span data-ttu-id="11ac6-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="11ac6-373">DATA_TYPE</span></span>|<span data-ttu-id="11ac6-374">Int32</span><span class="sxs-lookup"><span data-stu-id="11ac6-374">Int32</span></span>|  
|<span data-ttu-id="11ac6-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="11ac6-375">TYPE_GUID</span></span>|<span data-ttu-id="11ac6-376">Guid</span><span class="sxs-lookup"><span data-stu-id="11ac6-376">Guid</span></span>|  
|<span data-ttu-id="11ac6-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="11ac6-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="11ac6-378">Int64</span><span class="sxs-lookup"><span data-stu-id="11ac6-378">Int64</span></span>|  
|<span data-ttu-id="11ac6-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="11ac6-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="11ac6-380">Int64</span><span class="sxs-lookup"><span data-stu-id="11ac6-380">Int64</span></span>|  
|<span data-ttu-id="11ac6-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="11ac6-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="11ac6-382">Int32</span><span class="sxs-lookup"><span data-stu-id="11ac6-382">Int32</span></span>|  
|<span data-ttu-id="11ac6-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="11ac6-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="11ac6-384">Int16</span><span class="sxs-lookup"><span data-stu-id="11ac6-384">Int16</span></span>|  
|<span data-ttu-id="11ac6-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="11ac6-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="11ac6-386">Int64</span><span class="sxs-lookup"><span data-stu-id="11ac6-386">Int64</span></span>|  
|<span data-ttu-id="11ac6-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="11ac6-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="11ac6-388">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-388">String</span></span>|  
|<span data-ttu-id="11ac6-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="11ac6-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="11ac6-390">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-390">String</span></span>|  
|<span data-ttu-id="11ac6-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="11ac6-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="11ac6-392">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-392">String</span></span>|  
|<span data-ttu-id="11ac6-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="11ac6-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="11ac6-394">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-394">String</span></span>|  
|<span data-ttu-id="11ac6-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="11ac6-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="11ac6-396">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-396">String</span></span>|  
|<span data-ttu-id="11ac6-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="11ac6-397">COLLATION_NAME</span></span>|<span data-ttu-id="11ac6-398">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-398">String</span></span>|  
|<span data-ttu-id="11ac6-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="11ac6-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="11ac6-400">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-400">String</span></span>|  
|<span data-ttu-id="11ac6-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="11ac6-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="11ac6-402">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-402">String</span></span>|  
|<span data-ttu-id="11ac6-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="11ac6-403">DOMAIN_NAME</span></span>|<span data-ttu-id="11ac6-404">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-404">String</span></span>|  
|<span data-ttu-id="11ac6-405">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="11ac6-405">DESCRIPTION</span></span>|<span data-ttu-id="11ac6-406">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="11ac6-407">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="11ac6-407">Procedures</span></span>  
  
|<span data-ttu-id="11ac6-408">columnName</span><span class="sxs-lookup"><span data-stu-id="11ac6-408">ColumnName</span></span>|<span data-ttu-id="11ac6-409">Veri türü</span><span class="sxs-lookup"><span data-stu-id="11ac6-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="11ac6-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="11ac6-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="11ac6-411">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-411">String</span></span>|  
|<span data-ttu-id="11ac6-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="11ac6-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="11ac6-413">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-413">String</span></span>|  
|<span data-ttu-id="11ac6-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="11ac6-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="11ac6-415">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-415">String</span></span>|  
|<span data-ttu-id="11ac6-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="11ac6-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="11ac6-417">Int16</span><span class="sxs-lookup"><span data-stu-id="11ac6-417">Int16</span></span>|  
|<span data-ttu-id="11ac6-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="11ac6-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="11ac6-419">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-419">String</span></span>|  
|<span data-ttu-id="11ac6-420">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="11ac6-420">DESCRIPTION</span></span>|<span data-ttu-id="11ac6-421">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-421">String</span></span>|  
|<span data-ttu-id="11ac6-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="11ac6-422">DATE_CREATED</span></span>|<span data-ttu-id="11ac6-423">DateTime</span><span class="sxs-lookup"><span data-stu-id="11ac6-423">DateTime</span></span>|  
|<span data-ttu-id="11ac6-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="11ac6-424">DATE_MODIFIED</span></span>|<span data-ttu-id="11ac6-425">DateTime</span><span class="sxs-lookup"><span data-stu-id="11ac6-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="11ac6-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="11ac6-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="11ac6-427">columnName</span><span class="sxs-lookup"><span data-stu-id="11ac6-427">ColumnName</span></span>|<span data-ttu-id="11ac6-428">Veri türü</span><span class="sxs-lookup"><span data-stu-id="11ac6-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="11ac6-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="11ac6-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="11ac6-430">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-430">String</span></span>|  
|<span data-ttu-id="11ac6-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="11ac6-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="11ac6-432">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-432">String</span></span>|  
|<span data-ttu-id="11ac6-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="11ac6-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="11ac6-434">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-434">String</span></span>|  
|<span data-ttu-id="11ac6-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="11ac6-435">COLUMN_NAME</span></span>|<span data-ttu-id="11ac6-436">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-436">String</span></span>|  
|<span data-ttu-id="11ac6-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="11ac6-437">COLUMN_GUID</span></span>|<span data-ttu-id="11ac6-438">Guid</span><span class="sxs-lookup"><span data-stu-id="11ac6-438">Guid</span></span>|  
|<span data-ttu-id="11ac6-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="11ac6-439">COLUMN_PROPID</span></span>|<span data-ttu-id="11ac6-440">Int64</span><span class="sxs-lookup"><span data-stu-id="11ac6-440">Int64</span></span>|  
|<span data-ttu-id="11ac6-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="11ac6-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="11ac6-442">Int64</span><span class="sxs-lookup"><span data-stu-id="11ac6-442">Int64</span></span>|  
|<span data-ttu-id="11ac6-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="11ac6-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="11ac6-444">Int64</span><span class="sxs-lookup"><span data-stu-id="11ac6-444">Int64</span></span>|  
|<span data-ttu-id="11ac6-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="11ac6-445">IS_NULLABLE</span></span>|<span data-ttu-id="11ac6-446">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="11ac6-446">Boolean</span></span>|  
|<span data-ttu-id="11ac6-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="11ac6-447">DATA_TYPE</span></span>|<span data-ttu-id="11ac6-448">Int32</span><span class="sxs-lookup"><span data-stu-id="11ac6-448">Int32</span></span>|  
|<span data-ttu-id="11ac6-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="11ac6-449">TYPE_GUID</span></span>|<span data-ttu-id="11ac6-450">Guid</span><span class="sxs-lookup"><span data-stu-id="11ac6-450">Guid</span></span>|  
|<span data-ttu-id="11ac6-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="11ac6-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="11ac6-452">Int64</span><span class="sxs-lookup"><span data-stu-id="11ac6-452">Int64</span></span>|  
|<span data-ttu-id="11ac6-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="11ac6-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="11ac6-454">Int64</span><span class="sxs-lookup"><span data-stu-id="11ac6-454">Int64</span></span>|  
|<span data-ttu-id="11ac6-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="11ac6-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="11ac6-456">Int32</span><span class="sxs-lookup"><span data-stu-id="11ac6-456">Int32</span></span>|  
|<span data-ttu-id="11ac6-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="11ac6-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="11ac6-458">Int16</span><span class="sxs-lookup"><span data-stu-id="11ac6-458">Int16</span></span>|  
|<span data-ttu-id="11ac6-459">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="11ac6-459">DESCRIPTION</span></span>|<span data-ttu-id="11ac6-460">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-460">String</span></span>|  
|<span data-ttu-id="11ac6-461">AŞIRI YÜKLEME</span><span class="sxs-lookup"><span data-stu-id="11ac6-461">OVERLOAD</span></span>|<span data-ttu-id="11ac6-462">Int16</span><span class="sxs-lookup"><span data-stu-id="11ac6-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="11ac6-463">Görünümler</span><span class="sxs-lookup"><span data-stu-id="11ac6-463">Views</span></span>  
  
|<span data-ttu-id="11ac6-464">columnName</span><span class="sxs-lookup"><span data-stu-id="11ac6-464">ColumnName</span></span>|<span data-ttu-id="11ac6-465">Veri türü</span><span class="sxs-lookup"><span data-stu-id="11ac6-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="11ac6-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="11ac6-466">TABLE_CATALOG</span></span>|<span data-ttu-id="11ac6-467">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-467">String</span></span>|  
|<span data-ttu-id="11ac6-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="11ac6-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="11ac6-469">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-469">String</span></span>|  
|<span data-ttu-id="11ac6-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="11ac6-470">TABLE_NAME</span></span>|<span data-ttu-id="11ac6-471">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-471">String</span></span>|  
|<span data-ttu-id="11ac6-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="11ac6-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="11ac6-473">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-473">String</span></span>|  
|<span data-ttu-id="11ac6-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="11ac6-474">CHECK_OPTION</span></span>|<span data-ttu-id="11ac6-475">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="11ac6-475">Boolean</span></span>|  
|<span data-ttu-id="11ac6-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="11ac6-476">IS_UPDATABLE</span></span>|<span data-ttu-id="11ac6-477">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="11ac6-477">Boolean</span></span>|  
|<span data-ttu-id="11ac6-478">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="11ac6-478">DESCRIPTION</span></span>|<span data-ttu-id="11ac6-479">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-479">String</span></span>|  
|<span data-ttu-id="11ac6-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="11ac6-480">DATE_CREATED</span></span>|<span data-ttu-id="11ac6-481">DateTime</span><span class="sxs-lookup"><span data-stu-id="11ac6-481">DateTime</span></span>|  
|<span data-ttu-id="11ac6-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="11ac6-482">DATE_MODIFIED</span></span>|<span data-ttu-id="11ac6-483">DateTime</span><span class="sxs-lookup"><span data-stu-id="11ac6-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="11ac6-484">Dizinler</span><span class="sxs-lookup"><span data-stu-id="11ac6-484">Indexes</span></span>  
  
|<span data-ttu-id="11ac6-485">columnName</span><span class="sxs-lookup"><span data-stu-id="11ac6-485">ColumnName</span></span>|<span data-ttu-id="11ac6-486">Veri türü</span><span class="sxs-lookup"><span data-stu-id="11ac6-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="11ac6-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="11ac6-487">TABLE_CATALOG</span></span>|<span data-ttu-id="11ac6-488">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-488">String</span></span>|  
|<span data-ttu-id="11ac6-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="11ac6-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="11ac6-490">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-490">String</span></span>|  
|<span data-ttu-id="11ac6-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="11ac6-491">TABLE_NAME</span></span>|<span data-ttu-id="11ac6-492">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-492">String</span></span>|  
|<span data-ttu-id="11ac6-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="11ac6-493">INDEX_CATALOG</span></span>|<span data-ttu-id="11ac6-494">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-494">String</span></span>|  
|<span data-ttu-id="11ac6-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="11ac6-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="11ac6-496">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-496">String</span></span>|  
|<span data-ttu-id="11ac6-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="11ac6-497">INDEX_NAME</span></span>|<span data-ttu-id="11ac6-498">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-498">String</span></span>|  
|<span data-ttu-id="11ac6-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="11ac6-499">PRIMARY_KEY</span></span>|<span data-ttu-id="11ac6-500">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="11ac6-500">Boolean</span></span>|  
|<span data-ttu-id="11ac6-501">BENZERSİZ</span><span class="sxs-lookup"><span data-stu-id="11ac6-501">UNIQUE</span></span>|<span data-ttu-id="11ac6-502">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="11ac6-502">Boolean</span></span>|  
|<span data-ttu-id="11ac6-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="11ac6-503">CLUSTERED</span></span>|<span data-ttu-id="11ac6-504">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="11ac6-504">Boolean</span></span>|  
|<span data-ttu-id="11ac6-505">TÜRÜ</span><span class="sxs-lookup"><span data-stu-id="11ac6-505">TYPE</span></span>|<span data-ttu-id="11ac6-506">Int32</span><span class="sxs-lookup"><span data-stu-id="11ac6-506">Int32</span></span>|  
|<span data-ttu-id="11ac6-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="11ac6-507">FILL_FACTOR</span></span>|<span data-ttu-id="11ac6-508">Int32</span><span class="sxs-lookup"><span data-stu-id="11ac6-508">Int32</span></span>|  
|<span data-ttu-id="11ac6-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="11ac6-509">INITIAL_SIZE</span></span>|<span data-ttu-id="11ac6-510">Int32</span><span class="sxs-lookup"><span data-stu-id="11ac6-510">Int32</span></span>|  
|<span data-ttu-id="11ac6-511">NULLS</span><span class="sxs-lookup"><span data-stu-id="11ac6-511">NULLS</span></span>|<span data-ttu-id="11ac6-512">Int32</span><span class="sxs-lookup"><span data-stu-id="11ac6-512">Int32</span></span>|  
|<span data-ttu-id="11ac6-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="11ac6-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="11ac6-514">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="11ac6-514">Boolean</span></span>|  
|<span data-ttu-id="11ac6-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="11ac6-515">AUTO_UPDATE</span></span>|<span data-ttu-id="11ac6-516">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="11ac6-516">Boolean</span></span>|  
|<span data-ttu-id="11ac6-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="11ac6-517">NULL_COLLATION</span></span>|<span data-ttu-id="11ac6-518">Int32</span><span class="sxs-lookup"><span data-stu-id="11ac6-518">Int32</span></span>|  
|<span data-ttu-id="11ac6-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="11ac6-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="11ac6-520">Int64</span><span class="sxs-lookup"><span data-stu-id="11ac6-520">Int64</span></span>|  
|<span data-ttu-id="11ac6-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="11ac6-521">COLUMN_NAME</span></span>|<span data-ttu-id="11ac6-522">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-522">String</span></span>|  
|<span data-ttu-id="11ac6-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="11ac6-523">COLUMN_GUID</span></span>|<span data-ttu-id="11ac6-524">Guid</span><span class="sxs-lookup"><span data-stu-id="11ac6-524">Guid</span></span>|  
|<span data-ttu-id="11ac6-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="11ac6-525">COLUMN_PROPID</span></span>|<span data-ttu-id="11ac6-526">Int64</span><span class="sxs-lookup"><span data-stu-id="11ac6-526">Int64</span></span>|  
|<span data-ttu-id="11ac6-527">HARMANLAMA</span><span class="sxs-lookup"><span data-stu-id="11ac6-527">COLLATION</span></span>|<span data-ttu-id="11ac6-528">Int16</span><span class="sxs-lookup"><span data-stu-id="11ac6-528">Int16</span></span>|  
|<span data-ttu-id="11ac6-529">ÖNEM DÜZEYİ</span><span class="sxs-lookup"><span data-stu-id="11ac6-529">CARDINALITY</span></span>|<span data-ttu-id="11ac6-530">Ondalık</span><span class="sxs-lookup"><span data-stu-id="11ac6-530">Decimal</span></span>|  
|<span data-ttu-id="11ac6-531">SAYFALARI</span><span class="sxs-lookup"><span data-stu-id="11ac6-531">PAGES</span></span>|<span data-ttu-id="11ac6-532">Int32</span><span class="sxs-lookup"><span data-stu-id="11ac6-532">Int32</span></span>|  
|<span data-ttu-id="11ac6-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="11ac6-533">FILTER_CONDITION</span></span>|<span data-ttu-id="11ac6-534">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-534">String</span></span>|  
|<span data-ttu-id="11ac6-535">TÜMLEŞİK</span><span class="sxs-lookup"><span data-stu-id="11ac6-535">INTEGRATED</span></span>|<span data-ttu-id="11ac6-536">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="11ac6-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="11ac6-537">Microsoft Jet OLE DB sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="11ac6-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="11ac6-538">Microsoft Jet OLE DB sürücü ortak şeması koleksiyonları ek olarak aşağıdaki belirli şeması koleksiyonları destekler:</span><span class="sxs-lookup"><span data-stu-id="11ac6-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="11ac6-539">tabloları</span><span class="sxs-lookup"><span data-stu-id="11ac6-539">Tables</span></span>  
  
-   <span data-ttu-id="11ac6-540">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="11ac6-540">Columns</span></span>  
  
-   <span data-ttu-id="11ac6-541">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="11ac6-541">Procedures</span></span>  
  
-   <span data-ttu-id="11ac6-542">Görünümler</span><span class="sxs-lookup"><span data-stu-id="11ac6-542">Views</span></span>  
  
-   <span data-ttu-id="11ac6-543">Dizinler</span><span class="sxs-lookup"><span data-stu-id="11ac6-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="11ac6-544">tabloları</span><span class="sxs-lookup"><span data-stu-id="11ac6-544">Tables</span></span>  
  
|<span data-ttu-id="11ac6-545">columnName</span><span class="sxs-lookup"><span data-stu-id="11ac6-545">ColumnName</span></span>|<span data-ttu-id="11ac6-546">Veri türü</span><span class="sxs-lookup"><span data-stu-id="11ac6-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="11ac6-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="11ac6-547">TABLE_CATALOG</span></span>|<span data-ttu-id="11ac6-548">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-548">String</span></span>|  
|<span data-ttu-id="11ac6-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="11ac6-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="11ac6-550">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-550">String</span></span>|  
|<span data-ttu-id="11ac6-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="11ac6-551">TABLE_NAME</span></span>|<span data-ttu-id="11ac6-552">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-552">String</span></span>|  
|<span data-ttu-id="11ac6-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="11ac6-553">TABLE_TYPE</span></span>|<span data-ttu-id="11ac6-554">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-554">String</span></span>|  
|<span data-ttu-id="11ac6-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="11ac6-555">TABLE_GUID</span></span>|<span data-ttu-id="11ac6-556">Guid</span><span class="sxs-lookup"><span data-stu-id="11ac6-556">Guid</span></span>|  
|<span data-ttu-id="11ac6-557">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="11ac6-557">DESCRIPTION</span></span>|<span data-ttu-id="11ac6-558">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-558">String</span></span>|  
|<span data-ttu-id="11ac6-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="11ac6-559">TABLE_PROPID</span></span>|<span data-ttu-id="11ac6-560">Int64</span><span class="sxs-lookup"><span data-stu-id="11ac6-560">Int64</span></span>|  
|<span data-ttu-id="11ac6-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="11ac6-561">DATE_CREATED</span></span>|<span data-ttu-id="11ac6-562">DateTime</span><span class="sxs-lookup"><span data-stu-id="11ac6-562">DateTime</span></span>|  
|<span data-ttu-id="11ac6-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="11ac6-563">DATE_MODIFIED</span></span>|<span data-ttu-id="11ac6-564">DateTime</span><span class="sxs-lookup"><span data-stu-id="11ac6-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="11ac6-565">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="11ac6-565">Columns</span></span>  
  
|<span data-ttu-id="11ac6-566">columnName</span><span class="sxs-lookup"><span data-stu-id="11ac6-566">ColumnName</span></span>|<span data-ttu-id="11ac6-567">Veri türü</span><span class="sxs-lookup"><span data-stu-id="11ac6-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="11ac6-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="11ac6-568">TABLE_CATALOG</span></span>|<span data-ttu-id="11ac6-569">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-569">String</span></span>|  
|<span data-ttu-id="11ac6-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="11ac6-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="11ac6-571">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-571">String</span></span>|  
|<span data-ttu-id="11ac6-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="11ac6-572">TABLE_NAME</span></span>|<span data-ttu-id="11ac6-573">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-573">String</span></span>|  
|<span data-ttu-id="11ac6-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="11ac6-574">COLUMN_NAME</span></span>|<span data-ttu-id="11ac6-575">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-575">String</span></span>|  
|<span data-ttu-id="11ac6-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="11ac6-576">COLUMN_GUID</span></span>|<span data-ttu-id="11ac6-577">Guid</span><span class="sxs-lookup"><span data-stu-id="11ac6-577">Guid</span></span>|  
|<span data-ttu-id="11ac6-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="11ac6-578">COLUMN_PROPID</span></span>|<span data-ttu-id="11ac6-579">Int64</span><span class="sxs-lookup"><span data-stu-id="11ac6-579">Int64</span></span>|  
|<span data-ttu-id="11ac6-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="11ac6-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="11ac6-581">Int64</span><span class="sxs-lookup"><span data-stu-id="11ac6-581">Int64</span></span>|  
|<span data-ttu-id="11ac6-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="11ac6-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="11ac6-583">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="11ac6-583">Boolean</span></span>|  
|<span data-ttu-id="11ac6-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="11ac6-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="11ac6-585">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-585">String</span></span>|  
|<span data-ttu-id="11ac6-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="11ac6-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="11ac6-587">Int64</span><span class="sxs-lookup"><span data-stu-id="11ac6-587">Int64</span></span>|  
|<span data-ttu-id="11ac6-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="11ac6-588">IS_NULLABLE</span></span>|<span data-ttu-id="11ac6-589">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="11ac6-589">Boolean</span></span>|  
|<span data-ttu-id="11ac6-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="11ac6-590">DATA_TYPE</span></span>|<span data-ttu-id="11ac6-591">Int32</span><span class="sxs-lookup"><span data-stu-id="11ac6-591">Int32</span></span>|  
|<span data-ttu-id="11ac6-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="11ac6-592">TYPE_GUID</span></span>|<span data-ttu-id="11ac6-593">Guid</span><span class="sxs-lookup"><span data-stu-id="11ac6-593">Guid</span></span>|  
|<span data-ttu-id="11ac6-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="11ac6-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="11ac6-595">Int64</span><span class="sxs-lookup"><span data-stu-id="11ac6-595">Int64</span></span>|  
|<span data-ttu-id="11ac6-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="11ac6-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="11ac6-597">Int64</span><span class="sxs-lookup"><span data-stu-id="11ac6-597">Int64</span></span>|  
|<span data-ttu-id="11ac6-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="11ac6-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="11ac6-599">Int32</span><span class="sxs-lookup"><span data-stu-id="11ac6-599">Int32</span></span>|  
|<span data-ttu-id="11ac6-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="11ac6-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="11ac6-601">Int16</span><span class="sxs-lookup"><span data-stu-id="11ac6-601">Int16</span></span>|  
|<span data-ttu-id="11ac6-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="11ac6-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="11ac6-603">Int64</span><span class="sxs-lookup"><span data-stu-id="11ac6-603">Int64</span></span>|  
|<span data-ttu-id="11ac6-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="11ac6-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="11ac6-605">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-605">String</span></span>|  
|<span data-ttu-id="11ac6-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="11ac6-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="11ac6-607">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-607">String</span></span>|  
|<span data-ttu-id="11ac6-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="11ac6-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="11ac6-609">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-609">String</span></span>|  
|<span data-ttu-id="11ac6-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="11ac6-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="11ac6-611">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-611">String</span></span>|  
|<span data-ttu-id="11ac6-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="11ac6-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="11ac6-613">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-613">String</span></span>|  
|<span data-ttu-id="11ac6-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="11ac6-614">COLLATION_NAME</span></span>|<span data-ttu-id="11ac6-615">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-615">String</span></span>|  
|<span data-ttu-id="11ac6-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="11ac6-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="11ac6-617">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-617">String</span></span>|  
|<span data-ttu-id="11ac6-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="11ac6-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="11ac6-619">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-619">String</span></span>|  
|<span data-ttu-id="11ac6-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="11ac6-620">DOMAIN_NAME</span></span>|<span data-ttu-id="11ac6-621">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-621">String</span></span>|  
|<span data-ttu-id="11ac6-622">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="11ac6-622">DESCRIPTION</span></span>|<span data-ttu-id="11ac6-623">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="11ac6-624">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="11ac6-624">Procedures</span></span>  
  
|<span data-ttu-id="11ac6-625">columnName</span><span class="sxs-lookup"><span data-stu-id="11ac6-625">ColumnName</span></span>|<span data-ttu-id="11ac6-626">Veri türü</span><span class="sxs-lookup"><span data-stu-id="11ac6-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="11ac6-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="11ac6-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="11ac6-628">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-628">String</span></span>|  
|<span data-ttu-id="11ac6-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="11ac6-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="11ac6-630">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-630">String</span></span>|  
|<span data-ttu-id="11ac6-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="11ac6-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="11ac6-632">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-632">String</span></span>|  
|<span data-ttu-id="11ac6-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="11ac6-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="11ac6-634">Int16</span><span class="sxs-lookup"><span data-stu-id="11ac6-634">Int16</span></span>|  
|<span data-ttu-id="11ac6-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="11ac6-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="11ac6-636">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-636">String</span></span>|  
|<span data-ttu-id="11ac6-637">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="11ac6-637">DESCRIPTION</span></span>|<span data-ttu-id="11ac6-638">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-638">String</span></span>|  
|<span data-ttu-id="11ac6-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="11ac6-639">DATE_CREATED</span></span>|<span data-ttu-id="11ac6-640">DateTime</span><span class="sxs-lookup"><span data-stu-id="11ac6-640">DateTime</span></span>|  
|<span data-ttu-id="11ac6-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="11ac6-641">DATE_MODIFIED</span></span>|<span data-ttu-id="11ac6-642">DateTime</span><span class="sxs-lookup"><span data-stu-id="11ac6-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="11ac6-643">Görünümler</span><span class="sxs-lookup"><span data-stu-id="11ac6-643">Views</span></span>  
  
|<span data-ttu-id="11ac6-644">columnName</span><span class="sxs-lookup"><span data-stu-id="11ac6-644">ColumnName</span></span>|<span data-ttu-id="11ac6-645">Veri türü</span><span class="sxs-lookup"><span data-stu-id="11ac6-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="11ac6-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="11ac6-646">TABLE_CATALOG</span></span>|<span data-ttu-id="11ac6-647">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-647">String</span></span>|  
|<span data-ttu-id="11ac6-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="11ac6-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="11ac6-649">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-649">String</span></span>|  
|<span data-ttu-id="11ac6-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="11ac6-650">TABLE_NAME</span></span>|<span data-ttu-id="11ac6-651">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-651">String</span></span>|  
|<span data-ttu-id="11ac6-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="11ac6-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="11ac6-653">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-653">String</span></span>|  
|<span data-ttu-id="11ac6-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="11ac6-654">CHECK_OPTION</span></span>|<span data-ttu-id="11ac6-655">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="11ac6-655">Boolean</span></span>|  
|<span data-ttu-id="11ac6-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="11ac6-656">IS_UPDATABLE</span></span>|<span data-ttu-id="11ac6-657">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="11ac6-657">Boolean</span></span>|  
|<span data-ttu-id="11ac6-658">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="11ac6-658">DESCRIPTION</span></span>|<span data-ttu-id="11ac6-659">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-659">String</span></span>|  
|<span data-ttu-id="11ac6-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="11ac6-660">DATE_CREATED</span></span>|<span data-ttu-id="11ac6-661">DateTime</span><span class="sxs-lookup"><span data-stu-id="11ac6-661">DateTime</span></span>|  
|<span data-ttu-id="11ac6-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="11ac6-662">DATE_MODIFIED</span></span>|<span data-ttu-id="11ac6-663">DateTime</span><span class="sxs-lookup"><span data-stu-id="11ac6-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="11ac6-664">Dizinler</span><span class="sxs-lookup"><span data-stu-id="11ac6-664">Indexes</span></span>  
  
|<span data-ttu-id="11ac6-665">columnName</span><span class="sxs-lookup"><span data-stu-id="11ac6-665">ColumnName</span></span>|<span data-ttu-id="11ac6-666">Veri türü</span><span class="sxs-lookup"><span data-stu-id="11ac6-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="11ac6-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="11ac6-667">TABLE_CATALOG</span></span>|<span data-ttu-id="11ac6-668">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-668">String</span></span>|  
|<span data-ttu-id="11ac6-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="11ac6-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="11ac6-670">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-670">String</span></span>|  
|<span data-ttu-id="11ac6-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="11ac6-671">TABLE_NAME</span></span>|<span data-ttu-id="11ac6-672">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-672">String</span></span>|  
|<span data-ttu-id="11ac6-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="11ac6-673">INDEX_CATALOG</span></span>|<span data-ttu-id="11ac6-674">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-674">String</span></span>|  
|<span data-ttu-id="11ac6-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="11ac6-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="11ac6-676">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-676">String</span></span>|  
|<span data-ttu-id="11ac6-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="11ac6-677">INDEX_NAME</span></span>|<span data-ttu-id="11ac6-678">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-678">String</span></span>|  
|<span data-ttu-id="11ac6-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="11ac6-679">PRIMARY_KEY</span></span>|<span data-ttu-id="11ac6-680">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="11ac6-680">Boolean</span></span>|  
|<span data-ttu-id="11ac6-681">BENZERSİZ</span><span class="sxs-lookup"><span data-stu-id="11ac6-681">UNIQUE</span></span>|<span data-ttu-id="11ac6-682">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="11ac6-682">Boolean</span></span>|  
|<span data-ttu-id="11ac6-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="11ac6-683">CLUSTERED</span></span>|<span data-ttu-id="11ac6-684">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="11ac6-684">Boolean</span></span>|  
|<span data-ttu-id="11ac6-685">TÜRÜ</span><span class="sxs-lookup"><span data-stu-id="11ac6-685">TYPE</span></span>|<span data-ttu-id="11ac6-686">Int32</span><span class="sxs-lookup"><span data-stu-id="11ac6-686">Int32</span></span>|  
|<span data-ttu-id="11ac6-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="11ac6-687">FILL_FACTOR</span></span>|<span data-ttu-id="11ac6-688">Int32</span><span class="sxs-lookup"><span data-stu-id="11ac6-688">Int32</span></span>|  
|<span data-ttu-id="11ac6-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="11ac6-689">INITIAL_SIZE</span></span>|<span data-ttu-id="11ac6-690">Int32</span><span class="sxs-lookup"><span data-stu-id="11ac6-690">Int32</span></span>|  
|<span data-ttu-id="11ac6-691">NULLS</span><span class="sxs-lookup"><span data-stu-id="11ac6-691">NULLS</span></span>|<span data-ttu-id="11ac6-692">Int32</span><span class="sxs-lookup"><span data-stu-id="11ac6-692">Int32</span></span>|  
|<span data-ttu-id="11ac6-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="11ac6-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="11ac6-694">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="11ac6-694">Boolean</span></span>|  
|<span data-ttu-id="11ac6-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="11ac6-695">AUTO_UPDATE</span></span>|<span data-ttu-id="11ac6-696">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="11ac6-696">Boolean</span></span>|  
|<span data-ttu-id="11ac6-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="11ac6-697">NULL_COLLATION</span></span>|<span data-ttu-id="11ac6-698">Int32</span><span class="sxs-lookup"><span data-stu-id="11ac6-698">Int32</span></span>|  
|<span data-ttu-id="11ac6-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="11ac6-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="11ac6-700">Int64</span><span class="sxs-lookup"><span data-stu-id="11ac6-700">Int64</span></span>|  
|<span data-ttu-id="11ac6-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="11ac6-701">COLUMN_NAME</span></span>|<span data-ttu-id="11ac6-702">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-702">String</span></span>|  
|<span data-ttu-id="11ac6-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="11ac6-703">COLUMN_GUID</span></span>|<span data-ttu-id="11ac6-704">Guid</span><span class="sxs-lookup"><span data-stu-id="11ac6-704">Guid</span></span>|  
|<span data-ttu-id="11ac6-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="11ac6-705">COLUMN_PROPID</span></span>|<span data-ttu-id="11ac6-706">Int64</span><span class="sxs-lookup"><span data-stu-id="11ac6-706">Int64</span></span>|  
|<span data-ttu-id="11ac6-707">HARMANLAMA</span><span class="sxs-lookup"><span data-stu-id="11ac6-707">COLLATION</span></span>|<span data-ttu-id="11ac6-708">Int16</span><span class="sxs-lookup"><span data-stu-id="11ac6-708">Int16</span></span>|  
|<span data-ttu-id="11ac6-709">ÖNEM DÜZEYİ</span><span class="sxs-lookup"><span data-stu-id="11ac6-709">CARDINALITY</span></span>|<span data-ttu-id="11ac6-710">Ondalık</span><span class="sxs-lookup"><span data-stu-id="11ac6-710">Decimal</span></span>|  
|<span data-ttu-id="11ac6-711">SAYFALARI</span><span class="sxs-lookup"><span data-stu-id="11ac6-711">PAGES</span></span>|<span data-ttu-id="11ac6-712">Int32</span><span class="sxs-lookup"><span data-stu-id="11ac6-712">Int32</span></span>|  
|<span data-ttu-id="11ac6-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="11ac6-713">FILTER_CONDITION</span></span>|<span data-ttu-id="11ac6-714">Dize</span><span class="sxs-lookup"><span data-stu-id="11ac6-714">String</span></span>|  
|<span data-ttu-id="11ac6-715">TÜMLEŞİK</span><span class="sxs-lookup"><span data-stu-id="11ac6-715">INTEGRATED</span></span>|<span data-ttu-id="11ac6-716">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="11ac6-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="11ac6-717">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="11ac6-717">See Also</span></span>  
 [<span data-ttu-id="11ac6-718">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="11ac6-718">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
