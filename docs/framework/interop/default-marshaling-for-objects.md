---
title: Nesneler için Varsayılan Hazırlama
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
ms.openlocfilehash: 65b13d99873fe1027d0b316d1cf90e766799dbb1
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58409282"
---
# <a name="default-marshaling-for-objects"></a><span data-ttu-id="04b0e-102">Nesneler için Varsayılan Hazırlama</span><span class="sxs-lookup"><span data-stu-id="04b0e-102">Default Marshaling for Objects</span></span>
<span data-ttu-id="04b0e-103">Parametreler ve alanlar olarak yazılan <xref:System.Object?displayProperty=nameWithType> yönetilmeyen koda aşağıdaki türlerden biri olarak kullanıma sunulabilir:</span><span class="sxs-lookup"><span data-stu-id="04b0e-103">Parameters and fields typed as <xref:System.Object?displayProperty=nameWithType> can be exposed to unmanaged code as one of the following types:</span></span>  
  
-   <span data-ttu-id="04b0e-104">Nesnesi bir parametre olduğunda bir değişken.</span><span class="sxs-lookup"><span data-stu-id="04b0e-104">A variant when the object is a parameter.</span></span>  
  
-   <span data-ttu-id="04b0e-105">Nesne yapısını alanı olduğunda bir arabirim.</span><span class="sxs-lookup"><span data-stu-id="04b0e-105">An interface when the object is a structure field.</span></span>  
  
 <span data-ttu-id="04b0e-106">Yalnızca COM birlikte çalışma hazırlama için nesne türlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="04b0e-106">Only COM interop supports marshaling for object types.</span></span> <span data-ttu-id="04b0e-107">COM çeşitleri nesnelere hazırlamak için varsayılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="04b0e-107">The default behavior is to marshal objects to COM variants.</span></span> <span data-ttu-id="04b0e-108">Bu kurallar yalnızca türü için geçerli **nesne** ve türetilen bir türü kesin olarak belirtilmiş nesneler için geçerli değildir **nesne** sınıfı.</span><span class="sxs-lookup"><span data-stu-id="04b0e-108">These rules apply only to the type **Object** and do not apply to strongly typed objects that derive from the **Object** class.</span></span>  
  
## <a name="marshaling-options"></a><span data-ttu-id="04b0e-109">Hazırlama seçenekleri</span><span class="sxs-lookup"><span data-stu-id="04b0e-109">Marshaling Options</span></span>  
 <span data-ttu-id="04b0e-110">Sıralama seçenekleri aşağıdaki tabloda gösterilmektedir **nesne** veri türü.</span><span class="sxs-lookup"><span data-stu-id="04b0e-110">The following table shows the marshaling options for the **Object** data type.</span></span> <span data-ttu-id="04b0e-111"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Özniteliği sağlayan çeşitli <xref:System.Runtime.InteropServices.UnmanagedType> numaralandırma değerleri için sıralama nesneleri.</span><span class="sxs-lookup"><span data-stu-id="04b0e-111">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal objects.</span></span>  
  
|<span data-ttu-id="04b0e-112">Numaralandırma türü</span><span class="sxs-lookup"><span data-stu-id="04b0e-112">Enumeration type</span></span>|<span data-ttu-id="04b0e-113">Yönetilmeyen biçimi açıklaması</span><span class="sxs-lookup"><span data-stu-id="04b0e-113">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|<span data-ttu-id="04b0e-114">**UnmanagedType.Struct**</span><span class="sxs-lookup"><span data-stu-id="04b0e-114">**UnmanagedType.Struct**</span></span><br /><br /> <span data-ttu-id="04b0e-115">(varsayılan parametreleri için)</span><span class="sxs-lookup"><span data-stu-id="04b0e-115">(default for parameters)</span></span>|<span data-ttu-id="04b0e-116">Bir COM Stili değişken.</span><span class="sxs-lookup"><span data-stu-id="04b0e-116">A COM-style variant.</span></span>|  
|<span data-ttu-id="04b0e-117">**UnmanagedType.Interface**</span><span class="sxs-lookup"><span data-stu-id="04b0e-117">**UnmanagedType.Interface**</span></span>|<span data-ttu-id="04b0e-118">Bir **IDispatch** arabirim, mümkünse; Aksi takdirde bir **IUnknown** arabirimi.</span><span class="sxs-lookup"><span data-stu-id="04b0e-118">An **IDispatch** interface, if possible; otherwise, an **IUnknown** interface.</span></span>|  
|<span data-ttu-id="04b0e-119">**UnmanagedType.IUnknown**</span><span class="sxs-lookup"><span data-stu-id="04b0e-119">**UnmanagedType.IUnknown**</span></span><br /><br /> <span data-ttu-id="04b0e-120">(alanlar için varsayılan)</span><span class="sxs-lookup"><span data-stu-id="04b0e-120">(default for fields)</span></span>|<span data-ttu-id="04b0e-121">Bir **IUnknown** arabirimi.</span><span class="sxs-lookup"><span data-stu-id="04b0e-121">An **IUnknown** interface.</span></span>|  
|<span data-ttu-id="04b0e-122">**UnmanagedType.IDispatch**</span><span class="sxs-lookup"><span data-stu-id="04b0e-122">**UnmanagedType.IDispatch**</span></span>|<span data-ttu-id="04b0e-123">Bir **IDispatch** arabirimi.</span><span class="sxs-lookup"><span data-stu-id="04b0e-123">An **IDispatch** interface.</span></span>|  
  
 <span data-ttu-id="04b0e-124">Aşağıdaki örnek, yönetilen arabirimi tanımını gösterir `MarshalObject`.</span><span class="sxs-lookup"><span data-stu-id="04b0e-124">The following example shows the managed interface definition for `MarshalObject`.</span></span>  
  
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
  
 <span data-ttu-id="04b0e-125">Aşağıdaki kod dışarı aktarmaları `MarshalObject` bir tür kitaplığı için arabirim.</span><span class="sxs-lookup"><span data-stu-id="04b0e-125">The following code exports the `MarshalObject` interface to a type library.</span></span>  
  
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
>  <span data-ttu-id="04b0e-126">Birlikte çalışma sıralayıcısı, çağrıdan sonra ayrılan herhangi bir nesne değişkeni içinde otomatik olarak serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="04b0e-126">The interop marshaler automatically frees any allocated object inside the variant after the call.</span></span>  
  
 <span data-ttu-id="04b0e-127">Aşağıdaki örnek, biçimlendirilmiş değer türü gösterir.</span><span class="sxs-lookup"><span data-stu-id="04b0e-127">The following example shows a formatted value type.</span></span>  
  
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
  
 <span data-ttu-id="04b0e-128">Aşağıdaki kod biçimlendirilmiş türü için bir tür kitaplığı dışarı aktarır.</span><span class="sxs-lookup"><span data-stu-id="04b0e-128">The following code exports the formatted type to a type library.</span></span>  
  
