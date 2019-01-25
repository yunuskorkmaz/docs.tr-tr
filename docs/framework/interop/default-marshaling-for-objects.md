---
title: Nesneler için Varsayılan Sıralama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- objects, interop marshaling
- interop marshaling, objects
ms.assetid: c2ef0284-b061-4e12-b6d3-6a502b9cc558
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84a3ea24120a9548c9d1cd2b7b83997a2c849cde
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54528032"
---
# <a name="default-marshaling-for-objects"></a><span data-ttu-id="10ca3-102">Nesneler için Varsayılan Hazırlama</span><span class="sxs-lookup"><span data-stu-id="10ca3-102">Default Marshaling for Objects</span></span>
<span data-ttu-id="10ca3-103">Parametreler ve alanlar olarak yazılan <xref:System.Object?displayProperty=nameWithType> yönetilmeyen koda aşağıdaki türlerden biri olarak kullanıma sunulabilir:</span><span class="sxs-lookup"><span data-stu-id="10ca3-103">Parameters and fields typed as <xref:System.Object?displayProperty=nameWithType> can be exposed to unmanaged code as one of the following types:</span></span>  
  
-   <span data-ttu-id="10ca3-104">Nesnesi bir parametre olduğunda bir değişken.</span><span class="sxs-lookup"><span data-stu-id="10ca3-104">A variant when the object is a parameter.</span></span>  
  
-   <span data-ttu-id="10ca3-105">Nesne yapısını alanı olduğunda bir arabirim.</span><span class="sxs-lookup"><span data-stu-id="10ca3-105">An interface when the object is a structure field.</span></span>  
  
 <span data-ttu-id="10ca3-106">Yalnızca COM birlikte çalışma hazırlama için nesne türlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="10ca3-106">Only COM interop supports marshaling for object types.</span></span> <span data-ttu-id="10ca3-107">COM çeşitleri nesnelere hazırlamak için varsayılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="10ca3-107">The default behavior is to marshal objects to COM variants.</span></span> <span data-ttu-id="10ca3-108">Bu kurallar yalnızca türü için geçerli **nesne** ve türetilen bir türü kesin olarak belirtilmiş nesneler için geçerli değildir **nesne** sınıfı.</span><span class="sxs-lookup"><span data-stu-id="10ca3-108">These rules apply only to the type **Object** and do not apply to strongly typed objects that derive from the **Object** class.</span></span>  
  
 <span data-ttu-id="10ca3-109">Bu konu, nesne türlerini hazırlama hakkında aşağıdaki ek bilgileri sağlar:</span><span class="sxs-lookup"><span data-stu-id="10ca3-109">This topic provides the following additional information about marshaling object types:</span></span>  
  
