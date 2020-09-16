---
title: Nesneler için Varsayılan Hazırlama
description: Nesneler için varsayılan hazırlamayı anlayın. Sıralama seçeneklerini gözden geçirin. Nesneleri arabirimlere veya çeşitlere, çeşitlere ve ByRef çeşitlere göre sıralama.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- objects, interop marshaling
- interop marshaling, objects
ms.assetid: c2ef0284-b061-4e12-b6d3-6a502b9cc558
ms.openlocfilehash: 3e07ceef62d97db4206f530aa0859b101fe41a11
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555100"
---
# <a name="default-marshaling-for-objects"></a><span data-ttu-id="7472f-105">Nesneler için Varsayılan Hazırlama</span><span class="sxs-lookup"><span data-stu-id="7472f-105">Default Marshaling for Objects</span></span>

<span data-ttu-id="7472f-106">Olarak yazılan parametreler ve alanlar <xref:System.Object?displayProperty=nameWithType> , aşağıdaki türlerden biri olarak yönetilmeyen koda gösterilebilir:</span><span class="sxs-lookup"><span data-stu-id="7472f-106">Parameters and fields typed as <xref:System.Object?displayProperty=nameWithType> can be exposed to unmanaged code as one of the following types:</span></span>

- <span data-ttu-id="7472f-107">Nesne bir parametre olduğunda bir değişken.</span><span class="sxs-lookup"><span data-stu-id="7472f-107">A variant when the object is a parameter.</span></span>

- <span data-ttu-id="7472f-108">Nesne bir yapı alanı olduğunda arabirim.</span><span class="sxs-lookup"><span data-stu-id="7472f-108">An interface when the object is a structure field.</span></span>

<span data-ttu-id="7472f-109">Yalnızca COM birlikte çalışması nesne türleri için sıralama destekler.</span><span class="sxs-lookup"><span data-stu-id="7472f-109">Only COM interop supports marshaling for object types.</span></span> <span data-ttu-id="7472f-110">Varsayılan davranış, nesneleri COM türevlerine sıralamakta kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7472f-110">The default behavior is to marshal objects to COM variants.</span></span> <span data-ttu-id="7472f-111">Bu kurallar yalnızca tür **nesnesi** için geçerlidir ve **Object** sınıfından türetilmiş türü kesin belirlenmiş nesneler için uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="7472f-111">These rules apply only to the type **Object** and do not apply to strongly typed objects that derive from the **Object** class.</span></span>

## <a name="marshaling-options"></a><span data-ttu-id="7472f-112">Sıralama seçenekleri</span><span class="sxs-lookup"><span data-stu-id="7472f-112">Marshaling Options</span></span>

<span data-ttu-id="7472f-113">Aşağıdaki tabloda, **nesne** veri türü için sıralama seçenekleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7472f-113">The following table shows the marshaling options for the **Object** data type.</span></span> <span data-ttu-id="7472f-114"><xref:System.Runtime.InteropServices.MarshalAsAttribute>Özniteliği <xref:System.Runtime.InteropServices.UnmanagedType> nesneleri sıralamak için birkaç numaralandırma değeri sağlar.</span><span class="sxs-lookup"><span data-stu-id="7472f-114">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal objects.</span></span>

|<span data-ttu-id="7472f-115">Sabit listesi türü</span><span class="sxs-lookup"><span data-stu-id="7472f-115">Enumeration type</span></span>|<span data-ttu-id="7472f-116">Yönetilmeyen biçimin açıklaması</span><span class="sxs-lookup"><span data-stu-id="7472f-116">Description of unmanaged format</span></span>|
|----------------------|-------------------------------------|
|<span data-ttu-id="7472f-117">**UnmanagedType. struct**</span><span class="sxs-lookup"><span data-stu-id="7472f-117">**UnmanagedType.Struct**</span></span><br /><br /> <span data-ttu-id="7472f-118">(parametreler için varsayılan)</span><span class="sxs-lookup"><span data-stu-id="7472f-118">(default for parameters)</span></span>|<span data-ttu-id="7472f-119">COM stili bir varyant.</span><span class="sxs-lookup"><span data-stu-id="7472f-119">A COM-style variant.</span></span>|
|<span data-ttu-id="7472f-120">**UnmanagedType. Interface**</span><span class="sxs-lookup"><span data-stu-id="7472f-120">**UnmanagedType.Interface**</span></span>|<span data-ttu-id="7472f-121">Mümkünse **IDispatch** arabirimi; Aksi takdirde, bir **IUnknown** arabirimi.</span><span class="sxs-lookup"><span data-stu-id="7472f-121">An **IDispatch** interface, if possible; otherwise, an **IUnknown** interface.</span></span>|
|<span data-ttu-id="7472f-122">**UnmanagedType. IUnknown**</span><span class="sxs-lookup"><span data-stu-id="7472f-122">**UnmanagedType.IUnknown**</span></span><br /><br /> <span data-ttu-id="7472f-123">(alanlar için varsayılan)</span><span class="sxs-lookup"><span data-stu-id="7472f-123">(default for fields)</span></span>|<span data-ttu-id="7472f-124">Bir **IUnknown** arabirimi.</span><span class="sxs-lookup"><span data-stu-id="7472f-124">An **IUnknown** interface.</span></span>|
|<span data-ttu-id="7472f-125">**UnmanagedType. IDispatch**</span><span class="sxs-lookup"><span data-stu-id="7472f-125">**UnmanagedType.IDispatch**</span></span>|<span data-ttu-id="7472f-126">Bir **IDispatch** arabirimi.</span><span class="sxs-lookup"><span data-stu-id="7472f-126">An **IDispatch** interface.</span></span>|

<span data-ttu-id="7472f-127">Aşağıdaki örnek için yönetilen arabirim tanımını gösterir `MarshalObject` .</span><span class="sxs-lookup"><span data-stu-id="7472f-127">The following example shows the managed interface definition for `MarshalObject`.</span></span>

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

<span data-ttu-id="7472f-128">Aşağıdaki kod, `MarshalObject` arabirimi bir tür kitaplığına dışarı aktarır.</span><span class="sxs-lookup"><span data-stu-id="7472f-128">The following code exports the `MarshalObject` interface to a type library.</span></span>