```  
struct ObjectHolder {  
   VARIANT o1;  
   IDispatch *o2;  
}  
```  
  
## <a name="marshaling-object-to-interface"></a><span data-ttu-id="04b0e-129">Nesne arabirimi için hazırlama</span><span class="sxs-lookup"><span data-stu-id="04b0e-129">Marshaling Object to Interface</span></span>  
 <span data-ttu-id="04b0e-130">Bir nesne, COM arabirim olarak sunulduğunda, bu yönetilen türü için sınıf arabirimi arabirimidir <xref:System.Object> ( **n_esne** arabirimi).</span><span class="sxs-lookup"><span data-stu-id="04b0e-130">When an object is exposed to COM as an interface, that interface is the class interface for the managed type <xref:System.Object> (the **_Object** interface).</span></span> <span data-ttu-id="04b0e-131">Bu arabirim olarak yazılmış bir **IDispatch** (<xref:System.Runtime.InteropServices.UnmanagedType>) veya bir **IUnknown** (**UnmanagedType.IUnknown**) elde edilen tür kitaplığındaki.</span><span class="sxs-lookup"><span data-stu-id="04b0e-131">This interface is typed as an **IDispatch** (<xref:System.Runtime.InteropServices.UnmanagedType>) or an **IUnknown** (**UnmanagedType.IUnknown**) in the resulting type library.</span></span> <span data-ttu-id="04b0e-132">COM istemcileri dinamik olarak çağırmak yönetilen sınıf üyesi veya kendi türetilmiş sınıfları tarafından uygulanan herhangi bir üye **n_esne** arabirimi.</span><span class="sxs-lookup"><span data-stu-id="04b0e-132">COM clients can dynamically invoke the members of the managed class or any members implemented by its derived classes through the **_Object** interface.</span></span> <span data-ttu-id="04b0e-133">İstemci Ayrıca, çağırabilirsiniz **QueryInterface** açıkça yönetilen tür tarafından uygulanan arabirimi elde edilir.</span><span class="sxs-lookup"><span data-stu-id="04b0e-133">The client can also call **QueryInterface** to obtain any other interface explicitly implemented by the managed type.</span></span>  
  
## <a name="marshaling-object-to-variant"></a><span data-ttu-id="04b0e-134">Nesne değişken için hazırlama</span><span class="sxs-lookup"><span data-stu-id="04b0e-134">Marshaling Object to Variant</span></span>  
 <span data-ttu-id="04b0e-135">İç değişken türünde bir nesne için bir değişken başvuruya çalışma zamanında, aşağıdaki kurallara göre belirlenir:</span><span class="sxs-lookup"><span data-stu-id="04b0e-135">When an object is marshaled to a variant, the internal variant type is determined at run time, based on the following rules:</span></span>  
  