-   [<span data-ttu-id="10ca3-110">Hazırlama seçenekleri</span><span class="sxs-lookup"><span data-stu-id="10ca3-110">Marshaling Options</span></span>](#cpcondefaultmarshalingforobjectsanchor7)  
  
-   [<span data-ttu-id="10ca3-111">Nesne arabirimi için hazırlama</span><span class="sxs-lookup"><span data-stu-id="10ca3-111">Marshaling Object to Interface</span></span>](#cpcondefaultmarshalingforobjectsanchor2)  
  
-   [<span data-ttu-id="10ca3-112">Nesne değişken için hazırlama</span><span class="sxs-lookup"><span data-stu-id="10ca3-112">Marshaling Object to Variant</span></span>](#cpcondefaultmarshalingforobjectsanchor3)  
  
-   [<span data-ttu-id="10ca3-113">VARIANT nesnesi için hazırlama</span><span class="sxs-lookup"><span data-stu-id="10ca3-113">Marshaling Variant to Object</span></span>](#cpcondefaultmarshalingforobjectsanchor4)  
  
-   [<span data-ttu-id="10ca3-114">ByRef çeşitleri hazırlama</span><span class="sxs-lookup"><span data-stu-id="10ca3-114">Marshaling ByRef Variants</span></span>](#cpcondefaultmarshalingforobjectsanchor6)  
  
<a name="cpcondefaultmarshalingforobjectsanchor7"></a>   
## <a name="marshaling-options"></a><span data-ttu-id="10ca3-115">Hazırlama seçenekleri</span><span class="sxs-lookup"><span data-stu-id="10ca3-115">Marshaling Options</span></span>  
 <span data-ttu-id="10ca3-116">Sıralama seçenekleri aşağıdaki tabloda gösterilmektedir **nesne** veri türü.</span><span class="sxs-lookup"><span data-stu-id="10ca3-116">The following table shows the marshaling options for the **Object** data type.</span></span> <span data-ttu-id="10ca3-117"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Özniteliği sağlayan çeşitli <xref:System.Runtime.InteropServices.UnmanagedType> numaralandırma değerleri için sıralama nesneleri.</span><span class="sxs-lookup"><span data-stu-id="10ca3-117">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal objects.</span></span>  
  
|<span data-ttu-id="10ca3-118">Numaralandırma türü</span><span class="sxs-lookup"><span data-stu-id="10ca3-118">Enumeration type</span></span>|<span data-ttu-id="10ca3-119">Yönetilmeyen biçimi açıklaması</span><span class="sxs-lookup"><span data-stu-id="10ca3-119">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|<span data-ttu-id="10ca3-120">**UnmanagedType.Struct**</span><span class="sxs-lookup"><span data-stu-id="10ca3-120">**UnmanagedType.Struct**</span></span><br /><br /> <span data-ttu-id="10ca3-121">(varsayılan parametreleri için)</span><span class="sxs-lookup"><span data-stu-id="10ca3-121">(default for parameters)</span></span>|<span data-ttu-id="10ca3-122">Bir COM Stili değişken.</span><span class="sxs-lookup"><span data-stu-id="10ca3-122">A COM-style variant.</span></span>|  
|<span data-ttu-id="10ca3-123">**UnmanagedType.Interface**</span><span class="sxs-lookup"><span data-stu-id="10ca3-123">**UnmanagedType.Interface**</span></span>|<span data-ttu-id="10ca3-124">Bir **IDispatch** arabirim, mümkünse; Aksi takdirde bir **IUnknown** arabirimi.</span><span class="sxs-lookup"><span data-stu-id="10ca3-124">An **IDispatch** interface, if possible; otherwise, an **IUnknown** interface.</span></span>|  
|<span data-ttu-id="10ca3-125">**UnmanagedType.IUnknown**</span><span class="sxs-lookup"><span data-stu-id="10ca3-125">**UnmanagedType.IUnknown**</span></span><br /><br /> <span data-ttu-id="10ca3-126">(alanlar için varsayılan)</span><span class="sxs-lookup"><span data-stu-id="10ca3-126">(default for fields)</span></span>|<span data-ttu-id="10ca3-127">Bir **IUnknown** arabirimi.</span><span class="sxs-lookup"><span data-stu-id="10ca3-127">An **IUnknown** interface.</span></span>|  
|<span data-ttu-id="10ca3-128">**UnmanagedType.IDispatch**</span><span class="sxs-lookup"><span data-stu-id="10ca3-128">**UnmanagedType.IDispatch**</span></span>|<span data-ttu-id="10ca3-129">Bir **IDispatch** arabirimi.</span><span class="sxs-lookup"><span data-stu-id="10ca3-129">An **IDispatch** interface.</span></span>|  
  
 <span data-ttu-id="10ca3-130">Aşağıdaki örnek, yönetilen arabirimi tanımını gösterir `MarshalObject`.</span><span class="sxs-lookup"><span data-stu-id="10ca3-130">The following example shows the managed interface definition for `MarshalObject`.</span></span>  
  
```vb  
Interface MarshalObject  
   Sub SetVariant(o As Object)  
   Sub SetVariantRef(ByRef o As Object)  
   Function GetVariant() As Object  
  
   Sub SetIDispatch( <MarshalAs(UnmanagedType.IDispatch)> o As Object)  
   Sub SetIDispatchRef(ByRef <MarshalAs(UnmanagedType.IDispatch)> o _  
      As Object)  
   Function GetIDispatch() As <MarshalAs(UnmanagedType.IDispatch)> Object  
   Sub SetIUnknown( <MarshalAs(UnmanagedType.IUnknown)> o As Object)  
   Sub SetIUnknownRef(ByRef <MarshalAs(UnmanagedType.IUnknown)> o _  
      As Object)  
   Function GetIUnknown() As <MarshalAs(UnmanagedType.IUnknown)> Object  
End Interface  
```  
  
```csharp  
interface MarshalObject {  
   void SetVariant(Object o);  
   void SetVariantRef(ref Object o);  
   Object GetVariant();  
  
   void SetIDispatch ([MarshalAs(UnmanagedType.IDispatch)]Object o);  
   void SetIDispatchRef([MarshalAs(UnmanagedType.IDispatch)]ref Object o);  
   [MarshalAs(UnmanagedType.IDispatch)] Object GetIDispatch();  
   void SetIUnknown ([MarshalAs(UnmanagedType.IUnknown)]Object o);  
   void SetIUnknownRef([MarshalAs(UnmanagedType.IUnknown)]ref Object o);  
   [MarshalAs(UnmanagedType.IUnknown)] Object GetIUnknown();  
}  
```  
  
 <span data-ttu-id="10ca3-131">Aşağıdaki kod dışarı aktarmaları `MarshalObject` bir tür kitaplığı için arabirim.</span><span class="sxs-lookup"><span data-stu-id="10ca3-131">The following code exports the `MarshalObject` interface to a type library.</span></span>  
  
```  
interface MarshalObject {  
   HRESULT SetVariant([in] VARIANT o);  
   HRESULT SetVariantRef([in,out] VARIANT *o);  
   HRESULT GetVariant([out,retval] VARIANT *o)   
   HRESULT SetIDispatch([in] IDispatch *o);  
   HRESULT SetIDispatchRef([in,out] IDispatch **o);  
   HRESULT GetIDispatch([out,retval] IDispatch **o)   
   HRESULT SetIUnknown([in] IUnknown *o);  
   HRESULT SetIUnknownRef([in,out] IUnknown **o);  
   HRESULT GetIUnknown([out,retval] IUnknown **o)   
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="10ca3-132">Birlikte çalışma sıralayıcısı, çağrıdan sonra ayrılan herhangi bir nesne değişkeni içinde otomatik olarak serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="10ca3-132">The interop marshaler automatically frees any allocated object inside the variant after the call.</span></span>  
  
 <span data-ttu-id="10ca3-133">Aşağıdaki örnek, biçimlendirilmiş değer türü gösterir.</span><span class="sxs-lookup"><span data-stu-id="10ca3-133">The following example shows a formatted value type.</span></span>  
  
```vb  
Public Structure ObjectHolder  
   Dim o1 As Object  
   <MarshalAs(UnmanagedType.IDispatch)> Public o2 As Object  
End Structure  
```  
  
```csharp  
public struct ObjectHolder {  
   Object o1;  
   [MarshalAs(UnmanagedType.IDispatch)]public Object o2;  
}  
```  
  
 <span data-ttu-id="10ca3-134">Aşağıdaki kod biçimlendirilmiş türü için bir tür kitaplığı dışarı aktarır.</span><span class="sxs-lookup"><span data-stu-id="10ca3-134">The following code exports the formatted type to a type library.</span></span>  
  
```  
struct ObjectHolder {  
   VARIANT o1;  
   IDispatch *o2;  
}  
```  
  
<a name="cpcondefaultmarshalingforobjectsanchor2"></a>   
## <a name="marshaling-object-to-interface"></a><span data-ttu-id="10ca3-135">Nesne arabirimi için hazırlama</span><span class="sxs-lookup"><span data-stu-id="10ca3-135">Marshaling Object to Interface</span></span>  
 <span data-ttu-id="10ca3-136">Bir nesne, COM arabirim olarak sunulduğunda, bu yönetilen türü için sınıf arabirimi arabirimidir <xref:System.Object> ( **n_esne** arabirimi).</span><span class="sxs-lookup"><span data-stu-id="10ca3-136">When an object is exposed to COM as an interface, that interface is the class interface for the managed type <xref:System.Object> (the **_Object** interface).</span></span> <span data-ttu-id="10ca3-137">Bu arabirim olarak yazılmış bir **IDispatch** (<xref:System.Runtime.InteropServices.UnmanagedType>) veya bir **IUnknown** (**UnmanagedType.IUnknown**) elde edilen tür kitaplığındaki.</span><span class="sxs-lookup"><span data-stu-id="10ca3-137">This interface is typed as an **IDispatch** (<xref:System.Runtime.InteropServices.UnmanagedType>) or an **IUnknown** (**UnmanagedType.IUnknown**) in the resulting type library.</span></span> <span data-ttu-id="10ca3-138">COM istemcileri dinamik olarak çağırmak yönetilen sınıf üyesi veya kendi türetilmiş sınıfları tarafından uygulanan herhangi bir üye **n_esne** arabirimi.</span><span class="sxs-lookup"><span data-stu-id="10ca3-138">COM clients can dynamically invoke the members of the managed class or any members implemented by its derived classes through the **_Object** interface.</span></span> <span data-ttu-id="10ca3-139">İstemci Ayrıca, çağırabilirsiniz **QueryInterface** açıkça yönetilen tür tarafından uygulanan arabirimi elde edilir.</span><span class="sxs-lookup"><span data-stu-id="10ca3-139">The client can also call **QueryInterface** to obtain any other interface explicitly implemented by the managed type.</span></span>  
  
<a name="cpcondefaultmarshalingforobjectsanchor3"></a>   
## <a name="marshaling-object-to-variant"></a><span data-ttu-id="10ca3-140">Nesne değişken için hazırlama</span><span class="sxs-lookup"><span data-stu-id="10ca3-140">Marshaling Object to Variant</span></span>  
 <span data-ttu-id="10ca3-141">İç değişken türünde bir nesne için bir değişken başvuruya çalışma zamanında, aşağıdaki kurallara göre belirlenir:</span><span class="sxs-lookup"><span data-stu-id="10ca3-141">When an object is marshaled to a variant, the internal variant type is determined at run time, based on the following rules:</span></span>  
  
-   <span data-ttu-id="10ca3-142">Nesne başvurusu null ise (**hiçbir şey** Visual Basic'te), nesne türünde bir değişken için sıralanır **VT_EMPTY**.</span><span class="sxs-lookup"><span data-stu-id="10ca3-142">If the object reference is null (**Nothing** in Visual Basic), the object is marshaled to a variant of type **VT_EMPTY**.</span></span>  
  
-   <span data-ttu-id="10ca3-143">Nesne aşağıdaki tabloda listelenen herhangi bir türde bir örnek ise, sonuçta elde edilen değişken türü Sıralayıcı içinde oluşturulan ve tabloda belirtilen kurallar tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="10ca3-143">If the object is an instance of any type listed in the following table, the resulting variant type is determined by the rules built into the marshaler and shown in the table.</span></span>  
  
-   <span data-ttu-id="10ca3-144">Hazırlama davranışı açıkça denetlemek için gereken diğer nesnelerin uygulayabilirsiniz <xref:System.IConvertible> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="10ca3-144">Other objects that need to explicitly control the marshaling behavior can implement the <xref:System.IConvertible> interface.</span></span> <span data-ttu-id="10ca3-145">Bu durumda, döndürülen tür kod değişken türü belirlenir <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="10ca3-145">In that case, the variant type is determined by the type code returned from the <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="10ca3-146">Aksi takdirde, nesne türünde bir değişken sıralanır **VT_UNKNOWN**.</span><span class="sxs-lookup"><span data-stu-id="10ca3-146">Otherwise, the object is marshaled as a variant of type **VT_UNKNOWN**.</span></span>  
  
### <a name="marshaling-system-types-to-variant"></a><span data-ttu-id="10ca3-147">Değişken için sistem türlerini hazırlama</span><span class="sxs-lookup"><span data-stu-id="10ca3-147">Marshaling System Types to Variant</span></span>  
 <span data-ttu-id="10ca3-148">Aşağıdaki tabloda, yönetilen nesne türlerini ve bunların karşılık gelen COM değişken türlerine gösterir.</span><span class="sxs-lookup"><span data-stu-id="10ca3-148">The following table shows managed object types and their corresponding COM variant types.</span></span> <span data-ttu-id="10ca3-149">Çağrılan yöntem imzası türü olduğunda, bu tür dönüştürülür <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="10ca3-149">These types are converted only when the signature of the method being called is of type <xref:System.Object?displayProperty=nameWithType>.</span></span>  
  
|<span data-ttu-id="10ca3-150">Nesne türü</span><span class="sxs-lookup"><span data-stu-id="10ca3-150">Object type</span></span>|<span data-ttu-id="10ca3-151">COM değişken türü</span><span class="sxs-lookup"><span data-stu-id="10ca3-151">COM variant type</span></span>|  
|-----------------|----------------------|  
|<span data-ttu-id="10ca3-152">Null Nesne başvurusu (**hiçbir şey** Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="10ca3-152">Null object reference (**Nothing** in Visual Basic).</span></span>|<span data-ttu-id="10ca3-153">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="10ca3-153">**VT_EMPTY**</span></span>|  
|<xref:System.DBNull?displayProperty=nameWithType>|<span data-ttu-id="10ca3-154">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="10ca3-154">**VT_NULL**</span></span>|  
|<xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>|<span data-ttu-id="10ca3-155">**VT_ERROR**</span><span class="sxs-lookup"><span data-stu-id="10ca3-155">**VT_ERROR**</span></span>|  
|<xref:System.Reflection.Missing?displayProperty=nameWithType>|<span data-ttu-id="10ca3-156">**VT_ERROR** ile **E_PARAMNOTFOUND**</span><span class="sxs-lookup"><span data-stu-id="10ca3-156">**VT_ERROR** with **E_PARAMNOTFOUND**</span></span>|  
|<xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>|<span data-ttu-id="10ca3-157">**VT_DISPATCH**</span><span class="sxs-lookup"><span data-stu-id="10ca3-157">**VT_DISPATCH**</span></span>|  
|<xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>|<span data-ttu-id="10ca3-158">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="10ca3-158">**VT_UNKNOWN**</span></span>|  
|<xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>|<span data-ttu-id="10ca3-159">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="10ca3-159">**VT_CY**</span></span>|  
|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="10ca3-160">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="10ca3-160">**VT_BOOL**</span></span>|  
|<xref:System.SByte?displayProperty=nameWithType>|<span data-ttu-id="10ca3-161">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="10ca3-161">**VT_I1**</span></span>|  
|<xref:System.Byte?displayProperty=nameWithType>|<span data-ttu-id="10ca3-162">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="10ca3-162">**VT_UI1**</span></span>|  
|<xref:System.Int16?displayProperty=nameWithType>|<span data-ttu-id="10ca3-163">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="10ca3-163">**VT_I2**</span></span>|  
|<xref:System.UInt16?displayProperty=nameWithType>|<span data-ttu-id="10ca3-164">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="10ca3-164">**VT_UI2**</span></span>|  
|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="10ca3-165">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="10ca3-165">**VT_I4**</span></span>|  
|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="10ca3-166">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="10ca3-166">**VT_UI4**</span></span>|  
|<xref:System.Int64?displayProperty=nameWithType>|<span data-ttu-id="10ca3-167">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="10ca3-167">**VT_I8**</span></span>|  
|<xref:System.UInt64?displayProperty=nameWithType>|<span data-ttu-id="10ca3-168">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="10ca3-168">**VT_UI8**</span></span>|  
|<xref:System.Single?displayProperty=nameWithType>|<span data-ttu-id="10ca3-169">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="10ca3-169">**VT_R4**</span></span>|  
|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="10ca3-170">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="10ca3-170">**VT_R8**</span></span>|  
|<xref:System.Decimal?displayProperty=nameWithType>|<span data-ttu-id="10ca3-171">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="10ca3-171">**VT_DECIMAL**</span></span>|  
|<xref:System.DateTime?displayProperty=nameWithType>|<span data-ttu-id="10ca3-172">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="10ca3-172">**VT_DATE**</span></span>|  
|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="10ca3-173">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="10ca3-173">**VT_BSTR**</span></span>|  
|<xref:System.IntPtr?displayProperty=nameWithType>|<span data-ttu-id="10ca3-174">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="10ca3-174">**VT_INT**</span></span>|  
|<xref:System.UIntPtr?displayProperty=nameWithType>|<span data-ttu-id="10ca3-175">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="10ca3-175">**VT_UINT**</span></span>|  
|<xref:System.Array?displayProperty=nameWithType>|<span data-ttu-id="10ca3-176">**VT_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="10ca3-176">**VT_ARRAY**</span></span>|  
  
 <span data-ttu-id="10ca3-177">Kullanarak `MarshalObject` önceki örnekte, aşağıdaki kod örneğinde tanımlanan arabirimi çeşitleri çeşitli türlerdeki bir COM sunucuya geçirmek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="10ca3-177">Using the `MarshalObject` interface defined in the previous example, the following code example demonstrates how to pass various types of variants to a COM server.</span></span>  
  
```vb  
Dim mo As New MarshalObject()  
mo.SetVariant(Nothing)         ' Marshal as variant of type VT_EMPTY.  
mo.SetVariant(System.DBNull.Value) ' Marshal as variant of type VT_NULL.  
mo.SetVariant(CInt(27))        ' Marshal as variant of type VT_I2.  
mo.SetVariant(CLng(27))        ' Marshal as variant of type VT_I4.  
mo.SetVariant(CSng(27.0))      ' Marshal as variant of type VT_R4.  
mo.SetVariant(CDbl(27.0))      ' Marshal as variant of type VT_R8.  
```  
  
```csharp  
MarshalObject mo = new MarshalObject();  
mo.SetVariant(null);            // Marshal as variant of type VT_EMPTY.  
mo.SetVariant(System.DBNull.Value); // Marshal as variant of type VT_NULL.  
mo.SetVariant((int)27);          // Marshal as variant of type VT_I2.  
mo.SetVariant((long)27);          // Marshal as variant of type VT_I4.  
mo.SetVariant((single)27.0);   // Marshal as variant of type VT_R4.  
mo.SetVariant((double)27.0);   // Marshal as variant of type VT_R8.  
```  
  
 <span data-ttu-id="10ca3-178">Karşılık gelen yönetilen türleri COM türleri sıralanmış sarmalayıcı sınıflar gibi kullanarak <xref:System.Runtime.InteropServices.ErrorWrapper>, <xref:System.Runtime.InteropServices.DispatchWrapper>, <xref:System.Runtime.InteropServices.UnknownWrapper>, ve <xref:System.Runtime.InteropServices.CurrencyWrapper>.</span><span class="sxs-lookup"><span data-stu-id="10ca3-178">COM types that do not have corresponding managed types can be marshaled using wrapper classes such as <xref:System.Runtime.InteropServices.ErrorWrapper>, <xref:System.Runtime.InteropServices.DispatchWrapper>, <xref:System.Runtime.InteropServices.UnknownWrapper>, and <xref:System.Runtime.InteropServices.CurrencyWrapper>.</span></span> <span data-ttu-id="10ca3-179">Aşağıdaki kod örneği, bu sarmalayıcılar çeşitleri çeşitli türlerdeki bir COM sunucuya geçirmek için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="10ca3-179">The following code example demonstrates how to use these wrappers to pass various types of variants to a COM server.</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
' Pass inew as a variant of type VT_UNKNOWN interface.  
mo.SetVariant(New UnknownWrapper(inew))  
' Pass inew as a variant of type VT_DISPATCH interface.  
mo.SetVariant(New DispatchWrapper(inew))  
' Pass a value as a variant of type VT_ERROR interface.  
mo.SetVariant(New ErrorWrapper(&H80054002))  
' Pass a value as a variant of type VT_CURRENCY interface.  
mo.SetVariant(New CurrencyWrapper(New Decimal(5.25)))  
```  
  
```csharp  
using System.Runtime.InteropServices;  
// Pass inew as a variant of type VT_UNKNOWN interface.  
mo.SetVariant(new UnknownWrapper(inew));  
// Pass inew as a variant of type VT_DISPATCH interface.  
mo.SetVariant(new DispatchWrapper(inew));  
// Pass a value as a variant of type VT_ERROR interface.  
mo.SetVariant(new ErrorWrapper(0x80054002));  
// Pass a value as a variant of type VT_CURRENCY interface.  
mo.SetVariant(new CurrencyWrapper(new Decimal(5.25)));  
```  
  
 <span data-ttu-id="10ca3-180">Sarmalayıcı sınıflar tanımlanan <xref:System.Runtime.InteropServices> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="10ca3-180">The wrapper classes are defined in the <xref:System.Runtime.InteropServices> namespace.</span></span>  
  
### <a name="marshaling-the-iconvertible-interface-to-variant"></a><span data-ttu-id="10ca3-181">IConvertible arabirimi değişken için hazırlama</span><span class="sxs-lookup"><span data-stu-id="10ca3-181">Marshaling the IConvertible Interface to Variant</span></span>  
 <span data-ttu-id="10ca3-182">Önceki bölümde listelenen nasıl bunlar uygulayarak sıralanmış denetleyebilirsiniz daha diğer türleri <xref:System.IConvertible> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="10ca3-182">Types other than those listed in the previous section can control how they are marshaled by implementing the <xref:System.IConvertible> interface.</span></span> <span data-ttu-id="10ca3-183">Nesne uyguluyorsa **IConvertible** arabirimi, COM değişken türü, çalışma zamanında değeri tarafından belirlenir <xref:System.TypeCode> döndürüldüğü numaralandırma <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="10ca3-183">If the object implements the **IConvertible** interface, the COM variant type is determined at run time by the value of the <xref:System.TypeCode> enumeration returned from the <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="10ca3-184">İçin olası değerler aşağıdaki tabloda gösterilmektedir **TypeCode** sabit listesi ve her bir değer için karşılık gelen COM değişken türü.</span><span class="sxs-lookup"><span data-stu-id="10ca3-184">The following table shows the possible values for the **TypeCode** enumeration and the corresponding COM variant type for each value.</span></span>  
  
|<span data-ttu-id="10ca3-185">Typecode'u işlenemiyor</span><span class="sxs-lookup"><span data-stu-id="10ca3-185">TypeCode</span></span>|<span data-ttu-id="10ca3-186">COM değişken türü</span><span class="sxs-lookup"><span data-stu-id="10ca3-186">COM variant type</span></span>|  
|--------------|----------------------|  
|<span data-ttu-id="10ca3-187">**TypeCode.Empty**</span><span class="sxs-lookup"><span data-stu-id="10ca3-187">**TypeCode.Empty**</span></span>|<span data-ttu-id="10ca3-188">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="10ca3-188">**VT_EMPTY**</span></span>|  
|<span data-ttu-id="10ca3-189">**TypeCode.Object**</span><span class="sxs-lookup"><span data-stu-id="10ca3-189">**TypeCode.Object**</span></span>|<span data-ttu-id="10ca3-190">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="10ca3-190">**VT_UNKNOWN**</span></span>|  
|<span data-ttu-id="10ca3-191">**TypeCode.DBNull**</span><span class="sxs-lookup"><span data-stu-id="10ca3-191">**TypeCode.DBNull**</span></span>|<span data-ttu-id="10ca3-192">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="10ca3-192">**VT_NULL**</span></span>|  
|<span data-ttu-id="10ca3-193">**TypeCode.Boolean**</span><span class="sxs-lookup"><span data-stu-id="10ca3-193">**TypeCode.Boolean**</span></span>|<span data-ttu-id="10ca3-194">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="10ca3-194">**VT_BOOL**</span></span>|  
|<span data-ttu-id="10ca3-195">**TypeCode.Char**</span><span class="sxs-lookup"><span data-stu-id="10ca3-195">**TypeCode.Char**</span></span>|<span data-ttu-id="10ca3-196">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="10ca3-196">**VT_UI2**</span></span>|  
|<span data-ttu-id="10ca3-197">**TypeCode.Sbyte**</span><span class="sxs-lookup"><span data-stu-id="10ca3-197">**TypeCode.Sbyte**</span></span>|<span data-ttu-id="10ca3-198">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="10ca3-198">**VT_I1**</span></span>|  
|<span data-ttu-id="10ca3-199">**TypeCode.Byte**</span><span class="sxs-lookup"><span data-stu-id="10ca3-199">**TypeCode.Byte**</span></span>|<span data-ttu-id="10ca3-200">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="10ca3-200">**VT_UI1**</span></span>|  
|<span data-ttu-id="10ca3-201">**TypeCode.Int16**</span><span class="sxs-lookup"><span data-stu-id="10ca3-201">**TypeCode.Int16**</span></span>|<span data-ttu-id="10ca3-202">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="10ca3-202">**VT_I2**</span></span>|  
|<span data-ttu-id="10ca3-203">**TypeCode.UInt16**</span><span class="sxs-lookup"><span data-stu-id="10ca3-203">**TypeCode.UInt16**</span></span>|<span data-ttu-id="10ca3-204">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="10ca3-204">**VT_UI2**</span></span>|  
|<span data-ttu-id="10ca3-205">**TypeCode.Int32**</span><span class="sxs-lookup"><span data-stu-id="10ca3-205">**TypeCode.Int32**</span></span>|<span data-ttu-id="10ca3-206">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="10ca3-206">**VT_I4**</span></span>|  
|<span data-ttu-id="10ca3-207">**TypeCode.UInt32**</span><span class="sxs-lookup"><span data-stu-id="10ca3-207">**TypeCode.UInt32**</span></span>|<span data-ttu-id="10ca3-208">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="10ca3-208">**VT_UI4**</span></span>|  
|<span data-ttu-id="10ca3-209">**TypeCode.Int64**</span><span class="sxs-lookup"><span data-stu-id="10ca3-209">**TypeCode.Int64**</span></span>|<span data-ttu-id="10ca3-210">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="10ca3-210">**VT_I8**</span></span>|  
|<span data-ttu-id="10ca3-211">**TypeCode.UInt64**</span><span class="sxs-lookup"><span data-stu-id="10ca3-211">**TypeCode.UInt64**</span></span>|<span data-ttu-id="10ca3-212">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="10ca3-212">**VT_UI8**</span></span>|  
|<span data-ttu-id="10ca3-213">**TypeCode.Single**</span><span class="sxs-lookup"><span data-stu-id="10ca3-213">**TypeCode.Single**</span></span>|<span data-ttu-id="10ca3-214">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="10ca3-214">**VT_R4**</span></span>|  
|<span data-ttu-id="10ca3-215">**TypeCode.Double**</span><span class="sxs-lookup"><span data-stu-id="10ca3-215">**TypeCode.Double**</span></span>|<span data-ttu-id="10ca3-216">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="10ca3-216">**VT_R8**</span></span>|  
|<span data-ttu-id="10ca3-217">**TypeCode.Decimal**</span><span class="sxs-lookup"><span data-stu-id="10ca3-217">**TypeCode.Decimal**</span></span>|<span data-ttu-id="10ca3-218">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="10ca3-218">**VT_DECIMAL**</span></span>|  
|<span data-ttu-id="10ca3-219">**TypeCode.DateTime**</span><span class="sxs-lookup"><span data-stu-id="10ca3-219">**TypeCode.DateTime**</span></span>|<span data-ttu-id="10ca3-220">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="10ca3-220">**VT_DATE**</span></span>|  
|<span data-ttu-id="10ca3-221">**TypeCode.String**</span><span class="sxs-lookup"><span data-stu-id="10ca3-221">**TypeCode.String**</span></span>|<span data-ttu-id="10ca3-222">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="10ca3-222">**VT_BSTR**</span></span>|  
|<span data-ttu-id="10ca3-223">Desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="10ca3-223">Not supported.</span></span>|<span data-ttu-id="10ca3-224">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="10ca3-224">**VT_INT**</span></span>|  
|<span data-ttu-id="10ca3-225">Desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="10ca3-225">Not supported.</span></span>|<span data-ttu-id="10ca3-226">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="10ca3-226">**VT_UINT**</span></span>|  
|<span data-ttu-id="10ca3-227">Desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="10ca3-227">Not supported.</span></span>|<span data-ttu-id="10ca3-228">**VT_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="10ca3-228">**VT_ARRAY**</span></span>|  
|<span data-ttu-id="10ca3-229">Desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="10ca3-229">Not supported.</span></span>|<span data-ttu-id="10ca3-230">**VT_RECORD**</span><span class="sxs-lookup"><span data-stu-id="10ca3-230">**VT_RECORD**</span></span>|  
|<span data-ttu-id="10ca3-231">Desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="10ca3-231">Not supported.</span></span>|<span data-ttu-id="10ca3-232">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="10ca3-232">**VT_CY**</span></span>|  
|<span data-ttu-id="10ca3-233">Desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="10ca3-233">Not supported.</span></span>|<span data-ttu-id="10ca3-234">**VT_VARIANT**</span><span class="sxs-lookup"><span data-stu-id="10ca3-234">**VT_VARIANT**</span></span>|  
  
 <span data-ttu-id="10ca3-235">COM değişken değerini çağırarak belirlenir **IConvertible.To** *türü* arabirimi, burada **için** *türü* dönüştürme öğesinden döndürülen türüne karşılık gelen yordamı **IConvertible.GetTypeCode**.</span><span class="sxs-lookup"><span data-stu-id="10ca3-235">The value of the COM variant is determined by calling the **IConvertible.To** *Type* interface, where **To** *Type* is the conversion routine that corresponds to the type that was returned from **IConvertible.GetTypeCode**.</span></span> <span data-ttu-id="10ca3-236">Örneğin, döndüren bir nesne **TypeCode.Double** gelen **IConvertible.GetTypeCode** COM türünde sıralanmış **VT_R8**.</span><span class="sxs-lookup"><span data-stu-id="10ca3-236">For example, an object that returns **TypeCode.Double** from **IConvertible.GetTypeCode** is marshaled as a COM variant of type **VT_R8**.</span></span> <span data-ttu-id="10ca3-237">Değişken değeri elde edebilirsiniz (depolanan **dblVal** COM değişkeni alan) tarafından atamayı **IConvertible** arabirimi ve arama <xref:System.IConvertible.ToDouble%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="10ca3-237">You can obtain the value of the variant (stored in the **dblVal** field of the COM variant) by casting to the **IConvertible** interface and calling the <xref:System.IConvertible.ToDouble%2A> method.</span></span>  
  
<a name="cpcondefaultmarshalingforobjectsanchor4"></a>   
## <a name="marshaling-variant-to-object"></a><span data-ttu-id="10ca3-238">VARIANT nesnesi için hazırlama</span><span class="sxs-lookup"><span data-stu-id="10ca3-238">Marshaling Variant to Object</span></span>  
 <span data-ttu-id="10ca3-239">Üretilen ne zaman bir nesne, türü ve bazen değerini sıralanmış değişken için bir VARIANT'ı hazırlama nesne türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="10ca3-239">When marshaling a variant to an object, the type, and sometimes the value, of the marshaled variant determines the type of object produced.</span></span> <span data-ttu-id="10ca3-240">Aşağıdaki tabloda her değişken türünde bir değişken COM'dan .NET Framework geçirildiğinde Sıralayıcı oluşturur karşılık gelen nesne türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="10ca3-240">The following table identifies each variant type and the corresponding object type that the marshaler creates when a variant is passed from COM to the .NET Framework.</span></span>  
  
|<span data-ttu-id="10ca3-241">COM değişken türü</span><span class="sxs-lookup"><span data-stu-id="10ca3-241">COM variant type</span></span>|<span data-ttu-id="10ca3-242">Nesne türü</span><span class="sxs-lookup"><span data-stu-id="10ca3-242">Object type</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="10ca3-243">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="10ca3-243">**VT_EMPTY**</span></span>|<span data-ttu-id="10ca3-244">Null Nesne başvurusu (**hiçbir şey** Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="10ca3-244">Null object reference (**Nothing** in Visual Basic).</span></span>|  
|<span data-ttu-id="10ca3-245">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="10ca3-245">**VT_NULL**</span></span>|<xref:System.DBNull?displayProperty=nameWithType>|  
|<span data-ttu-id="10ca3-246">**VT_DISPATCH**</span><span class="sxs-lookup"><span data-stu-id="10ca3-246">**VT_DISPATCH**</span></span>|<span data-ttu-id="10ca3-247">**System.comobject'e** veya null ise (pdispVal == null)</span><span class="sxs-lookup"><span data-stu-id="10ca3-247">**System.__ComObject** or null if (pdispVal == null)</span></span>|  
|<span data-ttu-id="10ca3-248">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="10ca3-248">**VT_UNKNOWN**</span></span>|<span data-ttu-id="10ca3-249">**System.comobject'e** veya null ise (punkVal == null)</span><span class="sxs-lookup"><span data-stu-id="10ca3-249">**System.__ComObject** or null if (punkVal == null)</span></span>|  
|<span data-ttu-id="10ca3-250">**VT_ERROR**</span><span class="sxs-lookup"><span data-stu-id="10ca3-250">**VT_ERROR**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|  
|<span data-ttu-id="10ca3-251">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="10ca3-251">**VT_BOOL**</span></span>|<xref:System.Boolean?displayProperty=nameWithType>|  
|<span data-ttu-id="10ca3-252">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="10ca3-252">**VT_I1**</span></span>|<xref:System.SByte?displayProperty=nameWithType>|  
|<span data-ttu-id="10ca3-253">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="10ca3-253">**VT_UI1**</span></span>|<xref:System.Byte?displayProperty=nameWithType>|  
|<span data-ttu-id="10ca3-254">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="10ca3-254">**VT_I2**</span></span>|<xref:System.Int16?displayProperty=nameWithType>|  
|<span data-ttu-id="10ca3-255">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="10ca3-255">**VT_UI2**</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|  
|<span data-ttu-id="10ca3-256">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="10ca3-256">**VT_I4**</span></span>|<xref:System.Int32?displayProperty=nameWithType>|  
|<span data-ttu-id="10ca3-257">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="10ca3-257">**VT_UI4**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|  
|<span data-ttu-id="10ca3-258">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="10ca3-258">**VT_I8**</span></span>|<xref:System.Int64?displayProperty=nameWithType>|  
|<span data-ttu-id="10ca3-259">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="10ca3-259">**VT_UI8**</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|  
|<span data-ttu-id="10ca3-260">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="10ca3-260">**VT_R4**</span></span>|<xref:System.Single?displayProperty=nameWithType>|  
|<span data-ttu-id="10ca3-261">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="10ca3-261">**VT_R8**</span></span>|<xref:System.Double?displayProperty=nameWithType>|  
|<span data-ttu-id="10ca3-262">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="10ca3-262">**VT_DECIMAL**</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|  
|<span data-ttu-id="10ca3-263">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="10ca3-263">**VT_DATE**</span></span>|<xref:System.DateTime?displayProperty=nameWithType>|  
|<span data-ttu-id="10ca3-264">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="10ca3-264">**VT_BSTR**</span></span>|<xref:System.String?displayProperty=nameWithType>|  
|<span data-ttu-id="10ca3-265">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="10ca3-265">**VT_INT**</span></span>|<xref:System.Int32?displayProperty=nameWithType>|  
|<span data-ttu-id="10ca3-266">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="10ca3-266">**VT_UINT**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|  
|<span data-ttu-id="10ca3-267">**VT_ARRAY** &#124; **VT_**\*</span><span class="sxs-lookup"><span data-stu-id="10ca3-267">**VT_ARRAY** &#124; **VT_**\*</span></span>|<xref:System.Array?displayProperty=nameWithType>|  
|<span data-ttu-id="10ca3-268">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="10ca3-268">**VT_CY**</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|  
|<span data-ttu-id="10ca3-269">**VT_RECORD**</span><span class="sxs-lookup"><span data-stu-id="10ca3-269">**VT_RECORD**</span></span>|<span data-ttu-id="10ca3-270">Paketlenmiş değer türü karşılık gelen.</span><span class="sxs-lookup"><span data-stu-id="10ca3-270">Corresponding boxed value type.</span></span>|  
|<span data-ttu-id="10ca3-271">**VT_VARIANT**</span><span class="sxs-lookup"><span data-stu-id="10ca3-271">**VT_VARIANT**</span></span>|<span data-ttu-id="10ca3-272">Desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="10ca3-272">Not supported.</span></span>|  
  
 <span data-ttu-id="10ca3-273">Değişken türleri için COM'dan geçirilen yönetilen kod ve daha sonra geri COM için aynı değişken türünde çağrı süresi boyunca koruyamayabilir.</span><span class="sxs-lookup"><span data-stu-id="10ca3-273">Variant types passed from COM to managed code and then back to COM might not retain the same variant type for the duration of the call.</span></span> <span data-ttu-id="10ca3-274">Türünde bir değişken olduğunda ne olacağını düşünün **gt; vt_dıspatch &** COM'dan .NET Framework geçirilir.</span><span class="sxs-lookup"><span data-stu-id="10ca3-274">Consider what happens when a variant of type **VT_DISPATCH** is passed from COM to the .NET Framework.</span></span> <span data-ttu-id="10ca3-275">Hazırlama sırasında değişken dönüştürülür bir <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="10ca3-275">During marshaling, the variant is converted to a <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="10ca3-276">Varsa **nesne** ardından geçirilen geri COM için geri türünde bir değişken için sıralanır **VT_UNKNOWN**.</span><span class="sxs-lookup"><span data-stu-id="10ca3-276">If the **Object** is then passed back to COM, it is marshaled back to a variant of type **VT_UNKNOWN**.</span></span> <span data-ttu-id="10ca3-277">Başlangıçta nesne oluşturmak için kullanılan bir değişken aynı türde bir nesne için COM yönetilen koddan başvuruya üretilen değişken olacağını garanti yoktur.</span><span class="sxs-lookup"><span data-stu-id="10ca3-277">There is no guarantee that the variant produced when an object is marshaled from managed code to COM will be the same type as the variant initially used to produce the object.</span></span>  
  
<a name="cpcondefaultmarshalingforobjectsanchor6"></a>   
## <a name="marshaling-byref-variants"></a><span data-ttu-id="10ca3-278">ByRef çeşitleri hazırlama</span><span class="sxs-lookup"><span data-stu-id="10ca3-278">Marshaling ByRef Variants</span></span>  
 <span data-ttu-id="10ca3-279">Değere veya başvuruya göre çeşitleri kendilerini geçirilebilir ancak **VT_BYREF** bayrağı de kullanılabilir herhangi bir değişken türü değişken içeriğini yerine başvuruya göre geçirilen belirtmek için değere göre.</span><span class="sxs-lookup"><span data-stu-id="10ca3-279">Although variants themselves can be passed by value or by reference, the **VT_BYREF** flag can also be used with any variant type to indicate that the contents of the variant are being passed by reference instead of by value.</span></span> <span data-ttu-id="10ca3-280">Çeşitleri başvuruya göre sıralama ve bir değişken ile hazırlama arasındaki farkı **VT_BYREF** bayrağı kafa karıştırıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="10ca3-280">The difference between marshaling variants by reference and marshaling a variant with the **VT_BYREF** flag set can be confusing.</span></span> <span data-ttu-id="10ca3-281">Aşağıdaki çizim farkları açıklar.</span><span class="sxs-lookup"><span data-stu-id="10ca3-281">The following illustration clarifies the differences.</span></span>  
  
 <span data-ttu-id="10ca3-282">![Değişken Kalanlar yığın üzerinde](./media/interopvariant.gif "interopvariant")</span><span class="sxs-lookup"><span data-stu-id="10ca3-282">![Variant passed on the stack](./media/interopvariant.gif "interopvariant")</span></span>  
<span data-ttu-id="10ca3-283">Değere ve başvuruya göre geçirilen çeşitleri</span><span class="sxs-lookup"><span data-stu-id="10ca3-283">Variants passed by value and by reference</span></span>  
  
 <span data-ttu-id="10ca3-284">**Nesneleri ve değişkenleri değere göre sıralama için varsayılan davranış**</span><span class="sxs-lookup"><span data-stu-id="10ca3-284">**Default behavior for marshaling objects and variants by value**</span></span>  
  
-   <span data-ttu-id="10ca3-285">Nesneleri, COM yönetilen koddan geçirirken, nesnenin içeriğini tanımlanan kuralların kullanarak sıralayıcı tarafından oluşturulan yeni bir değişken içine kopyalanır [değişken hazırlama nesnesine](#cpcondefaultmarshalingforobjectsanchor3).</span><span class="sxs-lookup"><span data-stu-id="10ca3-285">When passing objects from managed code to COM, the contents of the object are copied into a new variant created by the marshaler, using the rules defined in [Marshaling Object to Variant](#cpcondefaultmarshalingforobjectsanchor3).</span></span> <span data-ttu-id="10ca3-286">Yönetilmeyen tarafında değişken yapılan değişiklikleri çağrısından dönüşte özgün nesneye geri yayılmaz.</span><span class="sxs-lookup"><span data-stu-id="10ca3-286">Changes made to the variant on the unmanaged side are not propagated back to the original object on return from the call.</span></span>  
  
-   <span data-ttu-id="10ca3-287">Çeşitleri için yönetilen kod COM'dan geçirirken, değişken içeriğini tanımlanan kuralların kullanarak yeni oluşturulan bir nesneye kopyalanır [hazırlama değişken nesneye](#cpcondefaultmarshalingforobjectsanchor4).</span><span class="sxs-lookup"><span data-stu-id="10ca3-287">When passing variants from COM to managed code, the contents of the variant are copied to a newly created object, using the rules defined in [Marshaling Variant to Object](#cpcondefaultmarshalingforobjectsanchor4).</span></span> <span data-ttu-id="10ca3-288">Yönetilen tarafında nesneye yapılan değişiklikleri geri çağrısından dönüşte özgün değişken için yayılmaz.</span><span class="sxs-lookup"><span data-stu-id="10ca3-288">Changes made to the object on the managed side are not propagated back to the original variant on return from the call.</span></span>  
  
 <span data-ttu-id="10ca3-289">**Nesneleri ve değişkenleri başvuruya göre hazırlama için varsayılan davranış**</span><span class="sxs-lookup"><span data-stu-id="10ca3-289">**Default behavior for marshaling objects and variants by reference**</span></span>  
  
 <span data-ttu-id="10ca3-290">Değişiklikleri tekrar çağırana yayılmasına parametreleri başvuruya göre geçirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="10ca3-290">To propagate changes back to the caller, the parameters must be passed by reference.</span></span> <span data-ttu-id="10ca3-291">Örneğin, kullanabilirsiniz **ref** anahtar sözcüğünü C# (veya **ByRef** yönetilen kod Visual Basic) başvuru ile parametreleri iletme.</span><span class="sxs-lookup"><span data-stu-id="10ca3-291">For example, you can use the **ref** keyword in C# (or **ByRef** in Visual Basic managed code) to pass parameters by reference.</span></span> <span data-ttu-id="10ca3-292">COM, başvuru parametreleri gibi bir işaretçi kullanılarak geçirilen bir **değişken \*** .</span><span class="sxs-lookup"><span data-stu-id="10ca3-292">In COM, reference parameters are passed using a pointer such as a **variant \***.</span></span>  
  
-   <span data-ttu-id="10ca3-293">Bir nesne için COM başvuruya göre geçirme, Sıralayıcı yeni bir değişken oluşturur ve çağrı yapılmadan önce değişken bir nesne başvurusu içeriğini kopyalar.</span><span class="sxs-lookup"><span data-stu-id="10ca3-293">When passing an object to COM by reference, the marshaler creates a new variant and copies the contents of the object reference into the variant before the call is made.</span></span> <span data-ttu-id="10ca3-294">Değişken, kullanıcının değişken içeriğini değiştirmek ücretsiz olduğu yönetilmeyen işleve geçirilir.</span><span class="sxs-lookup"><span data-stu-id="10ca3-294">The variant is passed to the unmanaged function where the user is free to change the contents of the variant.</span></span> <span data-ttu-id="10ca3-295">Geri çağrısından, yönetilmeyen tarafında değişken yapılan tüm değişiklikler özgün nesneye geri yayılır.</span><span class="sxs-lookup"><span data-stu-id="10ca3-295">On return from the call, any changes made to the variant on the unmanaged side are propagated back to the original object.</span></span> <span data-ttu-id="10ca3-296">Ardından bir çağrısına geçirilen değişken türünde bir değişken türünde farklıdır, değişiklikleri geri farklı türde bir nesne için yayılır.</span><span class="sxs-lookup"><span data-stu-id="10ca3-296">If the type of the variant differs from the type of the variant passed to the call, then the changes are propagated back to an object of a different type.</span></span> <span data-ttu-id="10ca3-297">Diğer bir deyişle, çağrısına geçirilen nesne türü çağrısından döndürülen nesnenin türü farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="10ca3-297">That is, the type of the object passed into the call can differ from the type of the object returned from the call.</span></span>  
  
-   <span data-ttu-id="10ca3-298">Bir değişken başvuru ile yönetilen kod için geçirirken, Sıralayıcı yeni bir nesne oluşturur ve çağrı yapmadan önce değişken içeriğini nesnesine kopyalar.</span><span class="sxs-lookup"><span data-stu-id="10ca3-298">When passing a variant to managed code by reference, the marshaler creates a new object and copies the contents of the variant into the object before making the call.</span></span> <span data-ttu-id="10ca3-299">Nesnesine bir başvuru, kullanıcının bir nesneyi değiştirmek ücretsiz olduğu yönetilen bir işleve geçirilir.</span><span class="sxs-lookup"><span data-stu-id="10ca3-299">A reference to the object is passed to the managed function, where the user is free to change the object.</span></span> <span data-ttu-id="10ca3-300">Geri çağrısından, başvurulan nesneye yapılan tüm değişiklikler özgün değişkenine geri yayılır.</span><span class="sxs-lookup"><span data-stu-id="10ca3-300">On return from the call, any changes made to the referenced object are propagated back to the original variant.</span></span> <span data-ttu-id="10ca3-301">Nesne türü çağrısına geçirilen nesnenin türü farklı olması durumunda, özgün değişken türü değiştirilir ve değeri değişken geri yayılır.</span><span class="sxs-lookup"><span data-stu-id="10ca3-301">If the type of the object differs from the type of the object passed in to the call, the type of the original variant is changed and the value is propagated back into the variant.</span></span> <span data-ttu-id="10ca3-302">Yeniden çağrısına geçirilen değişken türünü çağrısından döndürülen değişken türünden farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="10ca3-302">Again, the type of the variant passed into the call can differ from the type of the variant returned from the call.</span></span>  
  
 <span data-ttu-id="10ca3-303">**Bir değişken VT_BYREF bayrağı ayarlanmış hazırlama için varsayılan davranış**</span><span class="sxs-lookup"><span data-stu-id="10ca3-303">**Default behavior for marshaling a variant with the VT_BYREF flag set**</span></span>  
  
-   <span data-ttu-id="10ca3-304">Yönetilen kod için değere göre geçirilen bir değişken olabilir **VT_BYREF** bayrağı ayarlanmış değişken bir değer yerine bir başvuru içerdiğini belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="10ca3-304">A variant being passed to managed code by value can have the **VT_BYREF** flag set to indicate that the variant contains a reference instead of a value.</span></span> <span data-ttu-id="10ca3-305">Bu durumda, değişken değer olarak geçilemez çünkü değişken hala bir nesneye sıralanır.</span><span class="sxs-lookup"><span data-stu-id="10ca3-305">In this case, the variant is still marshaled to an object because the variant is being passed by value.</span></span> <span data-ttu-id="10ca3-306">Sıralayıcı otomatik olarak başvuru varyantı içeriğini ve çağrı yapmadan önce yeni oluşturulan bir nesneye kopyalar.</span><span class="sxs-lookup"><span data-stu-id="10ca3-306">The marshaler automatically dereferences the contents of the variant and copies it into a newly created object before making the call.</span></span> <span data-ttu-id="10ca3-307">Nesne, daha sonra yönetilen işleve geçirilir; Bununla birlikte, geri çağrısından, nesneyi geri özgün değişken dağıtılmadı.</span><span class="sxs-lookup"><span data-stu-id="10ca3-307">The object is then passed into the managed function; however, on return from the call, the object is not propagated back into the original variant.</span></span> <span data-ttu-id="10ca3-308">Yönetilen nesneye yapılan değişiklikler kaybolur.</span><span class="sxs-lookup"><span data-stu-id="10ca3-308">Changes made to the managed object are lost.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="10ca3-309">Değişken olsa bile, değer olarak geçilemez bir değişken değerini değiştirmek için bir yolu yoktur **VT_BYREF** bayrağı ayarlanmış.</span><span class="sxs-lookup"><span data-stu-id="10ca3-309">There is no way to change the value of a variant passed by value, even if the variant has the **VT_BYREF** flag set.</span></span>  
  
-   <span data-ttu-id="10ca3-310">Yönetilen kod için başvuruya göre geçirilen bir değişken bulundurabilirsiniz **VT_BYREF** bayrağı ayarlanmış başka bir başvuru varyantı içerdiğini belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="10ca3-310">A variant being passed to managed code by reference can also have the **VT_BYREF** flag set to indicate that the variant contains another reference.</span></span> <span data-ttu-id="10ca3-311">Değişken sıralanmış olduğundan bulursa, bir **ref** değişken başvuruyla geçirildi çünkü nesne.</span><span class="sxs-lookup"><span data-stu-id="10ca3-311">If it does, the variant is marshaled to a **ref** object because the variant is being passed by reference.</span></span> <span data-ttu-id="10ca3-312">Sıralayıcı otomatik olarak başvuru varyantı içeriğini ve çağrı yapmadan önce yeni oluşturulan bir nesneye kopyalar.</span><span class="sxs-lookup"><span data-stu-id="10ca3-312">The marshaler automatically dereferences the contents of the variant and copies it into a newly created object before making the call.</span></span> <span data-ttu-id="10ca3-313">Geçirilen nesne olarak yalnızca nesneyi aynı türde ise geri çağrısından, nesnenin değerini geri başvuru özgün değişken içinde yayılır.</span><span class="sxs-lookup"><span data-stu-id="10ca3-313">On return from the call, the value of the object is propagated back to the reference within the original variant only if the object is the same type as the object passed in.</span></span> <span data-ttu-id="10ca3-314">Diğer bir deyişle, yayma ile bir değişken türünü değiştirmez **VT_BYREF** bayrağı ayarlanmış.</span><span class="sxs-lookup"><span data-stu-id="10ca3-314">That is, propagation does not change the type of a variant with the **VT_BYREF** flag set.</span></span> <span data-ttu-id="10ca3-315">Nesne türü aramasında değiştirilirse bir <xref:System.InvalidCastException> çağrısından dönüşte gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="10ca3-315">If the type of the object is changed during the call, an <xref:System.InvalidCastException> occurs on return from the call.</span></span>  
  
 <span data-ttu-id="10ca3-316">Aşağıdaki tabloda çeşitleri ve nesneler için yayma kuralları özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="10ca3-316">The following table summarizes the propagation rules for variants and objects.</span></span>  
  
|<span data-ttu-id="10ca3-317">Başlangıç</span><span class="sxs-lookup"><span data-stu-id="10ca3-317">From</span></span>|<span data-ttu-id="10ca3-318">Bitiş</span><span class="sxs-lookup"><span data-stu-id="10ca3-318">To</span></span>|<span data-ttu-id="10ca3-319">Değişiklikleri geri yayılmaz</span><span class="sxs-lookup"><span data-stu-id="10ca3-319">Changes propagated back</span></span>|  
|----------|--------|-----------------------------|  
|<span data-ttu-id="10ca3-320">\**Değişken\*\*\*v* </span><span class="sxs-lookup"><span data-stu-id="10ca3-320">**Variant**  *v*</span></span>|<span data-ttu-id="10ca3-321">\**Nesne\*\*\*o* </span><span class="sxs-lookup"><span data-stu-id="10ca3-321">**Object**  *o*</span></span>|<span data-ttu-id="10ca3-322">hiçbir zaman</span><span class="sxs-lookup"><span data-stu-id="10ca3-322">Never</span></span>|  
|<span data-ttu-id="10ca3-323">\**Nesne\*\*\*o* </span><span class="sxs-lookup"><span data-stu-id="10ca3-323">**Object**  *o*</span></span>|<span data-ttu-id="10ca3-324">\**Değişken\*\*\*v* </span><span class="sxs-lookup"><span data-stu-id="10ca3-324">**Variant**  *v*</span></span>|<span data-ttu-id="10ca3-325">hiçbir zaman</span><span class="sxs-lookup"><span data-stu-id="10ca3-325">Never</span></span>|  
|<span data-ttu-id="10ca3-326">\**Değişken\*\*\*\*\*\*\*\*\*\*BD* </span><span class="sxs-lookup"><span data-stu-id="10ca3-326">**Variant**   ***\****  *pv*</span></span>|<span data-ttu-id="10ca3-327">\**Ref nesne\*\*\*o* </span><span class="sxs-lookup"><span data-stu-id="10ca3-327">**Ref Object**  *o*</span></span>|<span data-ttu-id="10ca3-328">Her zaman</span><span class="sxs-lookup"><span data-stu-id="10ca3-328">Always</span></span>|  
|<span data-ttu-id="10ca3-329">\**Ref nesne\*\*\*o* </span><span class="sxs-lookup"><span data-stu-id="10ca3-329">**Ref object**  *o*</span></span>|<span data-ttu-id="10ca3-330">\**Değişken\*\*\*\*\*\*\*\*\*\*BD* </span><span class="sxs-lookup"><span data-stu-id="10ca3-330">**Variant**   ***\****  *pv*</span></span>|<span data-ttu-id="10ca3-331">Her zaman</span><span class="sxs-lookup"><span data-stu-id="10ca3-331">Always</span></span>|  
|<span data-ttu-id="10ca3-332">\**Değişken\*\*\*v* **(VT_BYREF** *&#124;* **VT_\*)** </span><span class="sxs-lookup"><span data-stu-id="10ca3-332">**Variant**  *v* **(VT_BYREF** *&#124;* **VT_\*)**</span></span>|<span data-ttu-id="10ca3-333">\**Nesne\*\*\*o* </span><span class="sxs-lookup"><span data-stu-id="10ca3-333">**Object**  *o*</span></span>|<span data-ttu-id="10ca3-334">hiçbir zaman</span><span class="sxs-lookup"><span data-stu-id="10ca3-334">Never</span></span>|  
|<span data-ttu-id="10ca3-335">\**Değişken\*\*\*v* **(VT_BYREF** *&#124;* **VT_)** </span><span class="sxs-lookup"><span data-stu-id="10ca3-335">**Variant**  *v* **(VT_BYREF** *&#124;* **VT_)**</span></span>|<span data-ttu-id="10ca3-336">\**Ref nesne\*\*\*o* </span><span class="sxs-lookup"><span data-stu-id="10ca3-336">**Ref Object**  *o*</span></span>|<span data-ttu-id="10ca3-337">Yalnızca türü değişmemişse.</span><span class="sxs-lookup"><span data-stu-id="10ca3-337">Only if the type has not changed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="10ca3-338">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="10ca3-338">See also</span></span>
- [<span data-ttu-id="10ca3-339">Varsayılan Hazırlama Davranışı</span><span class="sxs-lookup"><span data-stu-id="10ca3-339">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
- [<span data-ttu-id="10ca3-340">Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler</span><span class="sxs-lookup"><span data-stu-id="10ca3-340">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- <span data-ttu-id="10ca3-341">[Yönlü öznitelikler](https://msdn.microsoft.com/library/241ac5b5-928e-4969-8f58-1dbc048f9ea2(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="10ca3-341">[Directional Attributes](https://msdn.microsoft.com/library/241ac5b5-928e-4969-8f58-1dbc048f9ea2(v=vs.100))</span></span>
- [<span data-ttu-id="10ca3-342">Kopyalama ve Sabitleme</span><span class="sxs-lookup"><span data-stu-id="10ca3-342">Copying and Pinning</span></span>](copying-and-pinning.md)