```cpp
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
> <span data-ttu-id="7472f-129">Birlikte çalışma sıralayıcısı, çağrıdan sonra değişken içinde tüm ayrılmış nesneleri otomatik olarak boşaltır.</span><span class="sxs-lookup"><span data-stu-id="7472f-129">The interop marshaler automatically frees any allocated object inside the variant after the call.</span></span>

<span data-ttu-id="7472f-130">Aşağıdaki örnek, biçimli bir değer türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="7472f-130">The following example shows a formatted value type.</span></span>

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

<span data-ttu-id="7472f-131">Aşağıdaki kod, biçimli türü bir tür kitaplığına dışarı aktarır.</span><span class="sxs-lookup"><span data-stu-id="7472f-131">The following code exports the formatted type to a type library.</span></span>

```cpp
struct ObjectHolder {
   VARIANT o1;
   IDispatch *o2;
}
```

## <a name="marshaling-object-to-interface"></a><span data-ttu-id="7472f-132">Nesne arabirime sıralanıyor</span><span class="sxs-lookup"><span data-stu-id="7472f-132">Marshaling Object to Interface</span></span>

<span data-ttu-id="7472f-133">Bir nesne bir arabirim olarak COM 'a sunulduğunda, bu arabirim yönetilen tür için sınıf arabirimidir <xref:System.Object> ( **_object** arabirimi).</span><span class="sxs-lookup"><span data-stu-id="7472f-133">When an object is exposed to COM as an interface, that interface is the class interface for the managed type <xref:System.Object> (the **_Object** interface).</span></span> <span data-ttu-id="7472f-134">Bu arabirim **IDispatch** <xref:System.Runtime.InteropServices.UnmanagedType> , sonuç türü kitaplığında bir IDispatch () veya **IUnknown** (**UnmanagedType. IUnknown**) olarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="7472f-134">This interface is typed as an **IDispatch** (<xref:System.Runtime.InteropServices.UnmanagedType>) or an **IUnknown** (**UnmanagedType.IUnknown**) in the resulting type library.</span></span> <span data-ttu-id="7472f-135">COM istemcileri yönetilen sınıfın veya **_object** arabirimi aracılığıyla türetilmiş sınıfları tarafından uygulanan herhangi bir üyenin üyelerini dinamik olarak çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="7472f-135">COM clients can dynamically invoke the members of the managed class or any members implemented by its derived classes through the **_Object** interface.</span></span> <span data-ttu-id="7472f-136">İstemci Ayrıca, yönetilen tür tarafından açıkça uygulanan başka bir arabirim elde etmek için **QueryInterface** 'i çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="7472f-136">The client can also call **QueryInterface** to obtain any other interface explicitly implemented by the managed type.</span></span>

## <a name="marshaling-object-to-variant"></a><span data-ttu-id="7472f-137">Nesne varyanta sıralanıyor</span><span class="sxs-lookup"><span data-stu-id="7472f-137">Marshaling Object to Variant</span></span>

<span data-ttu-id="7472f-138">Bir nesne bir varyanta sıralanışında, iç varyant türü çalışma zamanında aşağıdaki kurallara göre belirlenir:</span><span class="sxs-lookup"><span data-stu-id="7472f-138">When an object is marshaled to a variant, the internal variant type is determined at run time, based on the following rules:</span></span>

- <span data-ttu-id="7472f-139">Nesne başvurusu null ise (Visual Basic**hiçbir şey** ), nesne **VT_EMPTY**türünde bir değişkenle sıralanır.</span><span class="sxs-lookup"><span data-stu-id="7472f-139">If the object reference is null (**Nothing** in Visual Basic), the object is marshaled to a variant of type **VT_EMPTY**.</span></span>

- <span data-ttu-id="7472f-140">Nesne, aşağıdaki tabloda listelenen herhangi bir türde bir örnek ise, sonuçta elde edilen varyant türü Sıralayıcı içinde yerleşik olan ve tabloda gösterilen kurallara göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="7472f-140">If the object is an instance of any type listed in the following table, the resulting variant type is determined by the rules built into the marshaler and shown in the table.</span></span>

- <span data-ttu-id="7472f-141">Sıralama davranışını açıkça kontrol etmeniz gereken diğer nesneler <xref:System.IConvertible> arabirimi uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="7472f-141">Other objects that need to explicitly control the marshaling behavior can implement the <xref:System.IConvertible> interface.</span></span> <span data-ttu-id="7472f-142">Bu durumda, değişken türü yönteminden döndürülen tür koduna göre belirlenir <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="7472f-142">In that case, the variant type is determined by the type code returned from the <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="7472f-143">Aksi takdirde, nesne **VT_UNKNOWN**türünde bir değişken olarak sıralanır.</span><span class="sxs-lookup"><span data-stu-id="7472f-143">Otherwise, the object is marshaled as a variant of type **VT_UNKNOWN**.</span></span>

### <a name="marshaling-system-types-to-variant"></a><span data-ttu-id="7472f-144">Sistem türlerini varyanta sıralama</span><span class="sxs-lookup"><span data-stu-id="7472f-144">Marshaling System Types to Variant</span></span>

<span data-ttu-id="7472f-145">Aşağıdaki tabloda, yönetilen nesne türleri ve bunlara karşılık gelen COM Variant türleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7472f-145">The following table shows managed object types and their corresponding COM variant types.</span></span> <span data-ttu-id="7472f-146">Bu türler yalnızca çağrılan metodun imzası tür olduğunda dönüştürülür <xref:System.Object?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="7472f-146">These types are converted only when the signature of the method being called is of type <xref:System.Object?displayProperty=nameWithType>.</span></span>

|<span data-ttu-id="7472f-147">Nesne türü</span><span class="sxs-lookup"><span data-stu-id="7472f-147">Object type</span></span>|<span data-ttu-id="7472f-148">COM varyant türü</span><span class="sxs-lookup"><span data-stu-id="7472f-148">COM variant type</span></span>|
|-----------------|----------------------|
|<span data-ttu-id="7472f-149">Null nesne başvurusu (Visual Basic**hiçbir şey** ).</span><span class="sxs-lookup"><span data-stu-id="7472f-149">Null object reference (**Nothing** in Visual Basic).</span></span>|<span data-ttu-id="7472f-150">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="7472f-150">**VT_EMPTY**</span></span>|
|<xref:System.DBNull?displayProperty=nameWithType>|<span data-ttu-id="7472f-151">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="7472f-151">**VT_NULL**</span></span>|
|<xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>|<span data-ttu-id="7472f-152">**VT_ERROR**</span><span class="sxs-lookup"><span data-stu-id="7472f-152">**VT_ERROR**</span></span>|
|<xref:System.Reflection.Missing?displayProperty=nameWithType>|<span data-ttu-id="7472f-153">**E_PARAMNOTFOUND** **VT_ERROR**</span><span class="sxs-lookup"><span data-stu-id="7472f-153">**VT_ERROR** with **E_PARAMNOTFOUND**</span></span>|
|<xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>|<span data-ttu-id="7472f-154">**VT_DISPATCH**</span><span class="sxs-lookup"><span data-stu-id="7472f-154">**VT_DISPATCH**</span></span>|
|<xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>|<span data-ttu-id="7472f-155">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="7472f-155">**VT_UNKNOWN**</span></span>|
|<xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>|<span data-ttu-id="7472f-156">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="7472f-156">**VT_CY**</span></span>|
|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="7472f-157">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="7472f-157">**VT_BOOL**</span></span>|
|<xref:System.SByte?displayProperty=nameWithType>|<span data-ttu-id="7472f-158">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="7472f-158">**VT_I1**</span></span>|
|<xref:System.Byte?displayProperty=nameWithType>|<span data-ttu-id="7472f-159">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="7472f-159">**VT_UI1**</span></span>|
|<xref:System.Int16?displayProperty=nameWithType>|<span data-ttu-id="7472f-160">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="7472f-160">**VT_I2**</span></span>|
|<xref:System.UInt16?displayProperty=nameWithType>|<span data-ttu-id="7472f-161">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="7472f-161">**VT_UI2**</span></span>|
|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="7472f-162">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="7472f-162">**VT_I4**</span></span>|
|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="7472f-163">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="7472f-163">**VT_UI4**</span></span>|
|<xref:System.Int64?displayProperty=nameWithType>|<span data-ttu-id="7472f-164">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="7472f-164">**VT_I8**</span></span>|
|<xref:System.UInt64?displayProperty=nameWithType>|<span data-ttu-id="7472f-165">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="7472f-165">**VT_UI8**</span></span>|
|<xref:System.Single?displayProperty=nameWithType>|<span data-ttu-id="7472f-166">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="7472f-166">**VT_R4**</span></span>|
|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="7472f-167">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="7472f-167">**VT_R8**</span></span>|
|<xref:System.Decimal?displayProperty=nameWithType>|<span data-ttu-id="7472f-168">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="7472f-168">**VT_DECIMAL**</span></span>|
|<xref:System.DateTime?displayProperty=nameWithType>|<span data-ttu-id="7472f-169">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="7472f-169">**VT_DATE**</span></span>|
|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="7472f-170">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="7472f-170">**VT_BSTR**</span></span>|
|<xref:System.IntPtr?displayProperty=nameWithType>|<span data-ttu-id="7472f-171">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="7472f-171">**VT_INT**</span></span>|
|<xref:System.UIntPtr?displayProperty=nameWithType>|<span data-ttu-id="7472f-172">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="7472f-172">**VT_UINT**</span></span>|
|<xref:System.Array?displayProperty=nameWithType>|<span data-ttu-id="7472f-173">**VT_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="7472f-173">**VT_ARRAY**</span></span>|

<span data-ttu-id="7472f-174">`MarshalObject`Önceki örnekte tanımlanan arabirimi kullanarak, aşağıdaki kod örneği BIR com sunucusuna çeşitli çeşit çeşitlemelerini nasıl geçirebileceğinizi göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="7472f-174">Using the `MarshalObject` interface defined in the previous example, the following code example demonstrates how to pass various types of variants to a COM server.</span></span>

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

<span data-ttu-id="7472f-175">Karşılık gelen yönetilen türleri olmayan com türleri,,, ve gibi sarmalayıcı sınıflar kullanılarak sıralanabilir <xref:System.Runtime.InteropServices.ErrorWrapper> <xref:System.Runtime.InteropServices.DispatchWrapper> <xref:System.Runtime.InteropServices.UnknownWrapper> <xref:System.Runtime.InteropServices.CurrencyWrapper> .</span><span class="sxs-lookup"><span data-stu-id="7472f-175">COM types that do not have corresponding managed types can be marshaled using wrapper classes such as <xref:System.Runtime.InteropServices.ErrorWrapper>, <xref:System.Runtime.InteropServices.DispatchWrapper>, <xref:System.Runtime.InteropServices.UnknownWrapper>, and <xref:System.Runtime.InteropServices.CurrencyWrapper>.</span></span> <span data-ttu-id="7472f-176">Aşağıdaki kod örneği, bir COM sunucusuna çeşitli çeşit çeşitlemelerini geçirmek için bu sarmalayıcılarını nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="7472f-176">The following code example demonstrates how to use these wrappers to pass various types of variants to a COM server.</span></span>

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

<span data-ttu-id="7472f-177">Sarmalayıcı sınıflar <xref:System.Runtime.InteropServices> ad alanında tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="7472f-177">The wrapper classes are defined in the <xref:System.Runtime.InteropServices> namespace.</span></span>

### <a name="marshaling-the-iconvertible-interface-to-variant"></a><span data-ttu-id="7472f-178">Iverli arabirimini VARIANT 'a hazırlama</span><span class="sxs-lookup"><span data-stu-id="7472f-178">Marshaling the IConvertible Interface to Variant</span></span>

<span data-ttu-id="7472f-179">Önceki bölümde listelenenler dışındaki türler, arabirimini uygulayarak nasıl sıralandıklarından kontrol edebilir <xref:System.IConvertible> .</span><span class="sxs-lookup"><span data-stu-id="7472f-179">Types other than those listed in the previous section can control how they are marshaled by implementing the <xref:System.IConvertible> interface.</span></span> <span data-ttu-id="7472f-180">Nesne **Iconverli** arabirimini UYGULARSA, com Variant türü, <xref:System.TypeCode> yönteminden döndürülen numaralandırmanın değeri ile çalışma zamanında belirlenir <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="7472f-180">If the object implements the **IConvertible** interface, the COM variant type is determined at run time by the value of the <xref:System.TypeCode> enumeration returned from the <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="7472f-181">Aşağıdaki tabloda, her bir değer için **TypeCode** numaralandırması ve KARŞıLıK gelen com Variant türü için olası değerler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7472f-181">The following table shows the possible values for the **TypeCode** enumeration and the corresponding COM variant type for each value.</span></span>

|<span data-ttu-id="7472f-182">Kodunu</span><span class="sxs-lookup"><span data-stu-id="7472f-182">TypeCode</span></span>|<span data-ttu-id="7472f-183">COM varyant türü</span><span class="sxs-lookup"><span data-stu-id="7472f-183">COM variant type</span></span>|
|--------------|----------------------|
|<span data-ttu-id="7472f-184">**TypeCode. Empty**</span><span class="sxs-lookup"><span data-stu-id="7472f-184">**TypeCode.Empty**</span></span>|<span data-ttu-id="7472f-185">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="7472f-185">**VT_EMPTY**</span></span>|
|<span data-ttu-id="7472f-186">**TypeCode. Object**</span><span class="sxs-lookup"><span data-stu-id="7472f-186">**TypeCode.Object**</span></span>|<span data-ttu-id="7472f-187">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="7472f-187">**VT_UNKNOWN**</span></span>|
|<span data-ttu-id="7472f-188">**TypeCode. DBNull**</span><span class="sxs-lookup"><span data-stu-id="7472f-188">**TypeCode.DBNull**</span></span>|<span data-ttu-id="7472f-189">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="7472f-189">**VT_NULL**</span></span>|
|<span data-ttu-id="7472f-190">**TypeCode. Boolean**</span><span class="sxs-lookup"><span data-stu-id="7472f-190">**TypeCode.Boolean**</span></span>|<span data-ttu-id="7472f-191">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="7472f-191">**VT_BOOL**</span></span>|
|<span data-ttu-id="7472f-192">**TypeCode. Char**</span><span class="sxs-lookup"><span data-stu-id="7472f-192">**TypeCode.Char**</span></span>|<span data-ttu-id="7472f-193">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="7472f-193">**VT_UI2**</span></span>|
|<span data-ttu-id="7472f-194">**TypeCode. SByte**</span><span class="sxs-lookup"><span data-stu-id="7472f-194">**TypeCode.Sbyte**</span></span>|<span data-ttu-id="7472f-195">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="7472f-195">**VT_I1**</span></span>|
|<span data-ttu-id="7472f-196">**TypeCode. Byte**</span><span class="sxs-lookup"><span data-stu-id="7472f-196">**TypeCode.Byte**</span></span>|<span data-ttu-id="7472f-197">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="7472f-197">**VT_UI1**</span></span>|
|<span data-ttu-id="7472f-198">**TypeCode. Int16**</span><span class="sxs-lookup"><span data-stu-id="7472f-198">**TypeCode.Int16**</span></span>|<span data-ttu-id="7472f-199">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="7472f-199">**VT_I2**</span></span>|
|<span data-ttu-id="7472f-200">**TypeCode. UInt16**</span><span class="sxs-lookup"><span data-stu-id="7472f-200">**TypeCode.UInt16**</span></span>|<span data-ttu-id="7472f-201">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="7472f-201">**VT_UI2**</span></span>|
|<span data-ttu-id="7472f-202">**TypeCode. Int32**</span><span class="sxs-lookup"><span data-stu-id="7472f-202">**TypeCode.Int32**</span></span>|<span data-ttu-id="7472f-203">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="7472f-203">**VT_I4**</span></span>|
|<span data-ttu-id="7472f-204">**TypeCode. UInt32**</span><span class="sxs-lookup"><span data-stu-id="7472f-204">**TypeCode.UInt32**</span></span>|<span data-ttu-id="7472f-205">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="7472f-205">**VT_UI4**</span></span>|
|<span data-ttu-id="7472f-206">**TypeCode. Int64**</span><span class="sxs-lookup"><span data-stu-id="7472f-206">**TypeCode.Int64**</span></span>|<span data-ttu-id="7472f-207">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="7472f-207">**VT_I8**</span></span>|
|<span data-ttu-id="7472f-208">**TypeCode. UInt64**</span><span class="sxs-lookup"><span data-stu-id="7472f-208">**TypeCode.UInt64**</span></span>|<span data-ttu-id="7472f-209">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="7472f-209">**VT_UI8**</span></span>|
|<span data-ttu-id="7472f-210">**TypeCode. Single**</span><span class="sxs-lookup"><span data-stu-id="7472f-210">**TypeCode.Single**</span></span>|<span data-ttu-id="7472f-211">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="7472f-211">**VT_R4**</span></span>|
|<span data-ttu-id="7472f-212">**TypeCode. Double**</span><span class="sxs-lookup"><span data-stu-id="7472f-212">**TypeCode.Double**</span></span>|<span data-ttu-id="7472f-213">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="7472f-213">**VT_R8**</span></span>|
|<span data-ttu-id="7472f-214">**TypeCode. Decimal**</span><span class="sxs-lookup"><span data-stu-id="7472f-214">**TypeCode.Decimal**</span></span>|<span data-ttu-id="7472f-215">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="7472f-215">**VT_DECIMAL**</span></span>|
|<span data-ttu-id="7472f-216">**TypeCode. DateTime**</span><span class="sxs-lookup"><span data-stu-id="7472f-216">**TypeCode.DateTime**</span></span>|<span data-ttu-id="7472f-217">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="7472f-217">**VT_DATE**</span></span>|
|<span data-ttu-id="7472f-218">**TypeCode. String**</span><span class="sxs-lookup"><span data-stu-id="7472f-218">**TypeCode.String**</span></span>|<span data-ttu-id="7472f-219">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="7472f-219">**VT_BSTR**</span></span>|
|<span data-ttu-id="7472f-220">Desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="7472f-220">Not supported.</span></span>|<span data-ttu-id="7472f-221">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="7472f-221">**VT_INT**</span></span>|
|<span data-ttu-id="7472f-222">Desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="7472f-222">Not supported.</span></span>|<span data-ttu-id="7472f-223">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="7472f-223">**VT_UINT**</span></span>|
|<span data-ttu-id="7472f-224">Desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="7472f-224">Not supported.</span></span>|<span data-ttu-id="7472f-225">**VT_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="7472f-225">**VT_ARRAY**</span></span>|
|<span data-ttu-id="7472f-226">Desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="7472f-226">Not supported.</span></span>|<span data-ttu-id="7472f-227">**VT_RECORD**</span><span class="sxs-lookup"><span data-stu-id="7472f-227">**VT_RECORD**</span></span>|
|<span data-ttu-id="7472f-228">Desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="7472f-228">Not supported.</span></span>|<span data-ttu-id="7472f-229">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="7472f-229">**VT_CY**</span></span>|
|<span data-ttu-id="7472f-230">Desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="7472f-230">Not supported.</span></span>|<span data-ttu-id="7472f-231">**VT_VARIANT**</span><span class="sxs-lookup"><span data-stu-id="7472f-231">**VT_VARIANT**</span></span>|

<span data-ttu-id="7472f-232">COM çeşidinin değeri, **IConvertible.to** *tür* arabirimi çağırarak belirlenir **; burada** *tür* , **ıtypbleble. GetTypeCode**'dan döndürülen türe karşılık gelen dönüştürme yordamdır.</span><span class="sxs-lookup"><span data-stu-id="7472f-232">The value of the COM variant is determined by calling the **IConvertible.To** *Type* interface, where **To** *Type* is the conversion routine that corresponds to the type that was returned from **IConvertible.GetTypeCode**.</span></span> <span data-ttu-id="7472f-233">Örneğin, **ıtypbleble. GetTypeCode** 'dan **TypeCode. Double** döndüren bir nesne **VT_R8**türünde bir com değişkeni olarak sıralanır.</span><span class="sxs-lookup"><span data-stu-id="7472f-233">For example, an object that returns **TypeCode.Double** from **IConvertible.GetTypeCode** is marshaled as a COM variant of type **VT_R8**.</span></span> <span data-ttu-id="7472f-234">**Iverbleface** arabirimine atama yaparak ve metodunu çağırarak, değişkenin DEĞERINI (com çeşidinin **dblVal** alanında depolanır) elde edebilirsiniz <xref:System.IConvertible.ToDouble%2A> .</span><span class="sxs-lookup"><span data-stu-id="7472f-234">You can obtain the value of the variant (stored in the **dblVal** field of the COM variant) by casting to the **IConvertible** interface and calling the <xref:System.IConvertible.ToDouble%2A> method.</span></span>

## <a name="marshaling-variant-to-object"></a><span data-ttu-id="7472f-235">Değişkeni nesneye sıralama</span><span class="sxs-lookup"><span data-stu-id="7472f-235">Marshaling Variant to Object</span></span>

<span data-ttu-id="7472f-236">Bir değişkeni bir nesneye, türü ve bazen değeri, oluşturulan değişkenin değerini, üretilen nesnenin türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="7472f-236">When marshaling a variant to an object, the type, and sometimes the value, of the marshaled variant determines the type of object produced.</span></span> <span data-ttu-id="7472f-237">Aşağıdaki tabloda her bir varyant türü ve COM 'dan .NET Framework bir varyant geçirildiğinde sıralayıcı tarafından oluşturulan ilgili nesne türü tanımlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7472f-237">The following table identifies each variant type and the corresponding object type that the marshaler creates when a variant is passed from COM to the .NET Framework.</span></span>

|<span data-ttu-id="7472f-238">COM varyant türü</span><span class="sxs-lookup"><span data-stu-id="7472f-238">COM variant type</span></span>|<span data-ttu-id="7472f-239">Nesne türü</span><span class="sxs-lookup"><span data-stu-id="7472f-239">Object type</span></span>|
|----------------------|-----------------|
|<span data-ttu-id="7472f-240">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="7472f-240">**VT_EMPTY**</span></span>|<span data-ttu-id="7472f-241">Null nesne başvurusu (Visual Basic**hiçbir şey** ).</span><span class="sxs-lookup"><span data-stu-id="7472f-241">Null object reference (**Nothing** in Visual Basic).</span></span>|
|<span data-ttu-id="7472f-242">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="7472f-242">**VT_NULL**</span></span>|<xref:System.DBNull?displayProperty=nameWithType>|
|<span data-ttu-id="7472f-243">**VT_DISPATCH**</span><span class="sxs-lookup"><span data-stu-id="7472f-243">**VT_DISPATCH**</span></span>|<span data-ttu-id="7472f-244">**System. __ComObject** veya (pdispVal = = null) ise null</span><span class="sxs-lookup"><span data-stu-id="7472f-244">**System.__ComObject** or null if (pdispVal == null)</span></span>|
|<span data-ttu-id="7472f-245">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="7472f-245">**VT_UNKNOWN**</span></span>|<span data-ttu-id="7472f-246">**System. __ComObject** veya (punkVal = = null) ise null</span><span class="sxs-lookup"><span data-stu-id="7472f-246">**System.__ComObject** or null if (punkVal == null)</span></span>|
|<span data-ttu-id="7472f-247">**VT_ERROR**</span><span class="sxs-lookup"><span data-stu-id="7472f-247">**VT_ERROR**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|<span data-ttu-id="7472f-248">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="7472f-248">**VT_BOOL**</span></span>|<xref:System.Boolean?displayProperty=nameWithType>|
|<span data-ttu-id="7472f-249">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="7472f-249">**VT_I1**</span></span>|<xref:System.SByte?displayProperty=nameWithType>|
|<span data-ttu-id="7472f-250">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="7472f-250">**VT_UI1**</span></span>|<xref:System.Byte?displayProperty=nameWithType>|
|<span data-ttu-id="7472f-251">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="7472f-251">**VT_I2**</span></span>|<xref:System.Int16?displayProperty=nameWithType>|
|<span data-ttu-id="7472f-252">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="7472f-252">**VT_UI2**</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|
|<span data-ttu-id="7472f-253">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="7472f-253">**VT_I4**</span></span>|<xref:System.Int32?displayProperty=nameWithType>|
|<span data-ttu-id="7472f-254">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="7472f-254">**VT_UI4**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|<span data-ttu-id="7472f-255">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="7472f-255">**VT_I8**</span></span>|<xref:System.Int64?displayProperty=nameWithType>|
|<span data-ttu-id="7472f-256">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="7472f-256">**VT_UI8**</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|
|<span data-ttu-id="7472f-257">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="7472f-257">**VT_R4**</span></span>|<xref:System.Single?displayProperty=nameWithType>|
|<span data-ttu-id="7472f-258">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="7472f-258">**VT_R8**</span></span>|<xref:System.Double?displayProperty=nameWithType>|
|<span data-ttu-id="7472f-259">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="7472f-259">**VT_DECIMAL**</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|
|<span data-ttu-id="7472f-260">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="7472f-260">**VT_DATE**</span></span>|<xref:System.DateTime?displayProperty=nameWithType>|
|<span data-ttu-id="7472f-261">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="7472f-261">**VT_BSTR**</span></span>|<xref:System.String?displayProperty=nameWithType>|
|<span data-ttu-id="7472f-262">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="7472f-262">**VT_INT**</span></span>|<xref:System.Int32?displayProperty=nameWithType>|
|<span data-ttu-id="7472f-263">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="7472f-263">**VT_UINT**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|<span data-ttu-id="7472f-264">**VT_ARRAY** &#124; **VT_**\*</span><span class="sxs-lookup"><span data-stu-id="7472f-264">**VT_ARRAY** &#124; **VT_**\*</span></span>|<xref:System.Array?displayProperty=nameWithType>|
|<span data-ttu-id="7472f-265">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="7472f-265">**VT_CY**</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|
|<span data-ttu-id="7472f-266">**VT_RECORD**</span><span class="sxs-lookup"><span data-stu-id="7472f-266">**VT_RECORD**</span></span>|<span data-ttu-id="7472f-267">Karşılık gelen paketlenmiş değer türü.</span><span class="sxs-lookup"><span data-stu-id="7472f-267">Corresponding boxed value type.</span></span>|
|<span data-ttu-id="7472f-268">**VT_VARIANT**</span><span class="sxs-lookup"><span data-stu-id="7472f-268">**VT_VARIANT**</span></span>|<span data-ttu-id="7472f-269">Desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="7472f-269">Not supported.</span></span>|

<span data-ttu-id="7472f-270">COM 'dan yönetilen koda geçirilen ve sonra COM 'a geri dönüş değişken türleri, çağrının süresi boyunca aynı varyant türünü korumayabilir.</span><span class="sxs-lookup"><span data-stu-id="7472f-270">Variant types passed from COM to managed code and then back to COM might not retain the same variant type for the duration of the call.</span></span> <span data-ttu-id="7472f-271">**VT_DISPATCH** türünde BIR değişken COM 'tan .NET Framework geçirildiğinde ne olacağını düşünün.</span><span class="sxs-lookup"><span data-stu-id="7472f-271">Consider what happens when a variant of type **VT_DISPATCH** is passed from COM to the .NET Framework.</span></span> <span data-ttu-id="7472f-272">Sıralama sırasında, değişken öğesine dönüştürülür <xref:System.Object?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="7472f-272">During marshaling, the variant is converted to a <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7472f-273">**Nesne** daha sonra com 'a geri geçirilirse, **VT_UNKNOWN**türünde bir varyanta geri getirilir.</span><span class="sxs-lookup"><span data-stu-id="7472f-273">If the **Object** is then passed back to COM, it is marshaled back to a variant of type **VT_UNKNOWN**.</span></span> <span data-ttu-id="7472f-274">Bir nesne yönetilen koddan COM 'a sıralandığınızda üretilen varyantın, başlangıçta nesneyi oluşturmak için kullanılan değişkenle aynı türde olacağını garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="7472f-274">There is no guarantee that the variant produced when an object is marshaled from managed code to COM will be the same type as the variant initially used to produce the object.</span></span>

## <a name="marshaling-byref-variants"></a><span data-ttu-id="7472f-275">ByRef türevlerini sıralama</span><span class="sxs-lookup"><span data-stu-id="7472f-275">Marshaling ByRef Variants</span></span>

<span data-ttu-id="7472f-276">Varyantlar değere veya başvuruya göre geçirilebilir olsa da, değişken içeriğinin değer yerine başvuruya göre geçtiğini göstermek için **VT_BYREF** bayrağı herhangi bir varyant türüyle birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7472f-276">Although variants themselves can be passed by value or by reference, the **VT_BYREF** flag can also be used with any variant type to indicate that the contents of the variant are being passed by reference instead of by value.</span></span> <span data-ttu-id="7472f-277">Başvuruya göre sıralama ve bir değişkeni **VT_BYREF** bayrak kümesiyle sıralama arasındaki fark kafa karıştırıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="7472f-277">The difference between marshaling variants by reference and marshaling a variant with the **VT_BYREF** flag set can be confusing.</span></span> <span data-ttu-id="7472f-278">Aşağıdaki çizim farklılıkları açıklığa kavuşturulur:</span><span class="sxs-lookup"><span data-stu-id="7472f-278">The following illustration clarifies the differences:</span></span>

<span data-ttu-id="7472f-279">![Yığına geçilen varyansı gösteren diyagram.](./media/default-marshaling-for-objects/interop-variant-passed-value-reference.gif)</span><span class="sxs-lookup"><span data-stu-id="7472f-279">![Diagram that shows variant passed on the stack.](./media/default-marshaling-for-objects/interop-variant-passed-value-reference.gif)</span></span>
<span data-ttu-id="7472f-280">Değer ve başvuruya göre geçirilen çeşitler</span><span class="sxs-lookup"><span data-stu-id="7472f-280">Variants passed by value and by reference</span></span>

<span data-ttu-id="7472f-281">**Nesneleri ve çeşitlemeleri değere göre hazırlama için varsayılan davranış**</span><span class="sxs-lookup"><span data-stu-id="7472f-281">**Default behavior for marshaling objects and variants by value**</span></span>

- <span data-ttu-id="7472f-282">Nesneleri yönetilen koddan COM 'a geçirirken nesnenin içeriği sıralayıcı tarafından oluşturulan yeni bir varyanta kopyalanır ve bu, [nesneyi değişken olarak hazırlama](#marshaling-object-to-variant)bölümünde tanımlanan kurallar kullanılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="7472f-282">When passing objects from managed code to COM, the contents of the object are copied into a new variant created by the marshaler, using the rules defined in [Marshaling Object to Variant](#marshaling-object-to-variant).</span></span> <span data-ttu-id="7472f-283">Yönetilmeyen taraftaki VARIANT üzerinde yapılan değişiklikler, çağrıdan döndürülen özgün nesneye geri yayılmaz.</span><span class="sxs-lookup"><span data-stu-id="7472f-283">Changes made to the variant on the unmanaged side are not propagated back to the original object on return from the call.</span></span>

- <span data-ttu-id="7472f-284">Değişkenleri COM 'dan yönetilen koda geçirirken, varyantın içeriği, [değişken sıralama](#marshaling-variant-to-object)içinde tanımlanan kuralları kullanarak yeni oluşturulan bir nesneye kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="7472f-284">When passing variants from COM to managed code, the contents of the variant are copied to a newly created object, using the rules defined in [Marshaling Variant to Object](#marshaling-variant-to-object).</span></span> <span data-ttu-id="7472f-285">Yönetilen taraftaki nesnede yapılan değişiklikler, çağrıdan döndürülen özgün varyanta geri yayılmaz.</span><span class="sxs-lookup"><span data-stu-id="7472f-285">Changes made to the object on the managed side are not propagated back to the original variant on return from the call.</span></span>

<span data-ttu-id="7472f-286">**Başvuruya göre nesneleri ve türevleri hazırlama için varsayılan davranış**</span><span class="sxs-lookup"><span data-stu-id="7472f-286">**Default behavior for marshaling objects and variants by reference**</span></span>

<span data-ttu-id="7472f-287">Değişiklikleri çağırana geri yaymak için, parametrelerin başvuruya göre geçirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="7472f-287">To propagate changes back to the caller, the parameters must be passed by reference.</span></span> <span data-ttu-id="7472f-288">Örneğin, parametreleri başvuruya göre geçirmek için C# ' deki **ref** anahtar sözcüğünü (veya Visual Basic yönetilen kodda **ByRef** ) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7472f-288">For example, you can use the **ref** keyword in C# (or **ByRef** in Visual Basic managed code) to pass parameters by reference.</span></span> <span data-ttu-id="7472f-289">COM 'da, başvuru parametreleri \*\*değişken \* \*\*gibi bir işaretçi kullanılarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="7472f-289">In COM, reference parameters are passed using a pointer such as a **variant \***.</span></span>

- <span data-ttu-id="7472f-290">Bir nesneyi bir COM 'a başvuruya göre geçirirken Sıralayıcı yeni bir değişken oluşturur ve Nesne başvurusunun içeriğini çağrı yapılmadan önce varyanta kopyalar.</span><span class="sxs-lookup"><span data-stu-id="7472f-290">When passing an object to COM by reference, the marshaler creates a new variant and copies the contents of the object reference into the variant before the call is made.</span></span> <span data-ttu-id="7472f-291">Değişken, kullanıcının varyantın içeriğini değiştirmek için boş olduğu yönetilmeyen işleve geçirilir.</span><span class="sxs-lookup"><span data-stu-id="7472f-291">The variant is passed to the unmanaged function where the user is free to change the contents of the variant.</span></span> <span data-ttu-id="7472f-292">Çağrıdan geri döndüğünüzde, yönetilmeyen taraftaki VARIANT üzerinde yapılan tüm değişiklikler özgün nesneye geri yayılır.</span><span class="sxs-lookup"><span data-stu-id="7472f-292">On return from the call, any changes made to the variant on the unmanaged side are propagated back to the original object.</span></span> <span data-ttu-id="7472f-293">Değişken türü, çağrıya geçirilen varyantın türünden farklıysa, değişiklikler farklı türdeki bir nesneye geri yayılır.</span><span class="sxs-lookup"><span data-stu-id="7472f-293">If the type of the variant differs from the type of the variant passed to the call, then the changes are propagated back to an object of a different type.</span></span> <span data-ttu-id="7472f-294">Diğer bir deyişle, çağrıya geçirilen nesnenin türü, çağrıdan döndürülen nesne türünden farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="7472f-294">That is, the type of the object passed into the call can differ from the type of the object returned from the call.</span></span>

- <span data-ttu-id="7472f-295">Başvuruya göre yönetilen koda bir varyant geçirirken, Sıralayıcı yeni bir nesne oluşturur ve çağrıyı yapmadan önce değişkenin içeriğini nesnesine kopyalar.</span><span class="sxs-lookup"><span data-stu-id="7472f-295">When passing a variant to managed code by reference, the marshaler creates a new object and copies the contents of the variant into the object before making the call.</span></span> <span data-ttu-id="7472f-296">Nesnesine bir başvuru, kullanıcının nesneyi değiştirmek için ücretsiz olarak yönetilen işleve geçirilir.</span><span class="sxs-lookup"><span data-stu-id="7472f-296">A reference to the object is passed to the managed function, where the user is free to change the object.</span></span> <span data-ttu-id="7472f-297">Çağrıdan geri döndüğünüzde, başvurulan nesnede yapılan tüm değişiklikler özgün varyanta geri yayılır.</span><span class="sxs-lookup"><span data-stu-id="7472f-297">On return from the call, any changes made to the referenced object are propagated back to the original variant.</span></span> <span data-ttu-id="7472f-298">Nesnenin türü, çağrıya geçirilen nesne türünden farklıysa, özgün varyantın türü değiştirilir ve değer varyanta geri yayılır...</span><span class="sxs-lookup"><span data-stu-id="7472f-298">If the type of the object differs from the type of the object passed in to the call, the type of the original variant is changed and the value is propagated back into the variant.</span></span> <span data-ttu-id="7472f-299">Yine, çağrıya geçirilen varyantın türü, çağrıdan döndürülen VARIANT türünden farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="7472f-299">Again, the type of the variant passed into the call can differ from the type of the variant returned from the call.</span></span>

 <span data-ttu-id="7472f-300">**VT_BYREF bayrak kümesiyle bir değişkeni hazırlama için varsayılan davranış**</span><span class="sxs-lookup"><span data-stu-id="7472f-300">**Default behavior for marshaling a variant with the VT_BYREF flag set**</span></span>

- <span data-ttu-id="7472f-301">Değere göre yönetilen koda geçirilen bir değişken, değişkenin bir değer yerine bir başvuru içerdiğini göstermek için **VT_BYREF** bayrak kümesine sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="7472f-301">A variant being passed to managed code by value can have the **VT_BYREF** flag set to indicate that the variant contains a reference instead of a value.</span></span> <span data-ttu-id="7472f-302">Bu durumda, değişken değer ile geçirildiğinden değişken hala bir nesne olarak sıralanır.</span><span class="sxs-lookup"><span data-stu-id="7472f-302">In this case, the variant is still marshaled to an object because the variant is being passed by value.</span></span> <span data-ttu-id="7472f-303">Sıralayıcı, varyantın içeriğini otomatik olarak referans yapar ve çağrıyı yapmadan önce yeni oluşturulan bir nesneye kopyalar.</span><span class="sxs-lookup"><span data-stu-id="7472f-303">The marshaler automatically dereferences the contents of the variant and copies it into a newly created object before making the call.</span></span> <span data-ttu-id="7472f-304">Nesne daha sonra yönetilen işleve geçirilir; Ancak, çağrıdan dönüşte, nesne özgün varyanta geri yayılmaz.</span><span class="sxs-lookup"><span data-stu-id="7472f-304">The object is then passed into the managed function; however, on return from the call, the object is not propagated back into the original variant.</span></span> <span data-ttu-id="7472f-305">Yönetilen nesnede yapılan değişiklikler kaybedilir.</span><span class="sxs-lookup"><span data-stu-id="7472f-305">Changes made to the managed object are lost.</span></span>

  > [!CAUTION]
  > <span data-ttu-id="7472f-306">Değişken **VT_BYREF** bayrak kümesine sahip olsa bile, değer tarafından geçirilen bir değişkenin değerini değiştirme yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="7472f-306">There is no way to change the value of a variant passed by value, even if the variant has the **VT_BYREF** flag set.</span></span>

- <span data-ttu-id="7472f-307">Başvuruya göre yönetilen koda geçirilen bir değişken, değişkenin başka bir başvuru içerdiğini belirtmek için de **VT_BYREF** bayrak verebilir.</span><span class="sxs-lookup"><span data-stu-id="7472f-307">A variant being passed to managed code by reference can also have the **VT_BYREF** flag set to indicate that the variant contains another reference.</span></span> <span data-ttu-id="7472f-308">Varsa, değişken başvuruya göre geçirildiğinden bir **başvuru** nesnesine göre sıralanır.</span><span class="sxs-lookup"><span data-stu-id="7472f-308">If it does, the variant is marshaled to a **ref** object because the variant is being passed by reference.</span></span> <span data-ttu-id="7472f-309">Sıralayıcı, varyantın içeriğini otomatik olarak referans yapar ve çağrıyı yapmadan önce yeni oluşturulan bir nesneye kopyalar.</span><span class="sxs-lookup"><span data-stu-id="7472f-309">The marshaler automatically dereferences the contents of the variant and copies it into a newly created object before making the call.</span></span> <span data-ttu-id="7472f-310">Çağrıdan dönüşte, nesnenin değeri yalnızca nesnenin geçirildiği nesneyle aynı türde olması durumunda, özgün varyant içindeki başvuruya geri yayılır.</span><span class="sxs-lookup"><span data-stu-id="7472f-310">On return from the call, the value of the object is propagated back to the reference within the original variant only if the object is the same type as the object passed in.</span></span> <span data-ttu-id="7472f-311">Diğer bir deyişle, yayma **VT_BYREF** bayrak kümesiyle bir varyant türünü değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="7472f-311">That is, propagation does not change the type of a variant with the **VT_BYREF** flag set.</span></span> <span data-ttu-id="7472f-312">Çağrı sırasında nesnenin türü değiştirilirse, <xref:System.InvalidCastException> çağrıdan döndürülen bir meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="7472f-312">If the type of the object is changed during the call, an <xref:System.InvalidCastException> occurs on return from the call.</span></span>

<span data-ttu-id="7472f-313">Aşağıdaki tabloda, çeşitler ve nesneler için yayma kuralları özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="7472f-313">The following table summarizes the propagation rules for variants and objects.</span></span>

|<span data-ttu-id="7472f-314">Kaynak</span><span class="sxs-lookup"><span data-stu-id="7472f-314">From</span></span>|<span data-ttu-id="7472f-315">Amaç</span><span class="sxs-lookup"><span data-stu-id="7472f-315">To</span></span>|<span data-ttu-id="7472f-316">Geri yayılan değişiklikler</span><span class="sxs-lookup"><span data-stu-id="7472f-316">Changes propagated back</span></span>|
|----------|--------|-----------------------------|
|<span data-ttu-id="7472f-317">**Değişken**  *v*</span><span class="sxs-lookup"><span data-stu-id="7472f-317">**Variant**  *v*</span></span>|<span data-ttu-id="7472f-318">**Nesne**  *o*</span><span class="sxs-lookup"><span data-stu-id="7472f-318">**Object**  *o*</span></span>|<span data-ttu-id="7472f-319">Asla</span><span class="sxs-lookup"><span data-stu-id="7472f-319">Never</span></span>|
|<span data-ttu-id="7472f-320">**Nesne**  *o*</span><span class="sxs-lookup"><span data-stu-id="7472f-320">**Object**  *o*</span></span>|<span data-ttu-id="7472f-321">**Değişken**  *v*</span><span class="sxs-lookup"><span data-stu-id="7472f-321">**Variant**  *v*</span></span>|<span data-ttu-id="7472f-322">Asla</span><span class="sxs-lookup"><span data-stu-id="7472f-322">Never</span></span>|
|<span data-ttu-id="7472f-323">**Değişken** ***\**** *BD*     </span><span class="sxs-lookup"><span data-stu-id="7472f-323">**Variant**   ***\****  *pv*</span></span>|<span data-ttu-id="7472f-324">**Başvuru nesnesi**  *o*</span><span class="sxs-lookup"><span data-stu-id="7472f-324">**Ref Object**  *o*</span></span>|<span data-ttu-id="7472f-325">Her zaman</span><span class="sxs-lookup"><span data-stu-id="7472f-325">Always</span></span>|
|<span data-ttu-id="7472f-326">**Başvuru nesnesi**  *o*</span><span class="sxs-lookup"><span data-stu-id="7472f-326">**Ref object**  *o*</span></span>|<span data-ttu-id="7472f-327">**Değişken** ***\**** *BD*     </span><span class="sxs-lookup"><span data-stu-id="7472f-327">**Variant**   ***\****  *pv*</span></span>|<span data-ttu-id="7472f-328">Her zaman</span><span class="sxs-lookup"><span data-stu-id="7472f-328">Always</span></span>|
|<span data-ttu-id="7472f-329">**Değişken**  *v* **(VT_BYREF** *&#124;* **VT_ \* )**</span><span class="sxs-lookup"><span data-stu-id="7472f-329">**Variant**  *v* **(VT_BYREF** *&#124;* **VT_\*)**</span></span>|<span data-ttu-id="7472f-330">**Nesne**  *o*</span><span class="sxs-lookup"><span data-stu-id="7472f-330">**Object**  *o*</span></span>|<span data-ttu-id="7472f-331">Asla</span><span class="sxs-lookup"><span data-stu-id="7472f-331">Never</span></span>|
|<span data-ttu-id="7472f-332">**Değişken**  *v* **(VT_BYREF** *&#124;* **VT_)**</span><span class="sxs-lookup"><span data-stu-id="7472f-332">**Variant**  *v* **(VT_BYREF** *&#124;* **VT_)**</span></span>|<span data-ttu-id="7472f-333">**Başvuru nesnesi**  *o*</span><span class="sxs-lookup"><span data-stu-id="7472f-333">**Ref Object**  *o*</span></span>|<span data-ttu-id="7472f-334">Yalnızca tür değişmemiştir.</span><span class="sxs-lookup"><span data-stu-id="7472f-334">Only if the type has not changed.</span></span>|

## <a name="see-also"></a><span data-ttu-id="7472f-335">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7472f-335">See also</span></span>

- [<span data-ttu-id="7472f-336">Varsayılan Sıralama Davranışı</span><span class="sxs-lookup"><span data-stu-id="7472f-336">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
- [<span data-ttu-id="7472f-337">Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler</span><span class="sxs-lookup"><span data-stu-id="7472f-337">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- <span data-ttu-id="7472f-338">[Yönlü öznitelikler](/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7472f-338">[Directional Attributes](/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span></span>
- [<span data-ttu-id="7472f-339">Kopyalama ve Sabitleme</span><span class="sxs-lookup"><span data-stu-id="7472f-339">Copying and Pinning</span></span>](copying-and-pinning.md)