-   <span data-ttu-id="04b0e-136">Nesne başvurusu null ise (**hiçbir şey** Visual Basic'te), nesne türünde bir değişken için sıralanır **VT_EMPTY**.</span><span class="sxs-lookup"><span data-stu-id="04b0e-136">If the object reference is null (**Nothing** in Visual Basic), the object is marshaled to a variant of type **VT_EMPTY**.</span></span>  
  
-   <span data-ttu-id="04b0e-137">Nesne aşağıdaki tabloda listelenen herhangi bir türde bir örnek ise, sonuçta elde edilen değişken türü Sıralayıcı içinde oluşturulan ve tabloda belirtilen kurallar tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="04b0e-137">If the object is an instance of any type listed in the following table, the resulting variant type is determined by the rules built into the marshaler and shown in the table.</span></span>  
  
-   <span data-ttu-id="04b0e-138">Hazırlama davranışı açıkça denetlemek için gereken diğer nesnelerin uygulayabilirsiniz <xref:System.IConvertible> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="04b0e-138">Other objects that need to explicitly control the marshaling behavior can implement the <xref:System.IConvertible> interface.</span></span> <span data-ttu-id="04b0e-139">Bu durumda, döndürülen tür kod değişken türü belirlenir <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="04b0e-139">In that case, the variant type is determined by the type code returned from the <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="04b0e-140">Aksi takdirde, nesne türünde bir değişken sıralanır **VT_UNKNOWN**.</span><span class="sxs-lookup"><span data-stu-id="04b0e-140">Otherwise, the object is marshaled as a variant of type **VT_UNKNOWN**.</span></span>  
  
### <a name="marshaling-system-types-to-variant"></a><span data-ttu-id="04b0e-141">Değişken için sistem türlerini hazırlama</span><span class="sxs-lookup"><span data-stu-id="04b0e-141">Marshaling System Types to Variant</span></span>  
 <span data-ttu-id="04b0e-142">Aşağıdaki tabloda, yönetilen nesne türlerini ve bunların karşılık gelen COM değişken türlerine gösterir.</span><span class="sxs-lookup"><span data-stu-id="04b0e-142">The following table shows managed object types and their corresponding COM variant types.</span></span> <span data-ttu-id="04b0e-143">Çağrılan yöntem imzası türü olduğunda, bu tür dönüştürülür <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="04b0e-143">These types are converted only when the signature of the method being called is of type <xref:System.Object?displayProperty=nameWithType>.</span></span>  
  
|<span data-ttu-id="04b0e-144">Nesne türü</span><span class="sxs-lookup"><span data-stu-id="04b0e-144">Object type</span></span>|<span data-ttu-id="04b0e-145">COM değişken türü</span><span class="sxs-lookup"><span data-stu-id="04b0e-145">COM variant type</span></span>|  
|-----------------|----------------------|  
|<span data-ttu-id="04b0e-146">Null Nesne başvurusu (**hiçbir şey** Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="04b0e-146">Null object reference (**Nothing** in Visual Basic).</span></span>|<span data-ttu-id="04b0e-147">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="04b0e-147">**VT_EMPTY**</span></span>|  
|<xref:System.DBNull?displayProperty=nameWithType>|<span data-ttu-id="04b0e-148">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="04b0e-148">**VT_NULL**</span></span>|  
|<xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>|<span data-ttu-id="04b0e-149">**VT_ERROR**</span><span class="sxs-lookup"><span data-stu-id="04b0e-149">**VT_ERROR**</span></span>|  
|<xref:System.Reflection.Missing?displayProperty=nameWithType>|<span data-ttu-id="04b0e-150">**VT_ERROR** ile **E_PARAMNOTFOUND**</span><span class="sxs-lookup"><span data-stu-id="04b0e-150">**VT_ERROR** with **E_PARAMNOTFOUND**</span></span>|  
|<xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>|<span data-ttu-id="04b0e-151">**VT_DISPATCH**</span><span class="sxs-lookup"><span data-stu-id="04b0e-151">**VT_DISPATCH**</span></span>|  
|<xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>|<span data-ttu-id="04b0e-152">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="04b0e-152">**VT_UNKNOWN**</span></span>|  
|<xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>|<span data-ttu-id="04b0e-153">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="04b0e-153">**VT_CY**</span></span>|  
|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="04b0e-154">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="04b0e-154">**VT_BOOL**</span></span>|  
|<xref:System.SByte?displayProperty=nameWithType>|<span data-ttu-id="04b0e-155">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="04b0e-155">**VT_I1**</span></span>|  
|<xref:System.Byte?displayProperty=nameWithType>|<span data-ttu-id="04b0e-156">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="04b0e-156">**VT_UI1**</span></span>|  
|<xref:System.Int16?displayProperty=nameWithType>|<span data-ttu-id="04b0e-157">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="04b0e-157">**VT_I2**</span></span>|  
|<xref:System.UInt16?displayProperty=nameWithType>|<span data-ttu-id="04b0e-158">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="04b0e-158">**VT_UI2**</span></span>|  
|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="04b0e-159">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="04b0e-159">**VT_I4**</span></span>|  
|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="04b0e-160">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="04b0e-160">**VT_UI4**</span></span>|  
|<xref:System.Int64?displayProperty=nameWithType>|<span data-ttu-id="04b0e-161">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="04b0e-161">**VT_I8**</span></span>|  
|<xref:System.UInt64?displayProperty=nameWithType>|<span data-ttu-id="04b0e-162">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="04b0e-162">**VT_UI8**</span></span>|  
|<xref:System.Single?displayProperty=nameWithType>|<span data-ttu-id="04b0e-163">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="04b0e-163">**VT_R4**</span></span>|  
|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="04b0e-164">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="04b0e-164">**VT_R8**</span></span>|  
|<xref:System.Decimal?displayProperty=nameWithType>|<span data-ttu-id="04b0e-165">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="04b0e-165">**VT_DECIMAL**</span></span>|  
|<xref:System.DateTime?displayProperty=nameWithType>|<span data-ttu-id="04b0e-166">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="04b0e-166">**VT_DATE**</span></span>|  
|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="04b0e-167">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="04b0e-167">**VT_BSTR**</span></span>|  
|<xref:System.IntPtr?displayProperty=nameWithType>|<span data-ttu-id="04b0e-168">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="04b0e-168">**VT_INT**</span></span>|  
|<xref:System.UIntPtr?displayProperty=nameWithType>|<span data-ttu-id="04b0e-169">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="04b0e-169">**VT_UINT**</span></span>|  
|<xref:System.Array?displayProperty=nameWithType>|<span data-ttu-id="04b0e-170">**VT_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="04b0e-170">**VT_ARRAY**</span></span>|  
  
 <span data-ttu-id="04b0e-171">Kullanarak `MarshalObject` önceki örnekte, aşağıdaki kod örneğinde tanımlanan arabirimi çeşitleri çeşitli türlerdeki bir COM sunucuya geçirmek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="04b0e-171">Using the `MarshalObject` interface defined in the previous example, the following code example demonstrates how to pass various types of variants to a COM server.</span></span>  
  
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
  
 <span data-ttu-id="04b0e-172">Karşılık gelen yönetilen türleri COM türleri sıralanmış sarmalayıcı sınıflar gibi kullanarak <xref:System.Runtime.InteropServices.ErrorWrapper>, <xref:System.Runtime.InteropServices.DispatchWrapper>, <xref:System.Runtime.InteropServices.UnknownWrapper>, ve <xref:System.Runtime.InteropServices.CurrencyWrapper>.</span><span class="sxs-lookup"><span data-stu-id="04b0e-172">COM types that do not have corresponding managed types can be marshaled using wrapper classes such as <xref:System.Runtime.InteropServices.ErrorWrapper>, <xref:System.Runtime.InteropServices.DispatchWrapper>, <xref:System.Runtime.InteropServices.UnknownWrapper>, and <xref:System.Runtime.InteropServices.CurrencyWrapper>.</span></span> <span data-ttu-id="04b0e-173">Aşağıdaki kod örneği, bu sarmalayıcılar çeşitleri çeşitli türlerdeki bir COM sunucuya geçirmek için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="04b0e-173">The following code example demonstrates how to use these wrappers to pass various types of variants to a COM server.</span></span>  
  
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
  
 <span data-ttu-id="04b0e-174">Sarmalayıcı sınıflar tanımlanan <xref:System.Runtime.InteropServices> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="04b0e-174">The wrapper classes are defined in the <xref:System.Runtime.InteropServices> namespace.</span></span>  
  
### <a name="marshaling-the-iconvertible-interface-to-variant"></a><span data-ttu-id="04b0e-175">IConvertible arabirimi değişken için hazırlama</span><span class="sxs-lookup"><span data-stu-id="04b0e-175">Marshaling the IConvertible Interface to Variant</span></span>  
 <span data-ttu-id="04b0e-176">Önceki bölümde listelenen nasıl bunlar uygulayarak sıralanmış denetleyebilirsiniz daha diğer türleri <xref:System.IConvertible> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="04b0e-176">Types other than those listed in the previous section can control how they are marshaled by implementing the <xref:System.IConvertible> interface.</span></span> <span data-ttu-id="04b0e-177">Nesne uyguluyorsa **IConvertible** arabirimi, COM değişken türü, çalışma zamanında değeri tarafından belirlenir <xref:System.TypeCode> döndürüldüğü numaralandırma <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="04b0e-177">If the object implements the **IConvertible** interface, the COM variant type is determined at run time by the value of the <xref:System.TypeCode> enumeration returned from the <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="04b0e-178">İçin olası değerler aşağıdaki tabloda gösterilmektedir **TypeCode** sabit listesi ve her bir değer için karşılık gelen COM değişken türü.</span><span class="sxs-lookup"><span data-stu-id="04b0e-178">The following table shows the possible values for the **TypeCode** enumeration and the corresponding COM variant type for each value.</span></span>  
  
|<span data-ttu-id="04b0e-179">Typecode'u işlenemiyor</span><span class="sxs-lookup"><span data-stu-id="04b0e-179">TypeCode</span></span>|<span data-ttu-id="04b0e-180">COM değişken türü</span><span class="sxs-lookup"><span data-stu-id="04b0e-180">COM variant type</span></span>|  
|--------------|----------------------|  
|<span data-ttu-id="04b0e-181">**TypeCode.Empty**</span><span class="sxs-lookup"><span data-stu-id="04b0e-181">**TypeCode.Empty**</span></span>|<span data-ttu-id="04b0e-182">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="04b0e-182">**VT_EMPTY**</span></span>|  
|<span data-ttu-id="04b0e-183">**TypeCode.Object**</span><span class="sxs-lookup"><span data-stu-id="04b0e-183">**TypeCode.Object**</span></span>|<span data-ttu-id="04b0e-184">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="04b0e-184">**VT_UNKNOWN**</span></span>|  
|<span data-ttu-id="04b0e-185">**TypeCode.DBNull**</span><span class="sxs-lookup"><span data-stu-id="04b0e-185">**TypeCode.DBNull**</span></span>|<span data-ttu-id="04b0e-186">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="04b0e-186">**VT_NULL**</span></span>|  
|<span data-ttu-id="04b0e-187">**TypeCode.Boolean**</span><span class="sxs-lookup"><span data-stu-id="04b0e-187">**TypeCode.Boolean**</span></span>|<span data-ttu-id="04b0e-188">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="04b0e-188">**VT_BOOL**</span></span>|  
|<span data-ttu-id="04b0e-189">**TypeCode.Char**</span><span class="sxs-lookup"><span data-stu-id="04b0e-189">**TypeCode.Char**</span></span>|<span data-ttu-id="04b0e-190">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="04b0e-190">**VT_UI2**</span></span>|  
|<span data-ttu-id="04b0e-191">**TypeCode.Sbyte**</span><span class="sxs-lookup"><span data-stu-id="04b0e-191">**TypeCode.Sbyte**</span></span>|<span data-ttu-id="04b0e-192">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="04b0e-192">**VT_I1**</span></span>|  
|<span data-ttu-id="04b0e-193">**TypeCode.Byte**</span><span class="sxs-lookup"><span data-stu-id="04b0e-193">**TypeCode.Byte**</span></span>|<span data-ttu-id="04b0e-194">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="04b0e-194">**VT_UI1**</span></span>|  
|<span data-ttu-id="04b0e-195">**TypeCode.Int16**</span><span class="sxs-lookup"><span data-stu-id="04b0e-195">**TypeCode.Int16**</span></span>|<span data-ttu-id="04b0e-196">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="04b0e-196">**VT_I2**</span></span>|  
|<span data-ttu-id="04b0e-197">**TypeCode.UInt16**</span><span class="sxs-lookup"><span data-stu-id="04b0e-197">**TypeCode.UInt16**</span></span>|<span data-ttu-id="04b0e-198">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="04b0e-198">**VT_UI2**</span></span>|  
|<span data-ttu-id="04b0e-199">**TypeCode.Int32**</span><span class="sxs-lookup"><span data-stu-id="04b0e-199">**TypeCode.Int32**</span></span>|<span data-ttu-id="04b0e-200">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="04b0e-200">**VT_I4**</span></span>|  
|<span data-ttu-id="04b0e-201">**TypeCode.UInt32**</span><span class="sxs-lookup"><span data-stu-id="04b0e-201">**TypeCode.UInt32**</span></span>|<span data-ttu-id="04b0e-202">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="04b0e-202">**VT_UI4**</span></span>|  
|<span data-ttu-id="04b0e-203">**TypeCode.Int64**</span><span class="sxs-lookup"><span data-stu-id="04b0e-203">**TypeCode.Int64**</span></span>|<span data-ttu-id="04b0e-204">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="04b0e-204">**VT_I8**</span></span>|  
|<span data-ttu-id="04b0e-205">**TypeCode.UInt64**</span><span class="sxs-lookup"><span data-stu-id="04b0e-205">**TypeCode.UInt64**</span></span>|<span data-ttu-id="04b0e-206">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="04b0e-206">**VT_UI8**</span></span>|  
|<span data-ttu-id="04b0e-207">**TypeCode.Single**</span><span class="sxs-lookup"><span data-stu-id="04b0e-207">**TypeCode.Single**</span></span>|<span data-ttu-id="04b0e-208">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="04b0e-208">**VT_R4**</span></span>|  
|<span data-ttu-id="04b0e-209">**TypeCode.Double**</span><span class="sxs-lookup"><span data-stu-id="04b0e-209">**TypeCode.Double**</span></span>|<span data-ttu-id="04b0e-210">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="04b0e-210">**VT_R8**</span></span>|  
|<span data-ttu-id="04b0e-211">**TypeCode.Decimal**</span><span class="sxs-lookup"><span data-stu-id="04b0e-211">**TypeCode.Decimal**</span></span>|<span data-ttu-id="04b0e-212">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="04b0e-212">**VT_DECIMAL**</span></span>|  
|<span data-ttu-id="04b0e-213">**TypeCode.DateTime**</span><span class="sxs-lookup"><span data-stu-id="04b0e-213">**TypeCode.DateTime**</span></span>|<span data-ttu-id="04b0e-214">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="04b0e-214">**VT_DATE**</span></span>|  
|<span data-ttu-id="04b0e-215">**TypeCode.String**</span><span class="sxs-lookup"><span data-stu-id="04b0e-215">**TypeCode.String**</span></span>|<span data-ttu-id="04b0e-216">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="04b0e-216">**VT_BSTR**</span></span>|  
|<span data-ttu-id="04b0e-217">Desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="04b0e-217">Not supported.</span></span>|<span data-ttu-id="04b0e-218">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="04b0e-218">**VT_INT**</span></span>|  
|<span data-ttu-id="04b0e-219">Desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="04b0e-219">Not supported.</span></span>|<span data-ttu-id="04b0e-220">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="04b0e-220">**VT_UINT**</span></span>|  
|<span data-ttu-id="04b0e-221">Desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="04b0e-221">Not supported.</span></span>|<span data-ttu-id="04b0e-222">**VT_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="04b0e-222">**VT_ARRAY**</span></span>|  
|<span data-ttu-id="04b0e-223">Desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="04b0e-223">Not supported.</span></span>|<span data-ttu-id="04b0e-224">**VT_RECORD**</span><span class="sxs-lookup"><span data-stu-id="04b0e-224">**VT_RECORD**</span></span>|  
|<span data-ttu-id="04b0e-225">Desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="04b0e-225">Not supported.</span></span>|<span data-ttu-id="04b0e-226">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="04b0e-226">**VT_CY**</span></span>|  
|<span data-ttu-id="04b0e-227">Desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="04b0e-227">Not supported.</span></span>|<span data-ttu-id="04b0e-228">**VT_VARIANT**</span><span class="sxs-lookup"><span data-stu-id="04b0e-228">**VT_VARIANT**</span></span>|  
  
 <span data-ttu-id="04b0e-229">COM değişken değerini çağırarak belirlenir **IConvertible.To** *türü* arabirimi, burada **için** *türü* dönüştürme öğesinden döndürülen türüne karşılık gelen yordamı **IConvertible.GetTypeCode**.</span><span class="sxs-lookup"><span data-stu-id="04b0e-229">The value of the COM variant is determined by calling the **IConvertible.To** *Type* interface, where **To** *Type* is the conversion routine that corresponds to the type that was returned from **IConvertible.GetTypeCode**.</span></span> <span data-ttu-id="04b0e-230">Örneğin, döndüren bir nesne **TypeCode.Double** gelen **IConvertible.GetTypeCode** COM türünde sıralanmış **VT_R8**.</span><span class="sxs-lookup"><span data-stu-id="04b0e-230">For example, an object that returns **TypeCode.Double** from **IConvertible.GetTypeCode** is marshaled as a COM variant of type **VT_R8**.</span></span> <span data-ttu-id="04b0e-231">Değişken değeri elde edebilirsiniz (depolanan **dblVal** COM değişkeni alan) tarafından atamayı **IConvertible** arabirimi ve arama <xref:System.IConvertible.ToDouble%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="04b0e-231">You can obtain the value of the variant (stored in the **dblVal** field of the COM variant) by casting to the **IConvertible** interface and calling the <xref:System.IConvertible.ToDouble%2A> method.</span></span>  
  
## <a name="marshaling-variant-to-object"></a><span data-ttu-id="04b0e-232">VARIANT nesnesi için hazırlama</span><span class="sxs-lookup"><span data-stu-id="04b0e-232">Marshaling Variant to Object</span></span>  
 <span data-ttu-id="04b0e-233">Üretilen ne zaman bir nesne, türü ve bazen değerini sıralanmış değişken için bir VARIANT'ı hazırlama nesne türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="04b0e-233">When marshaling a variant to an object, the type, and sometimes the value, of the marshaled variant determines the type of object produced.</span></span> <span data-ttu-id="04b0e-234">Aşağıdaki tabloda her değişken türünde bir değişken COM'dan .NET Framework geçirildiğinde Sıralayıcı oluşturur karşılık gelen nesne türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="04b0e-234">The following table identifies each variant type and the corresponding object type that the marshaler creates when a variant is passed from COM to the .NET Framework.</span></span>  
  
|<span data-ttu-id="04b0e-235">COM değişken türü</span><span class="sxs-lookup"><span data-stu-id="04b0e-235">COM variant type</span></span>|<span data-ttu-id="04b0e-236">Nesne türü</span><span class="sxs-lookup"><span data-stu-id="04b0e-236">Object type</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="04b0e-237">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="04b0e-237">**VT_EMPTY**</span></span>|<span data-ttu-id="04b0e-238">Null Nesne başvurusu (**hiçbir şey** Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="04b0e-238">Null object reference (**Nothing** in Visual Basic).</span></span>|  
|<span data-ttu-id="04b0e-239">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="04b0e-239">**VT_NULL**</span></span>|<xref:System.DBNull?displayProperty=nameWithType>|  
|<span data-ttu-id="04b0e-240">**VT_DISPATCH**</span><span class="sxs-lookup"><span data-stu-id="04b0e-240">**VT_DISPATCH**</span></span>|<span data-ttu-id="04b0e-241">**System.comobject'e** veya null ise (pdispVal == null)</span><span class="sxs-lookup"><span data-stu-id="04b0e-241">**System.__ComObject** or null if (pdispVal == null)</span></span>|  
|<span data-ttu-id="04b0e-242">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="04b0e-242">**VT_UNKNOWN**</span></span>|<span data-ttu-id="04b0e-243">**System.comobject'e** veya null ise (punkVal == null)</span><span class="sxs-lookup"><span data-stu-id="04b0e-243">**System.__ComObject** or null if (punkVal == null)</span></span>|  
|<span data-ttu-id="04b0e-244">**VT_ERROR**</span><span class="sxs-lookup"><span data-stu-id="04b0e-244">**VT_ERROR**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|  
|<span data-ttu-id="04b0e-245">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="04b0e-245">**VT_BOOL**</span></span>|<xref:System.Boolean?displayProperty=nameWithType>|  
|<span data-ttu-id="04b0e-246">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="04b0e-246">**VT_I1**</span></span>|<xref:System.SByte?displayProperty=nameWithType>|  
|<span data-ttu-id="04b0e-247">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="04b0e-247">**VT_UI1**</span></span>|<xref:System.Byte?displayProperty=nameWithType>|  
|<span data-ttu-id="04b0e-248">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="04b0e-248">**VT_I2**</span></span>|<xref:System.Int16?displayProperty=nameWithType>|  
|<span data-ttu-id="04b0e-249">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="04b0e-249">**VT_UI2**</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|  
|<span data-ttu-id="04b0e-250">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="04b0e-250">**VT_I4**</span></span>|<xref:System.Int32?displayProperty=nameWithType>|  
|<span data-ttu-id="04b0e-251">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="04b0e-251">**VT_UI4**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|  
|<span data-ttu-id="04b0e-252">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="04b0e-252">**VT_I8**</span></span>|<xref:System.Int64?displayProperty=nameWithType>|  
|<span data-ttu-id="04b0e-253">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="04b0e-253">**VT_UI8**</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|  
|<span data-ttu-id="04b0e-254">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="04b0e-254">**VT_R4**</span></span>|<xref:System.Single?displayProperty=nameWithType>|  
|<span data-ttu-id="04b0e-255">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="04b0e-255">**VT_R8**</span></span>|<xref:System.Double?displayProperty=nameWithType>|  
|<span data-ttu-id="04b0e-256">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="04b0e-256">**VT_DECIMAL**</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|  
|<span data-ttu-id="04b0e-257">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="04b0e-257">**VT_DATE**</span></span>|<xref:System.DateTime?displayProperty=nameWithType>|  
|<span data-ttu-id="04b0e-258">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="04b0e-258">**VT_BSTR**</span></span>|<xref:System.String?displayProperty=nameWithType>|  
|<span data-ttu-id="04b0e-259">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="04b0e-259">**VT_INT**</span></span>|<xref:System.Int32?displayProperty=nameWithType>|  
|<span data-ttu-id="04b0e-260">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="04b0e-260">**VT_UINT**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|  
|<span data-ttu-id="04b0e-261">**VT_ARRAY** &#124; **VT_**\*</span><span class="sxs-lookup"><span data-stu-id="04b0e-261">**VT_ARRAY** &#124; **VT_**\*</span></span>|<xref:System.Array?displayProperty=nameWithType>|  
|<span data-ttu-id="04b0e-262">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="04b0e-262">**VT_CY**</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|  
|<span data-ttu-id="04b0e-263">**VT_RECORD**</span><span class="sxs-lookup"><span data-stu-id="04b0e-263">**VT_RECORD**</span></span>|<span data-ttu-id="04b0e-264">Paketlenmiş değer türü karşılık gelen.</span><span class="sxs-lookup"><span data-stu-id="04b0e-264">Corresponding boxed value type.</span></span>|  
|<span data-ttu-id="04b0e-265">**VT_VARIANT**</span><span class="sxs-lookup"><span data-stu-id="04b0e-265">**VT_VARIANT**</span></span>|<span data-ttu-id="04b0e-266">Desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="04b0e-266">Not supported.</span></span>|  
  
 <span data-ttu-id="04b0e-267">Değişken türleri için COM'dan geçirilen yönetilen kod ve daha sonra geri COM için aynı değişken türünde çağrı süresi boyunca koruyamayabilir.</span><span class="sxs-lookup"><span data-stu-id="04b0e-267">Variant types passed from COM to managed code and then back to COM might not retain the same variant type for the duration of the call.</span></span> <span data-ttu-id="04b0e-268">Türünde bir değişken olduğunda ne olacağını düşünün **gt; vt_dıspatch &** COM'dan .NET Framework geçirilir.</span><span class="sxs-lookup"><span data-stu-id="04b0e-268">Consider what happens when a variant of type **VT_DISPATCH** is passed from COM to the .NET Framework.</span></span> <span data-ttu-id="04b0e-269">Hazırlama sırasında değişken dönüştürülür bir <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="04b0e-269">During marshaling, the variant is converted to a <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="04b0e-270">Varsa **nesne** ardından geçirilen geri COM için geri türünde bir değişken için sıralanır **VT_UNKNOWN**.</span><span class="sxs-lookup"><span data-stu-id="04b0e-270">If the **Object** is then passed back to COM, it is marshaled back to a variant of type **VT_UNKNOWN**.</span></span> <span data-ttu-id="04b0e-271">Başlangıçta nesne oluşturmak için kullanılan bir değişken aynı türde bir nesne için COM yönetilen koddan başvuruya üretilen değişken olacağını garanti yoktur.</span><span class="sxs-lookup"><span data-stu-id="04b0e-271">There is no guarantee that the variant produced when an object is marshaled from managed code to COM will be the same type as the variant initially used to produce the object.</span></span>  
  
## <a name="marshaling-byref-variants"></a><span data-ttu-id="04b0e-272">ByRef çeşitleri hazırlama</span><span class="sxs-lookup"><span data-stu-id="04b0e-272">Marshaling ByRef Variants</span></span>  
 <span data-ttu-id="04b0e-273">Değere veya başvuruya göre çeşitleri kendilerini geçirilebilir ancak **VT_BYREF** bayrağı de kullanılabilir herhangi bir değişken türü değişken içeriğini yerine başvuruya göre geçirilen belirtmek için değere göre.</span><span class="sxs-lookup"><span data-stu-id="04b0e-273">Although variants themselves can be passed by value or by reference, the **VT_BYREF** flag can also be used with any variant type to indicate that the contents of the variant are being passed by reference instead of by value.</span></span> <span data-ttu-id="04b0e-274">Çeşitleri başvuruya göre sıralama ve bir değişken ile hazırlama arasındaki farkı **VT_BYREF** bayrağı kafa karıştırıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="04b0e-274">The difference between marshaling variants by reference and marshaling a variant with the **VT_BYREF** flag set can be confusing.</span></span> <span data-ttu-id="04b0e-275">Aşağıdaki çizim farklılıkları açıklar:</span><span class="sxs-lookup"><span data-stu-id="04b0e-275">The following illustration clarifies the differences:</span></span>  
  
 ![Değişken gösteren diyagram yığında geçirildi.](./media/default-marshaling-for-objects/interop-variant-passed-value-reference.gif)  
<span data-ttu-id="04b0e-277">Değere ve başvuruya göre geçirilen çeşitleri</span><span class="sxs-lookup"><span data-stu-id="04b0e-277">Variants passed by value and by reference</span></span>  
  
 <span data-ttu-id="04b0e-278">**Nesneleri ve değişkenleri değere göre sıralama için varsayılan davranış**</span><span class="sxs-lookup"><span data-stu-id="04b0e-278">**Default behavior for marshaling objects and variants by value**</span></span>  
  
-   <span data-ttu-id="04b0e-279">Nesneleri, COM yönetilen koddan geçirirken, nesnenin içeriğini tanımlanan kuralların kullanarak sıralayıcı tarafından oluşturulan yeni bir değişken içine kopyalanır [değişken hazırlama nesnesine](#marshaling-object-to-variant).</span><span class="sxs-lookup"><span data-stu-id="04b0e-279">When passing objects from managed code to COM, the contents of the object are copied into a new variant created by the marshaler, using the rules defined in [Marshaling Object to Variant](#marshaling-object-to-variant).</span></span> <span data-ttu-id="04b0e-280">Yönetilmeyen tarafında değişken yapılan değişiklikleri çağrısından dönüşte özgün nesneye geri yayılmaz.</span><span class="sxs-lookup"><span data-stu-id="04b0e-280">Changes made to the variant on the unmanaged side are not propagated back to the original object on return from the call.</span></span>  
  
-   <span data-ttu-id="04b0e-281">Çeşitleri için yönetilen kod COM'dan geçirirken, değişken içeriğini tanımlanan kuralların kullanarak yeni oluşturulan bir nesneye kopyalanır [hazırlama değişken nesneye](#marshaling-variant-to-object).</span><span class="sxs-lookup"><span data-stu-id="04b0e-281">When passing variants from COM to managed code, the contents of the variant are copied to a newly created object, using the rules defined in [Marshaling Variant to Object](#marshaling-variant-to-object).</span></span> <span data-ttu-id="04b0e-282">Yönetilen tarafında nesneye yapılan değişiklikleri geri çağrısından dönüşte özgün değişken için yayılmaz.</span><span class="sxs-lookup"><span data-stu-id="04b0e-282">Changes made to the object on the managed side are not propagated back to the original variant on return from the call.</span></span>  
  
 <span data-ttu-id="04b0e-283">**Nesneleri ve değişkenleri başvuruya göre hazırlama için varsayılan davranış**</span><span class="sxs-lookup"><span data-stu-id="04b0e-283">**Default behavior for marshaling objects and variants by reference**</span></span>  
  
 <span data-ttu-id="04b0e-284">Değişiklikleri tekrar çağırana yayılmasına parametreleri başvuruya göre geçirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="04b0e-284">To propagate changes back to the caller, the parameters must be passed by reference.</span></span> <span data-ttu-id="04b0e-285">Örneğin, kullanabilirsiniz **ref** anahtar sözcüğünü C# (veya **ByRef** yönetilen kod Visual Basic) başvuru ile parametreleri iletme.</span><span class="sxs-lookup"><span data-stu-id="04b0e-285">For example, you can use the **ref** keyword in C# (or **ByRef** in Visual Basic managed code) to pass parameters by reference.</span></span> <span data-ttu-id="04b0e-286">COM, başvuru parametreleri gibi bir işaretçi kullanılarak geçirilen bir **değişken \*** .</span><span class="sxs-lookup"><span data-stu-id="04b0e-286">In COM, reference parameters are passed using a pointer such as a **variant \***.</span></span>  
  
-   <span data-ttu-id="04b0e-287">Bir nesne için COM başvuruya göre geçirme, Sıralayıcı yeni bir değişken oluşturur ve çağrı yapılmadan önce değişken bir nesne başvurusu içeriğini kopyalar.</span><span class="sxs-lookup"><span data-stu-id="04b0e-287">When passing an object to COM by reference, the marshaler creates a new variant and copies the contents of the object reference into the variant before the call is made.</span></span> <span data-ttu-id="04b0e-288">Değişken, kullanıcının değişken içeriğini değiştirmek ücretsiz olduğu yönetilmeyen işleve geçirilir.</span><span class="sxs-lookup"><span data-stu-id="04b0e-288">The variant is passed to the unmanaged function where the user is free to change the contents of the variant.</span></span> <span data-ttu-id="04b0e-289">Geri çağrısından, yönetilmeyen tarafında değişken yapılan tüm değişiklikler özgün nesneye geri yayılır.</span><span class="sxs-lookup"><span data-stu-id="04b0e-289">On return from the call, any changes made to the variant on the unmanaged side are propagated back to the original object.</span></span> <span data-ttu-id="04b0e-290">Ardından bir çağrısına geçirilen değişken türünde bir değişken türünde farklıdır, değişiklikleri geri farklı türde bir nesne için yayılır.</span><span class="sxs-lookup"><span data-stu-id="04b0e-290">If the type of the variant differs from the type of the variant passed to the call, then the changes are propagated back to an object of a different type.</span></span> <span data-ttu-id="04b0e-291">Diğer bir deyişle, çağrısına geçirilen nesne türü çağrısından döndürülen nesnenin türü farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="04b0e-291">That is, the type of the object passed into the call can differ from the type of the object returned from the call.</span></span>  
  
-   <span data-ttu-id="04b0e-292">Bir değişken başvuru ile yönetilen kod için geçirirken, Sıralayıcı yeni bir nesne oluşturur ve çağrı yapmadan önce değişken içeriğini nesnesine kopyalar.</span><span class="sxs-lookup"><span data-stu-id="04b0e-292">When passing a variant to managed code by reference, the marshaler creates a new object and copies the contents of the variant into the object before making the call.</span></span> <span data-ttu-id="04b0e-293">Nesnesine bir başvuru, kullanıcının bir nesneyi değiştirmek ücretsiz olduğu yönetilen bir işleve geçirilir.</span><span class="sxs-lookup"><span data-stu-id="04b0e-293">A reference to the object is passed to the managed function, where the user is free to change the object.</span></span> <span data-ttu-id="04b0e-294">Geri çağrısından, başvurulan nesneye yapılan tüm değişiklikler özgün değişkenine geri yayılır.</span><span class="sxs-lookup"><span data-stu-id="04b0e-294">On return from the call, any changes made to the referenced object are propagated back to the original variant.</span></span> <span data-ttu-id="04b0e-295">Nesne türü çağrısına geçirilen nesnenin türü farklı olması durumunda, özgün değişken türü değiştirilir ve değeri değişken geri yayılır.</span><span class="sxs-lookup"><span data-stu-id="04b0e-295">If the type of the object differs from the type of the object passed in to the call, the type of the original variant is changed and the value is propagated back into the variant.</span></span> <span data-ttu-id="04b0e-296">Yeniden çağrısına geçirilen değişken türünü çağrısından döndürülen değişken türünden farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="04b0e-296">Again, the type of the variant passed into the call can differ from the type of the variant returned from the call.</span></span>  
  
 <span data-ttu-id="04b0e-297">**Bir değişken VT_BYREF bayrağı ayarlanmış hazırlama için varsayılan davranış**</span><span class="sxs-lookup"><span data-stu-id="04b0e-297">**Default behavior for marshaling a variant with the VT_BYREF flag set**</span></span>  
  
-   <span data-ttu-id="04b0e-298">Yönetilen kod için değere göre geçirilen bir değişken olabilir **VT_BYREF** bayrağı ayarlanmış değişken bir değer yerine bir başvuru içerdiğini belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="04b0e-298">A variant being passed to managed code by value can have the **VT_BYREF** flag set to indicate that the variant contains a reference instead of a value.</span></span> <span data-ttu-id="04b0e-299">Bu durumda, değişken değer olarak geçilemez çünkü değişken hala bir nesneye sıralanır.</span><span class="sxs-lookup"><span data-stu-id="04b0e-299">In this case, the variant is still marshaled to an object because the variant is being passed by value.</span></span> <span data-ttu-id="04b0e-300">Sıralayıcı otomatik olarak başvuru varyantı içeriğini ve çağrı yapmadan önce yeni oluşturulan bir nesneye kopyalar.</span><span class="sxs-lookup"><span data-stu-id="04b0e-300">The marshaler automatically dereferences the contents of the variant and copies it into a newly created object before making the call.</span></span> <span data-ttu-id="04b0e-301">Nesne, daha sonra yönetilen işleve geçirilir; Bununla birlikte, geri çağrısından, nesneyi geri özgün değişken dağıtılmadı.</span><span class="sxs-lookup"><span data-stu-id="04b0e-301">The object is then passed into the managed function; however, on return from the call, the object is not propagated back into the original variant.</span></span> <span data-ttu-id="04b0e-302">Yönetilen nesneye yapılan değişiklikler kaybolur.</span><span class="sxs-lookup"><span data-stu-id="04b0e-302">Changes made to the managed object are lost.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="04b0e-303">Değişken olsa bile, değer olarak geçilemez bir değişken değerini değiştirmek için bir yolu yoktur **VT_BYREF** bayrağı ayarlanmış.</span><span class="sxs-lookup"><span data-stu-id="04b0e-303">There is no way to change the value of a variant passed by value, even if the variant has the **VT_BYREF** flag set.</span></span>  
  
-   <span data-ttu-id="04b0e-304">Yönetilen kod için başvuruya göre geçirilen bir değişken bulundurabilirsiniz **VT_BYREF** bayrağı ayarlanmış başka bir başvuru varyantı içerdiğini belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="04b0e-304">A variant being passed to managed code by reference can also have the **VT_BYREF** flag set to indicate that the variant contains another reference.</span></span> <span data-ttu-id="04b0e-305">Değişken sıralanmış olduğundan bulursa, bir **ref** değişken başvuruyla geçirildi çünkü nesne.</span><span class="sxs-lookup"><span data-stu-id="04b0e-305">If it does, the variant is marshaled to a **ref** object because the variant is being passed by reference.</span></span> <span data-ttu-id="04b0e-306">Sıralayıcı otomatik olarak başvuru varyantı içeriğini ve çağrı yapmadan önce yeni oluşturulan bir nesneye kopyalar.</span><span class="sxs-lookup"><span data-stu-id="04b0e-306">The marshaler automatically dereferences the contents of the variant and copies it into a newly created object before making the call.</span></span> <span data-ttu-id="04b0e-307">Geçirilen nesne olarak yalnızca nesneyi aynı türde ise geri çağrısından, nesnenin değerini geri başvuru özgün değişken içinde yayılır.</span><span class="sxs-lookup"><span data-stu-id="04b0e-307">On return from the call, the value of the object is propagated back to the reference within the original variant only if the object is the same type as the object passed in.</span></span> <span data-ttu-id="04b0e-308">Diğer bir deyişle, yayma ile bir değişken türünü değiştirmez **VT_BYREF** bayrağı ayarlanmış.</span><span class="sxs-lookup"><span data-stu-id="04b0e-308">That is, propagation does not change the type of a variant with the **VT_BYREF** flag set.</span></span> <span data-ttu-id="04b0e-309">Nesne türü aramasında değiştirilirse bir <xref:System.InvalidCastException> çağrısından dönüşte gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="04b0e-309">If the type of the object is changed during the call, an <xref:System.InvalidCastException> occurs on return from the call.</span></span>  
  
 <span data-ttu-id="04b0e-310">Aşağıdaki tabloda çeşitleri ve nesneler için yayma kuralları özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="04b0e-310">The following table summarizes the propagation rules for variants and objects.</span></span>  
  
|<span data-ttu-id="04b0e-311">Başlangıç</span><span class="sxs-lookup"><span data-stu-id="04b0e-311">From</span></span>|<span data-ttu-id="04b0e-312">Bitiş</span><span class="sxs-lookup"><span data-stu-id="04b0e-312">To</span></span>|<span data-ttu-id="04b0e-313">Değişiklikleri geri yayılmaz</span><span class="sxs-lookup"><span data-stu-id="04b0e-313">Changes propagated back</span></span>|  
|----------|--------|-----------------------------|  
|<span data-ttu-id="04b0e-314">\**Değişken\*\*\*v*</span><span class="sxs-lookup"><span data-stu-id="04b0e-314">**Variant**  *v*</span></span>|<span data-ttu-id="04b0e-315">\**Nesne\*\*\*o*</span><span class="sxs-lookup"><span data-stu-id="04b0e-315">**Object**  *o*</span></span>|<span data-ttu-id="04b0e-316">hiçbir zaman</span><span class="sxs-lookup"><span data-stu-id="04b0e-316">Never</span></span>|  
|<span data-ttu-id="04b0e-317">\**Nesne\*\*\*o*</span><span class="sxs-lookup"><span data-stu-id="04b0e-317">**Object**  *o*</span></span>|<span data-ttu-id="04b0e-318">\**Değişken\*\*\*v*</span><span class="sxs-lookup"><span data-stu-id="04b0e-318">**Variant**  *v*</span></span>|<span data-ttu-id="04b0e-319">hiçbir zaman</span><span class="sxs-lookup"><span data-stu-id="04b0e-319">Never</span></span>|  
|<span data-ttu-id="04b0e-320">\**Değişken\*\*\*\*\*\*\*\*\*\*BD*</span><span class="sxs-lookup"><span data-stu-id="04b0e-320">**Variant**   ***\****  *pv*</span></span>|<span data-ttu-id="04b0e-321">\**Ref nesne\*\*\*o*</span><span class="sxs-lookup"><span data-stu-id="04b0e-321">**Ref Object**  *o*</span></span>|<span data-ttu-id="04b0e-322">Her zaman</span><span class="sxs-lookup"><span data-stu-id="04b0e-322">Always</span></span>|  
|<span data-ttu-id="04b0e-323">\**Ref nesne\*\*\*o*</span><span class="sxs-lookup"><span data-stu-id="04b0e-323">**Ref object**  *o*</span></span>|<span data-ttu-id="04b0e-324">\**Değişken\*\*\*\*\*\*\*\*\*\*BD*</span><span class="sxs-lookup"><span data-stu-id="04b0e-324">**Variant**   ***\****  *pv*</span></span>|<span data-ttu-id="04b0e-325">Her zaman</span><span class="sxs-lookup"><span data-stu-id="04b0e-325">Always</span></span>|  
|<span data-ttu-id="04b0e-326">\**Değişken\*\*\*v* **(VT_BYREF** *&#124;* **VT_\*)** </span><span class="sxs-lookup"><span data-stu-id="04b0e-326">**Variant**  *v* **(VT_BYREF** *&#124;* **VT_\*)**</span></span>|<span data-ttu-id="04b0e-327">\**Nesne\*\*\*o*</span><span class="sxs-lookup"><span data-stu-id="04b0e-327">**Object**  *o*</span></span>|<span data-ttu-id="04b0e-328">hiçbir zaman</span><span class="sxs-lookup"><span data-stu-id="04b0e-328">Never</span></span>|  
|<span data-ttu-id="04b0e-329">\**Değişken\*\*\*v* **(VT_BYREF** *&#124;* **VT_)** </span><span class="sxs-lookup"><span data-stu-id="04b0e-329">**Variant**  *v* **(VT_BYREF** *&#124;* **VT_)**</span></span>|<span data-ttu-id="04b0e-330">\**Ref nesne\*\*\*o*</span><span class="sxs-lookup"><span data-stu-id="04b0e-330">**Ref Object**  *o*</span></span>|<span data-ttu-id="04b0e-331">Yalnızca türü değişmemişse.</span><span class="sxs-lookup"><span data-stu-id="04b0e-331">Only if the type has not changed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="04b0e-332">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04b0e-332">See also</span></span>
- [<span data-ttu-id="04b0e-333">Varsayılan Hazırlama Davranışı</span><span class="sxs-lookup"><span data-stu-id="04b0e-333">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
- [<span data-ttu-id="04b0e-334">Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler</span><span class="sxs-lookup"><span data-stu-id="04b0e-334">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- <span data-ttu-id="04b0e-335">[Yönlü öznitelikler](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="04b0e-335">[Directional Attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span></span>
- [<span data-ttu-id="04b0e-336">Kopyalama ve Sabitleme</span><span class="sxs-lookup"><span data-stu-id="04b0e-336">Copying and Pinning</span></span>](copying-and-pinning.md)
