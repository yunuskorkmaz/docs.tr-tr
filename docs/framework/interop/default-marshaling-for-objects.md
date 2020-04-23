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
ms.openlocfilehash: e0de715a3ed33eedf212fc3e0e9930c9cbaa0a38
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123586"
---
# <a name="default-marshaling-for-objects"></a><span data-ttu-id="2fbb0-102">Nesneler için Varsayılan Hazırlama</span><span class="sxs-lookup"><span data-stu-id="2fbb0-102">Default Marshaling for Objects</span></span>

<span data-ttu-id="2fbb0-103">Olarak <xref:System.Object?displayProperty=nameWithType> yazılan parametreler ve alanlar, aşağıdaki türlerden biri olarak yönetilmeyen koda gösterilebilir:</span><span class="sxs-lookup"><span data-stu-id="2fbb0-103">Parameters and fields typed as <xref:System.Object?displayProperty=nameWithType> can be exposed to unmanaged code as one of the following types:</span></span>

- <span data-ttu-id="2fbb0-104">Nesne bir parametre olduğunda bir değişken.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-104">A variant when the object is a parameter.</span></span>

- <span data-ttu-id="2fbb0-105">Nesne bir yapı alanı olduğunda arabirim.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-105">An interface when the object is a structure field.</span></span>

<span data-ttu-id="2fbb0-106">Yalnızca COM birlikte çalışması nesne türleri için sıralama destekler.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-106">Only COM interop supports marshaling for object types.</span></span> <span data-ttu-id="2fbb0-107">Varsayılan davranış, nesneleri COM türevlerine sıralamakta kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-107">The default behavior is to marshal objects to COM variants.</span></span> <span data-ttu-id="2fbb0-108">Bu kurallar yalnızca tür **nesnesi** için geçerlidir ve **Object** sınıfından türetilmiş türü kesin belirlenmiş nesneler için uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-108">These rules apply only to the type **Object** and do not apply to strongly typed objects that derive from the **Object** class.</span></span>

## <a name="marshaling-options"></a><span data-ttu-id="2fbb0-109">Sıralama seçenekleri</span><span class="sxs-lookup"><span data-stu-id="2fbb0-109">Marshaling Options</span></span>

<span data-ttu-id="2fbb0-110">Aşağıdaki tabloda, **nesne** veri türü için sıralama seçenekleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-110">The following table shows the marshaling options for the **Object** data type.</span></span> <span data-ttu-id="2fbb0-111"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Özniteliği nesneleri sıralamak için <xref:System.Runtime.InteropServices.UnmanagedType> birkaç numaralandırma değeri sağlar.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-111">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal objects.</span></span>

|<span data-ttu-id="2fbb0-112">Sabit listesi türü</span><span class="sxs-lookup"><span data-stu-id="2fbb0-112">Enumeration type</span></span>|<span data-ttu-id="2fbb0-113">Yönetilmeyen biçimin açıklaması</span><span class="sxs-lookup"><span data-stu-id="2fbb0-113">Description of unmanaged format</span></span>|
|----------------------|-------------------------------------|
|<span data-ttu-id="2fbb0-114">**UnmanagedType. struct**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-114">**UnmanagedType.Struct**</span></span><br /><br /> <span data-ttu-id="2fbb0-115">(parametreler için varsayılan)</span><span class="sxs-lookup"><span data-stu-id="2fbb0-115">(default for parameters)</span></span>|<span data-ttu-id="2fbb0-116">COM stili bir varyant.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-116">A COM-style variant.</span></span>|
|<span data-ttu-id="2fbb0-117">**UnmanagedType. Interface**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-117">**UnmanagedType.Interface**</span></span>|<span data-ttu-id="2fbb0-118">Mümkünse **IDispatch** arabirimi; Aksi takdirde, bir **IUnknown** arabirimi.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-118">An **IDispatch** interface, if possible; otherwise, an **IUnknown** interface.</span></span>|
|<span data-ttu-id="2fbb0-119">**UnmanagedType. IUnknown**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-119">**UnmanagedType.IUnknown**</span></span><br /><br /> <span data-ttu-id="2fbb0-120">(alanlar için varsayılan)</span><span class="sxs-lookup"><span data-stu-id="2fbb0-120">(default for fields)</span></span>|<span data-ttu-id="2fbb0-121">Bir **IUnknown** arabirimi.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-121">An **IUnknown** interface.</span></span>|
|<span data-ttu-id="2fbb0-122">**UnmanagedType. IDispatch**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-122">**UnmanagedType.IDispatch**</span></span>|<span data-ttu-id="2fbb0-123">Bir **IDispatch** arabirimi.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-123">An **IDispatch** interface.</span></span>|

<span data-ttu-id="2fbb0-124">Aşağıdaki örnek için `MarshalObject`yönetilen arabirim tanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-124">The following example shows the managed interface definition for `MarshalObject`.</span></span>

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

<span data-ttu-id="2fbb0-125">Aşağıdaki kod, `MarshalObject` arabirimi bir tür kitaplığına dışarı aktarır.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-125">The following code exports the `MarshalObject` interface to a type library.</span></span>

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
> <span data-ttu-id="2fbb0-126">Birlikte çalışma sıralayıcısı, çağrıdan sonra değişken içinde tüm ayrılmış nesneleri otomatik olarak boşaltır.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-126">The interop marshaler automatically frees any allocated object inside the variant after the call.</span></span>

<span data-ttu-id="2fbb0-127">Aşağıdaki örnek, biçimli bir değer türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-127">The following example shows a formatted value type.</span></span>

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

<span data-ttu-id="2fbb0-128">Aşağıdaki kod, biçimli türü bir tür kitaplığına dışarı aktarır.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-128">The following code exports the formatted type to a type library.</span></span>

```cpp
struct ObjectHolder {
   VARIANT o1;
   IDispatch *o2;
}
```

## <a name="marshaling-object-to-interface"></a><span data-ttu-id="2fbb0-129">Nesne arabirime sıralanıyor</span><span class="sxs-lookup"><span data-stu-id="2fbb0-129">Marshaling Object to Interface</span></span>

<span data-ttu-id="2fbb0-130">Bir nesne bir arabirim olarak COM 'a sunulduğunda, bu arabirim yönetilen tür <xref:System.Object> için sınıf arabirimidir ( **_object** arabirimi).</span><span class="sxs-lookup"><span data-stu-id="2fbb0-130">When an object is exposed to COM as an interface, that interface is the class interface for the managed type <xref:System.Object> (the **_Object** interface).</span></span> <span data-ttu-id="2fbb0-131">Bu arabirim, sonuç türü kitaplığında **IDispatch** bir IDispatch<xref:System.Runtime.InteropServices.UnmanagedType>() veya **IUnknown** (**UnmanagedType. IUnknown**) olarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-131">This interface is typed as an **IDispatch** (<xref:System.Runtime.InteropServices.UnmanagedType>) or an **IUnknown** (**UnmanagedType.IUnknown**) in the resulting type library.</span></span> <span data-ttu-id="2fbb0-132">COM istemcileri yönetilen sınıfın veya **_object** arabirimi aracılığıyla türetilmiş sınıfları tarafından uygulanan herhangi bir üyenin üyelerini dinamik olarak çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-132">COM clients can dynamically invoke the members of the managed class or any members implemented by its derived classes through the **_Object** interface.</span></span> <span data-ttu-id="2fbb0-133">İstemci Ayrıca, yönetilen tür tarafından açıkça uygulanan başka bir arabirim elde etmek için **QueryInterface** 'i çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-133">The client can also call **QueryInterface** to obtain any other interface explicitly implemented by the managed type.</span></span>

## <a name="marshaling-object-to-variant"></a><span data-ttu-id="2fbb0-134">Nesne varyanta sıralanıyor</span><span class="sxs-lookup"><span data-stu-id="2fbb0-134">Marshaling Object to Variant</span></span>

<span data-ttu-id="2fbb0-135">Bir nesne bir varyanta sıralanışında, iç varyant türü çalışma zamanında aşağıdaki kurallara göre belirlenir:</span><span class="sxs-lookup"><span data-stu-id="2fbb0-135">When an object is marshaled to a variant, the internal variant type is determined at run time, based on the following rules:</span></span>

- <span data-ttu-id="2fbb0-136">Nesne başvurusu null ise (Visual Basic**hiçbir şey** ), nesne **VT_EMPTY**türünde bir değişkenle sıralanır.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-136">If the object reference is null (**Nothing** in Visual Basic), the object is marshaled to a variant of type **VT_EMPTY**.</span></span>

- <span data-ttu-id="2fbb0-137">Nesne, aşağıdaki tabloda listelenen herhangi bir türde bir örnek ise, sonuçta elde edilen varyant türü Sıralayıcı içinde yerleşik olan ve tabloda gösterilen kurallara göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-137">If the object is an instance of any type listed in the following table, the resulting variant type is determined by the rules built into the marshaler and shown in the table.</span></span>

- <span data-ttu-id="2fbb0-138">Sıralama davranışını açıkça kontrol etmeniz gereken diğer nesneler <xref:System.IConvertible> arabirimi uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-138">Other objects that need to explicitly control the marshaling behavior can implement the <xref:System.IConvertible> interface.</span></span> <span data-ttu-id="2fbb0-139">Bu durumda, değişken türü <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> yönteminden döndürülen tür koduna göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-139">In that case, the variant type is determined by the type code returned from the <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="2fbb0-140">Aksi takdirde, nesne **VT_UNKNOWN**türünde bir değişken olarak sıralanır.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-140">Otherwise, the object is marshaled as a variant of type **VT_UNKNOWN**.</span></span>

### <a name="marshaling-system-types-to-variant"></a><span data-ttu-id="2fbb0-141">Sistem türlerini varyanta sıralama</span><span class="sxs-lookup"><span data-stu-id="2fbb0-141">Marshaling System Types to Variant</span></span>

<span data-ttu-id="2fbb0-142">Aşağıdaki tabloda, yönetilen nesne türleri ve bunlara karşılık gelen COM Variant türleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-142">The following table shows managed object types and their corresponding COM variant types.</span></span> <span data-ttu-id="2fbb0-143">Bu türler yalnızca çağrılan metodun imzası tür <xref:System.Object?displayProperty=nameWithType>olduğunda dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-143">These types are converted only when the signature of the method being called is of type <xref:System.Object?displayProperty=nameWithType>.</span></span>

|<span data-ttu-id="2fbb0-144">Nesne türü</span><span class="sxs-lookup"><span data-stu-id="2fbb0-144">Object type</span></span>|<span data-ttu-id="2fbb0-145">COM varyant türü</span><span class="sxs-lookup"><span data-stu-id="2fbb0-145">COM variant type</span></span>|
|-----------------|----------------------|
|<span data-ttu-id="2fbb0-146">Null nesne başvurusu (Visual Basic**hiçbir şey** ).</span><span class="sxs-lookup"><span data-stu-id="2fbb0-146">Null object reference (**Nothing** in Visual Basic).</span></span>|<span data-ttu-id="2fbb0-147">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-147">**VT_EMPTY**</span></span>|
|<xref:System.DBNull?displayProperty=nameWithType>|<span data-ttu-id="2fbb0-148">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-148">**VT_NULL**</span></span>|
|<xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>|<span data-ttu-id="2fbb0-149">**VT_ERROR**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-149">**VT_ERROR**</span></span>|
|<xref:System.Reflection.Missing?displayProperty=nameWithType>|<span data-ttu-id="2fbb0-150">**E_PARAMNOTFOUND** **VT_ERROR**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-150">**VT_ERROR** with **E_PARAMNOTFOUND**</span></span>|
|<xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>|<span data-ttu-id="2fbb0-151">**VT_DISPATCH**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-151">**VT_DISPATCH**</span></span>|
|<xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>|<span data-ttu-id="2fbb0-152">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-152">**VT_UNKNOWN**</span></span>|
|<xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>|<span data-ttu-id="2fbb0-153">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-153">**VT_CY**</span></span>|
|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="2fbb0-154">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-154">**VT_BOOL**</span></span>|
|<xref:System.SByte?displayProperty=nameWithType>|<span data-ttu-id="2fbb0-155">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-155">**VT_I1**</span></span>|
|<xref:System.Byte?displayProperty=nameWithType>|<span data-ttu-id="2fbb0-156">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-156">**VT_UI1**</span></span>|
|<xref:System.Int16?displayProperty=nameWithType>|<span data-ttu-id="2fbb0-157">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-157">**VT_I2**</span></span>|
|<xref:System.UInt16?displayProperty=nameWithType>|<span data-ttu-id="2fbb0-158">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-158">**VT_UI2**</span></span>|
|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="2fbb0-159">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-159">**VT_I4**</span></span>|
|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="2fbb0-160">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-160">**VT_UI4**</span></span>|
|<xref:System.Int64?displayProperty=nameWithType>|<span data-ttu-id="2fbb0-161">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-161">**VT_I8**</span></span>|
|<xref:System.UInt64?displayProperty=nameWithType>|<span data-ttu-id="2fbb0-162">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-162">**VT_UI8**</span></span>|
|<xref:System.Single?displayProperty=nameWithType>|<span data-ttu-id="2fbb0-163">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-163">**VT_R4**</span></span>|
|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="2fbb0-164">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-164">**VT_R8**</span></span>|
|<xref:System.Decimal?displayProperty=nameWithType>|<span data-ttu-id="2fbb0-165">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-165">**VT_DECIMAL**</span></span>|
|<xref:System.DateTime?displayProperty=nameWithType>|<span data-ttu-id="2fbb0-166">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-166">**VT_DATE**</span></span>|
|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="2fbb0-167">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-167">**VT_BSTR**</span></span>|
|<xref:System.IntPtr?displayProperty=nameWithType>|<span data-ttu-id="2fbb0-168">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-168">**VT_INT**</span></span>|
|<xref:System.UIntPtr?displayProperty=nameWithType>|<span data-ttu-id="2fbb0-169">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-169">**VT_UINT**</span></span>|
|<xref:System.Array?displayProperty=nameWithType>|<span data-ttu-id="2fbb0-170">**VT_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-170">**VT_ARRAY**</span></span>|

<span data-ttu-id="2fbb0-171">Önceki örnekte `MarshalObject` tanımlanan arabirimi kullanarak, aşağıdaki kod ÖRNEĞI bir com sunucusuna çeşitli çeşit çeşitlemelerini nasıl geçirebileceğinizi göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-171">Using the `MarshalObject` interface defined in the previous example, the following code example demonstrates how to pass various types of variants to a COM server.</span></span>

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

<span data-ttu-id="2fbb0-172">Karşılık gelen yönetilen türleri olmayan com <xref:System.Runtime.InteropServices.ErrorWrapper>türleri, <xref:System.Runtime.InteropServices.DispatchWrapper> <xref:System.Runtime.InteropServices.UnknownWrapper>,, ve <xref:System.Runtime.InteropServices.CurrencyWrapper>gibi sarmalayıcı sınıflar kullanılarak sıralanabilir.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-172">COM types that do not have corresponding managed types can be marshaled using wrapper classes such as <xref:System.Runtime.InteropServices.ErrorWrapper>, <xref:System.Runtime.InteropServices.DispatchWrapper>, <xref:System.Runtime.InteropServices.UnknownWrapper>, and <xref:System.Runtime.InteropServices.CurrencyWrapper>.</span></span> <span data-ttu-id="2fbb0-173">Aşağıdaki kod örneği, bir COM sunucusuna çeşitli çeşit çeşitlemelerini geçirmek için bu sarmalayıcılarını nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-173">The following code example demonstrates how to use these wrappers to pass various types of variants to a COM server.</span></span>

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

<span data-ttu-id="2fbb0-174">Sarmalayıcı sınıflar <xref:System.Runtime.InteropServices> ad alanında tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-174">The wrapper classes are defined in the <xref:System.Runtime.InteropServices> namespace.</span></span>

### <a name="marshaling-the-iconvertible-interface-to-variant"></a><span data-ttu-id="2fbb0-175">Iverli arabirimini VARIANT 'a hazırlama</span><span class="sxs-lookup"><span data-stu-id="2fbb0-175">Marshaling the IConvertible Interface to Variant</span></span>

<span data-ttu-id="2fbb0-176">Önceki bölümde listelenenler dışındaki türler, <xref:System.IConvertible> arabirimini uygulayarak nasıl sıralandıklarından kontrol edebilir.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-176">Types other than those listed in the previous section can control how they are marshaled by implementing the <xref:System.IConvertible> interface.</span></span> <span data-ttu-id="2fbb0-177">Nesne **Iconverli** arabirimini UYGULARSA, com Variant türü, <xref:System.TypeCode> <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> yönteminden döndürülen numaralandırmanın değeri ile çalışma zamanında belirlenir.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-177">If the object implements the **IConvertible** interface, the COM variant type is determined at run time by the value of the <xref:System.TypeCode> enumeration returned from the <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="2fbb0-178">Aşağıdaki tabloda, her bir değer için **TypeCode** numaralandırması ve KARŞıLıK gelen com Variant türü için olası değerler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-178">The following table shows the possible values for the **TypeCode** enumeration and the corresponding COM variant type for each value.</span></span>

|<span data-ttu-id="2fbb0-179">Kodunu</span><span class="sxs-lookup"><span data-stu-id="2fbb0-179">TypeCode</span></span>|<span data-ttu-id="2fbb0-180">COM varyant türü</span><span class="sxs-lookup"><span data-stu-id="2fbb0-180">COM variant type</span></span>|
|--------------|----------------------|
|<span data-ttu-id="2fbb0-181">**TypeCode. Empty**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-181">**TypeCode.Empty**</span></span>|<span data-ttu-id="2fbb0-182">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-182">**VT_EMPTY**</span></span>|
|<span data-ttu-id="2fbb0-183">**TypeCode. Object**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-183">**TypeCode.Object**</span></span>|<span data-ttu-id="2fbb0-184">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-184">**VT_UNKNOWN**</span></span>|
|<span data-ttu-id="2fbb0-185">**TypeCode. DBNull**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-185">**TypeCode.DBNull**</span></span>|<span data-ttu-id="2fbb0-186">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-186">**VT_NULL**</span></span>|
|<span data-ttu-id="2fbb0-187">**TypeCode. Boolean**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-187">**TypeCode.Boolean**</span></span>|<span data-ttu-id="2fbb0-188">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-188">**VT_BOOL**</span></span>|
|<span data-ttu-id="2fbb0-189">**TypeCode. Char**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-189">**TypeCode.Char**</span></span>|<span data-ttu-id="2fbb0-190">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-190">**VT_UI2**</span></span>|
|<span data-ttu-id="2fbb0-191">**TypeCode. SByte**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-191">**TypeCode.Sbyte**</span></span>|<span data-ttu-id="2fbb0-192">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-192">**VT_I1**</span></span>|
|<span data-ttu-id="2fbb0-193">**TypeCode. Byte**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-193">**TypeCode.Byte**</span></span>|<span data-ttu-id="2fbb0-194">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-194">**VT_UI1**</span></span>|
|<span data-ttu-id="2fbb0-195">**TypeCode. Int16**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-195">**TypeCode.Int16**</span></span>|<span data-ttu-id="2fbb0-196">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-196">**VT_I2**</span></span>|
|<span data-ttu-id="2fbb0-197">**TypeCode. UInt16**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-197">**TypeCode.UInt16**</span></span>|<span data-ttu-id="2fbb0-198">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-198">**VT_UI2**</span></span>|
|<span data-ttu-id="2fbb0-199">**TypeCode. Int32**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-199">**TypeCode.Int32**</span></span>|<span data-ttu-id="2fbb0-200">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-200">**VT_I4**</span></span>|
|<span data-ttu-id="2fbb0-201">**TypeCode. UInt32**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-201">**TypeCode.UInt32**</span></span>|<span data-ttu-id="2fbb0-202">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-202">**VT_UI4**</span></span>|
|<span data-ttu-id="2fbb0-203">**TypeCode. Int64**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-203">**TypeCode.Int64**</span></span>|<span data-ttu-id="2fbb0-204">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-204">**VT_I8**</span></span>|
|<span data-ttu-id="2fbb0-205">**TypeCode. UInt64**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-205">**TypeCode.UInt64**</span></span>|<span data-ttu-id="2fbb0-206">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-206">**VT_UI8**</span></span>|
|<span data-ttu-id="2fbb0-207">**TypeCode. Single**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-207">**TypeCode.Single**</span></span>|<span data-ttu-id="2fbb0-208">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-208">**VT_R4**</span></span>|
|<span data-ttu-id="2fbb0-209">**TypeCode. Double**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-209">**TypeCode.Double**</span></span>|<span data-ttu-id="2fbb0-210">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-210">**VT_R8**</span></span>|
|<span data-ttu-id="2fbb0-211">**TypeCode. Decimal**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-211">**TypeCode.Decimal**</span></span>|<span data-ttu-id="2fbb0-212">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-212">**VT_DECIMAL**</span></span>|
|<span data-ttu-id="2fbb0-213">**TypeCode. DateTime**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-213">**TypeCode.DateTime**</span></span>|<span data-ttu-id="2fbb0-214">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-214">**VT_DATE**</span></span>|
|<span data-ttu-id="2fbb0-215">**TypeCode. String**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-215">**TypeCode.String**</span></span>|<span data-ttu-id="2fbb0-216">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-216">**VT_BSTR**</span></span>|
|<span data-ttu-id="2fbb0-217">Desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-217">Not supported.</span></span>|<span data-ttu-id="2fbb0-218">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-218">**VT_INT**</span></span>|
|<span data-ttu-id="2fbb0-219">Desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-219">Not supported.</span></span>|<span data-ttu-id="2fbb0-220">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-220">**VT_UINT**</span></span>|
|<span data-ttu-id="2fbb0-221">Desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-221">Not supported.</span></span>|<span data-ttu-id="2fbb0-222">**VT_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-222">**VT_ARRAY**</span></span>|
|<span data-ttu-id="2fbb0-223">Desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-223">Not supported.</span></span>|<span data-ttu-id="2fbb0-224">**VT_RECORD**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-224">**VT_RECORD**</span></span>|
|<span data-ttu-id="2fbb0-225">Desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-225">Not supported.</span></span>|<span data-ttu-id="2fbb0-226">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-226">**VT_CY**</span></span>|
|<span data-ttu-id="2fbb0-227">Desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-227">Not supported.</span></span>|<span data-ttu-id="2fbb0-228">**VT_VARIANT**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-228">**VT_VARIANT**</span></span>|

<span data-ttu-id="2fbb0-229">COM çeşidinin değeri, **IConvertible.to** *tür* arabirimi çağırarak belirlenir **; burada** *tür* , **ıtypbleble. GetTypeCode**'dan döndürülen türe karşılık gelen dönüştürme yordamdır.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-229">The value of the COM variant is determined by calling the **IConvertible.To** *Type* interface, where **To** *Type* is the conversion routine that corresponds to the type that was returned from **IConvertible.GetTypeCode**.</span></span> <span data-ttu-id="2fbb0-230">Örneğin, **ıtypbleble. GetTypeCode** 'dan **TypeCode. Double** döndüren bir nesne **VT_R8**türünde bir com değişkeni olarak sıralanır.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-230">For example, an object that returns **TypeCode.Double** from **IConvertible.GetTypeCode** is marshaled as a COM variant of type **VT_R8**.</span></span> <span data-ttu-id="2fbb0-231">**Iverbleface** arabirimine atama yaparak ve <xref:System.IConvertible.ToDouble%2A> metodunu çağırarak, değişkenin değerini (com çeşidinin **dblVal** alanında depolanır) elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-231">You can obtain the value of the variant (stored in the **dblVal** field of the COM variant) by casting to the **IConvertible** interface and calling the <xref:System.IConvertible.ToDouble%2A> method.</span></span>

## <a name="marshaling-variant-to-object"></a><span data-ttu-id="2fbb0-232">Değişkeni nesneye sıralama</span><span class="sxs-lookup"><span data-stu-id="2fbb0-232">Marshaling Variant to Object</span></span>

<span data-ttu-id="2fbb0-233">Bir değişkeni bir nesneye, türü ve bazen değeri, oluşturulan değişkenin değerini, üretilen nesnenin türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-233">When marshaling a variant to an object, the type, and sometimes the value, of the marshaled variant determines the type of object produced.</span></span> <span data-ttu-id="2fbb0-234">Aşağıdaki tabloda her bir varyant türü ve COM 'dan .NET Framework bir varyant geçirildiğinde sıralayıcı tarafından oluşturulan ilgili nesne türü tanımlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-234">The following table identifies each variant type and the corresponding object type that the marshaler creates when a variant is passed from COM to the .NET Framework.</span></span>

|<span data-ttu-id="2fbb0-235">COM varyant türü</span><span class="sxs-lookup"><span data-stu-id="2fbb0-235">COM variant type</span></span>|<span data-ttu-id="2fbb0-236">Nesne türü</span><span class="sxs-lookup"><span data-stu-id="2fbb0-236">Object type</span></span>|
|----------------------|-----------------|
|<span data-ttu-id="2fbb0-237">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-237">**VT_EMPTY**</span></span>|<span data-ttu-id="2fbb0-238">Null nesne başvurusu (Visual Basic**hiçbir şey** ).</span><span class="sxs-lookup"><span data-stu-id="2fbb0-238">Null object reference (**Nothing** in Visual Basic).</span></span>|
|<span data-ttu-id="2fbb0-239">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-239">**VT_NULL**</span></span>|<xref:System.DBNull?displayProperty=nameWithType>|
|<span data-ttu-id="2fbb0-240">**VT_DISPATCH**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-240">**VT_DISPATCH**</span></span>|<span data-ttu-id="2fbb0-241">**System. __ComObject** veya (pdispVal = = null) ise null</span><span class="sxs-lookup"><span data-stu-id="2fbb0-241">**System.__ComObject** or null if (pdispVal == null)</span></span>|
|<span data-ttu-id="2fbb0-242">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-242">**VT_UNKNOWN**</span></span>|<span data-ttu-id="2fbb0-243">**System. __ComObject** veya (punkVal = = null) ise null</span><span class="sxs-lookup"><span data-stu-id="2fbb0-243">**System.__ComObject** or null if (punkVal == null)</span></span>|
|<span data-ttu-id="2fbb0-244">**VT_ERROR**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-244">**VT_ERROR**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|<span data-ttu-id="2fbb0-245">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-245">**VT_BOOL**</span></span>|<xref:System.Boolean?displayProperty=nameWithType>|
|<span data-ttu-id="2fbb0-246">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-246">**VT_I1**</span></span>|<xref:System.SByte?displayProperty=nameWithType>|
|<span data-ttu-id="2fbb0-247">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-247">**VT_UI1**</span></span>|<xref:System.Byte?displayProperty=nameWithType>|
|<span data-ttu-id="2fbb0-248">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-248">**VT_I2**</span></span>|<xref:System.Int16?displayProperty=nameWithType>|
|<span data-ttu-id="2fbb0-249">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-249">**VT_UI2**</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|
|<span data-ttu-id="2fbb0-250">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-250">**VT_I4**</span></span>|<xref:System.Int32?displayProperty=nameWithType>|
|<span data-ttu-id="2fbb0-251">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-251">**VT_UI4**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|<span data-ttu-id="2fbb0-252">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-252">**VT_I8**</span></span>|<xref:System.Int64?displayProperty=nameWithType>|
|<span data-ttu-id="2fbb0-253">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-253">**VT_UI8**</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|
|<span data-ttu-id="2fbb0-254">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-254">**VT_R4**</span></span>|<xref:System.Single?displayProperty=nameWithType>|
|<span data-ttu-id="2fbb0-255">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-255">**VT_R8**</span></span>|<xref:System.Double?displayProperty=nameWithType>|
|<span data-ttu-id="2fbb0-256">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-256">**VT_DECIMAL**</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|
|<span data-ttu-id="2fbb0-257">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-257">**VT_DATE**</span></span>|<xref:System.DateTime?displayProperty=nameWithType>|
|<span data-ttu-id="2fbb0-258">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-258">**VT_BSTR**</span></span>|<xref:System.String?displayProperty=nameWithType>|
|<span data-ttu-id="2fbb0-259">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-259">**VT_INT**</span></span>|<xref:System.Int32?displayProperty=nameWithType>|
|<span data-ttu-id="2fbb0-260">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-260">**VT_UINT**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|<span data-ttu-id="2fbb0-261">**VT_ARRAY** &#124; **VT_**\*</span><span class="sxs-lookup"><span data-stu-id="2fbb0-261">**VT_ARRAY** &#124; **VT_**\*</span></span>|<xref:System.Array?displayProperty=nameWithType>|
|<span data-ttu-id="2fbb0-262">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-262">**VT_CY**</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|
|<span data-ttu-id="2fbb0-263">**VT_RECORD**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-263">**VT_RECORD**</span></span>|<span data-ttu-id="2fbb0-264">Karşılık gelen paketlenmiş değer türü.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-264">Corresponding boxed value type.</span></span>|
|<span data-ttu-id="2fbb0-265">**VT_VARIANT**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-265">**VT_VARIANT**</span></span>|<span data-ttu-id="2fbb0-266">Desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-266">Not supported.</span></span>|

<span data-ttu-id="2fbb0-267">COM 'dan yönetilen koda geçirilen ve sonra COM 'a geri dönüş değişken türleri, çağrının süresi boyunca aynı varyant türünü korumayabilir.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-267">Variant types passed from COM to managed code and then back to COM might not retain the same variant type for the duration of the call.</span></span> <span data-ttu-id="2fbb0-268">**VT_DISPATCH** türünde BIR değişken COM 'tan .NET Framework geçirildiğinde ne olacağını düşünün.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-268">Consider what happens when a variant of type **VT_DISPATCH** is passed from COM to the .NET Framework.</span></span> <span data-ttu-id="2fbb0-269">Sıralama sırasında, değişken öğesine dönüştürülür <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-269">During marshaling, the variant is converted to a <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2fbb0-270">**Nesne** daha sonra com 'a geri geçirilirse, **VT_UNKNOWN**türünde bir varyanta geri getirilir.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-270">If the **Object** is then passed back to COM, it is marshaled back to a variant of type **VT_UNKNOWN**.</span></span> <span data-ttu-id="2fbb0-271">Bir nesne yönetilen koddan COM 'a sıralandığınızda üretilen varyantın, başlangıçta nesneyi oluşturmak için kullanılan değişkenle aynı türde olacağını garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-271">There is no guarantee that the variant produced when an object is marshaled from managed code to COM will be the same type as the variant initially used to produce the object.</span></span>

## <a name="marshaling-byref-variants"></a><span data-ttu-id="2fbb0-272">ByRef türevlerini sıralama</span><span class="sxs-lookup"><span data-stu-id="2fbb0-272">Marshaling ByRef Variants</span></span>

<span data-ttu-id="2fbb0-273">Varyantlar değere veya başvuruya göre geçirilebilir olsa da, değişken içeriğinin değer yerine başvuruya göre geçtiğini göstermek için **VT_BYREF** bayrağı herhangi bir varyant türüyle birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-273">Although variants themselves can be passed by value or by reference, the **VT_BYREF** flag can also be used with any variant type to indicate that the contents of the variant are being passed by reference instead of by value.</span></span> <span data-ttu-id="2fbb0-274">Başvuruya göre sıralama ve bir değişkeni **VT_BYREF** bayrak kümesiyle sıralama arasındaki fark kafa karıştırıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-274">The difference between marshaling variants by reference and marshaling a variant with the **VT_BYREF** flag set can be confusing.</span></span> <span data-ttu-id="2fbb0-275">Aşağıdaki çizim farklılıkları açıklığa kavuşturulur:</span><span class="sxs-lookup"><span data-stu-id="2fbb0-275">The following illustration clarifies the differences:</span></span>

<span data-ttu-id="2fbb0-276">![Yığına geçilen varyansı gösteren diyagram.](./media/default-marshaling-for-objects/interop-variant-passed-value-reference.gif)</span><span class="sxs-lookup"><span data-stu-id="2fbb0-276">![Diagram that shows variant passed on the stack.](./media/default-marshaling-for-objects/interop-variant-passed-value-reference.gif)</span></span>
<span data-ttu-id="2fbb0-277">Değer ve başvuruya göre geçirilen çeşitler</span><span class="sxs-lookup"><span data-stu-id="2fbb0-277">Variants passed by value and by reference</span></span>

<span data-ttu-id="2fbb0-278">**Nesneleri ve çeşitlemeleri değere göre hazırlama için varsayılan davranış**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-278">**Default behavior for marshaling objects and variants by value**</span></span>

- <span data-ttu-id="2fbb0-279">Nesneleri yönetilen koddan COM 'a geçirirken nesnenin içeriği sıralayıcı tarafından oluşturulan yeni bir varyanta kopyalanır ve bu, [nesneyi değişken olarak hazırlama](#marshaling-object-to-variant)bölümünde tanımlanan kurallar kullanılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-279">When passing objects from managed code to COM, the contents of the object are copied into a new variant created by the marshaler, using the rules defined in [Marshaling Object to Variant](#marshaling-object-to-variant).</span></span> <span data-ttu-id="2fbb0-280">Yönetilmeyen taraftaki VARIANT üzerinde yapılan değişiklikler, çağrıdan döndürülen özgün nesneye geri yayılmaz.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-280">Changes made to the variant on the unmanaged side are not propagated back to the original object on return from the call.</span></span>

- <span data-ttu-id="2fbb0-281">Değişkenleri COM 'dan yönetilen koda geçirirken, varyantın içeriği, [değişken sıralama](#marshaling-variant-to-object)içinde tanımlanan kuralları kullanarak yeni oluşturulan bir nesneye kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-281">When passing variants from COM to managed code, the contents of the variant are copied to a newly created object, using the rules defined in [Marshaling Variant to Object](#marshaling-variant-to-object).</span></span> <span data-ttu-id="2fbb0-282">Yönetilen taraftaki nesnede yapılan değişiklikler, çağrıdan döndürülen özgün varyanta geri yayılmaz.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-282">Changes made to the object on the managed side are not propagated back to the original variant on return from the call.</span></span>

<span data-ttu-id="2fbb0-283">**Başvuruya göre nesneleri ve türevleri hazırlama için varsayılan davranış**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-283">**Default behavior for marshaling objects and variants by reference**</span></span>

<span data-ttu-id="2fbb0-284">Değişiklikleri çağırana geri yaymak için, parametrelerin başvuruya göre geçirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-284">To propagate changes back to the caller, the parameters must be passed by reference.</span></span> <span data-ttu-id="2fbb0-285">Örneğin, parametreleri başvuruya göre geçirmek için C# ' deki **ref** anahtar sözcüğünü (veya Visual Basic yönetilen kodda **ByRef** ) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-285">For example, you can use the **ref** keyword in C# (or **ByRef** in Visual Basic managed code) to pass parameters by reference.</span></span> <span data-ttu-id="2fbb0-286">COM 'da, başvuru parametreleri \*\*değişken \* \*\*gibi bir işaretçi kullanılarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-286">In COM, reference parameters are passed using a pointer such as a **variant \***.</span></span>

- <span data-ttu-id="2fbb0-287">Bir nesneyi bir COM 'a başvuruya göre geçirirken Sıralayıcı yeni bir değişken oluşturur ve Nesne başvurusunun içeriğini çağrı yapılmadan önce varyanta kopyalar.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-287">When passing an object to COM by reference, the marshaler creates a new variant and copies the contents of the object reference into the variant before the call is made.</span></span> <span data-ttu-id="2fbb0-288">Değişken, kullanıcının varyantın içeriğini değiştirmek için boş olduğu yönetilmeyen işleve geçirilir.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-288">The variant is passed to the unmanaged function where the user is free to change the contents of the variant.</span></span> <span data-ttu-id="2fbb0-289">Çağrıdan geri döndüğünüzde, yönetilmeyen taraftaki VARIANT üzerinde yapılan tüm değişiklikler özgün nesneye geri yayılır.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-289">On return from the call, any changes made to the variant on the unmanaged side are propagated back to the original object.</span></span> <span data-ttu-id="2fbb0-290">Değişken türü, çağrıya geçirilen varyantın türünden farklıysa, değişiklikler farklı türdeki bir nesneye geri yayılır.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-290">If the type of the variant differs from the type of the variant passed to the call, then the changes are propagated back to an object of a different type.</span></span> <span data-ttu-id="2fbb0-291">Diğer bir deyişle, çağrıya geçirilen nesnenin türü, çağrıdan döndürülen nesne türünden farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-291">That is, the type of the object passed into the call can differ from the type of the object returned from the call.</span></span>

- <span data-ttu-id="2fbb0-292">Başvuruya göre yönetilen koda bir varyant geçirirken, Sıralayıcı yeni bir nesne oluşturur ve çağrıyı yapmadan önce değişkenin içeriğini nesnesine kopyalar.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-292">When passing a variant to managed code by reference, the marshaler creates a new object and copies the contents of the variant into the object before making the call.</span></span> <span data-ttu-id="2fbb0-293">Nesnesine bir başvuru, kullanıcının nesneyi değiştirmek için ücretsiz olarak yönetilen işleve geçirilir.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-293">A reference to the object is passed to the managed function, where the user is free to change the object.</span></span> <span data-ttu-id="2fbb0-294">Çağrıdan geri döndüğünüzde, başvurulan nesnede yapılan tüm değişiklikler özgün varyanta geri yayılır.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-294">On return from the call, any changes made to the referenced object are propagated back to the original variant.</span></span> <span data-ttu-id="2fbb0-295">Nesnenin türü, çağrıya geçirilen nesne türünden farklıysa, özgün varyantın türü değiştirilir ve değer varyanta geri yayılır...</span><span class="sxs-lookup"><span data-stu-id="2fbb0-295">If the type of the object differs from the type of the object passed in to the call, the type of the original variant is changed and the value is propagated back into the variant.</span></span> <span data-ttu-id="2fbb0-296">Yine, çağrıya geçirilen varyantın türü, çağrıdan döndürülen VARIANT türünden farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-296">Again, the type of the variant passed into the call can differ from the type of the variant returned from the call.</span></span>

 <span data-ttu-id="2fbb0-297">**VT_BYREF bayrak kümesiyle bir değişkeni hazırlama için varsayılan davranış**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-297">**Default behavior for marshaling a variant with the VT_BYREF flag set**</span></span>

- <span data-ttu-id="2fbb0-298">Değere göre yönetilen koda geçirilen bir değişken, değişkenin bir değer yerine bir başvuru içerdiğini göstermek için **VT_BYREF** bayrak kümesine sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-298">A variant being passed to managed code by value can have the **VT_BYREF** flag set to indicate that the variant contains a reference instead of a value.</span></span> <span data-ttu-id="2fbb0-299">Bu durumda, değişken değer ile geçirildiğinden değişken hala bir nesne olarak sıralanır.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-299">In this case, the variant is still marshaled to an object because the variant is being passed by value.</span></span> <span data-ttu-id="2fbb0-300">Sıralayıcı, varyantın içeriğini otomatik olarak referans yapar ve çağrıyı yapmadan önce yeni oluşturulan bir nesneye kopyalar.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-300">The marshaler automatically dereferences the contents of the variant and copies it into a newly created object before making the call.</span></span> <span data-ttu-id="2fbb0-301">Nesne daha sonra yönetilen işleve geçirilir; Ancak, çağrıdan dönüşte, nesne özgün varyanta geri yayılmaz.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-301">The object is then passed into the managed function; however, on return from the call, the object is not propagated back into the original variant.</span></span> <span data-ttu-id="2fbb0-302">Yönetilen nesnede yapılan değişiklikler kaybedilir.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-302">Changes made to the managed object are lost.</span></span>

  > [!CAUTION]
  > <span data-ttu-id="2fbb0-303">Değişken **VT_BYREF** bayrak kümesine sahip olsa bile, değer tarafından geçirilen bir değişkenin değerini değiştirme yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-303">There is no way to change the value of a variant passed by value, even if the variant has the **VT_BYREF** flag set.</span></span>

- <span data-ttu-id="2fbb0-304">Başvuruya göre yönetilen koda geçirilen bir değişken, değişkenin başka bir başvuru içerdiğini belirtmek için de **VT_BYREF** bayrak verebilir.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-304">A variant being passed to managed code by reference can also have the **VT_BYREF** flag set to indicate that the variant contains another reference.</span></span> <span data-ttu-id="2fbb0-305">Varsa, değişken başvuruya göre geçirildiğinden bir **başvuru** nesnesine göre sıralanır.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-305">If it does, the variant is marshaled to a **ref** object because the variant is being passed by reference.</span></span> <span data-ttu-id="2fbb0-306">Sıralayıcı, varyantın içeriğini otomatik olarak referans yapar ve çağrıyı yapmadan önce yeni oluşturulan bir nesneye kopyalar.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-306">The marshaler automatically dereferences the contents of the variant and copies it into a newly created object before making the call.</span></span> <span data-ttu-id="2fbb0-307">Çağrıdan dönüşte, nesnenin değeri yalnızca nesnenin geçirildiği nesneyle aynı türde olması durumunda, özgün varyant içindeki başvuruya geri yayılır.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-307">On return from the call, the value of the object is propagated back to the reference within the original variant only if the object is the same type as the object passed in.</span></span> <span data-ttu-id="2fbb0-308">Diğer bir deyişle, yayma **VT_BYREF** bayrak kümesiyle bir varyant türünü değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-308">That is, propagation does not change the type of a variant with the **VT_BYREF** flag set.</span></span> <span data-ttu-id="2fbb0-309">Çağrı sırasında nesnenin türü değiştirilirse, çağrıdan döndürülen bir <xref:System.InvalidCastException> meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-309">If the type of the object is changed during the call, an <xref:System.InvalidCastException> occurs on return from the call.</span></span>

<span data-ttu-id="2fbb0-310">Aşağıdaki tabloda, çeşitler ve nesneler için yayma kuralları özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-310">The following table summarizes the propagation rules for variants and objects.</span></span>

|<span data-ttu-id="2fbb0-311">Başlangıç</span><span class="sxs-lookup"><span data-stu-id="2fbb0-311">From</span></span>|<span data-ttu-id="2fbb0-312">Alıcı</span><span class="sxs-lookup"><span data-stu-id="2fbb0-312">To</span></span>|<span data-ttu-id="2fbb0-313">Geri yayılan değişiklikler</span><span class="sxs-lookup"><span data-stu-id="2fbb0-313">Changes propagated back</span></span>|
|----------|--------|-----------------------------|
|<span data-ttu-id="2fbb0-314">**Değişken**  *v*</span><span class="sxs-lookup"><span data-stu-id="2fbb0-314">**Variant**  *v*</span></span>|<span data-ttu-id="2fbb0-315">**Nesne**  *o*</span><span class="sxs-lookup"><span data-stu-id="2fbb0-315">**Object**  *o*</span></span>|<span data-ttu-id="2fbb0-316">Hiçbir zaman</span><span class="sxs-lookup"><span data-stu-id="2fbb0-316">Never</span></span>|
|<span data-ttu-id="2fbb0-317">**Nesne**  *o*</span><span class="sxs-lookup"><span data-stu-id="2fbb0-317">**Object**  *o*</span></span>|<span data-ttu-id="2fbb0-318">**Değişken**  *v*</span><span class="sxs-lookup"><span data-stu-id="2fbb0-318">**Variant**  *v*</span></span>|<span data-ttu-id="2fbb0-319">Hiçbir zaman</span><span class="sxs-lookup"><span data-stu-id="2fbb0-319">Never</span></span>|
|<span data-ttu-id="2fbb0-320">**Değişken**   ***\****  *BD*</span><span class="sxs-lookup"><span data-stu-id="2fbb0-320">**Variant**   ***\****  *pv*</span></span>|<span data-ttu-id="2fbb0-321">**Başvuru nesnesi**  *o*</span><span class="sxs-lookup"><span data-stu-id="2fbb0-321">**Ref Object**  *o*</span></span>|<span data-ttu-id="2fbb0-322">Her zaman</span><span class="sxs-lookup"><span data-stu-id="2fbb0-322">Always</span></span>|
|<span data-ttu-id="2fbb0-323">**Başvuru nesnesi**  *o*</span><span class="sxs-lookup"><span data-stu-id="2fbb0-323">**Ref object**  *o*</span></span>|<span data-ttu-id="2fbb0-324">**Değişken**   ***\****  *BD*</span><span class="sxs-lookup"><span data-stu-id="2fbb0-324">**Variant**   ***\****  *pv*</span></span>|<span data-ttu-id="2fbb0-325">Her zaman</span><span class="sxs-lookup"><span data-stu-id="2fbb0-325">Always</span></span>|
|<span data-ttu-id="2fbb0-326">**Değişken**  *v* **(VT_BYREF** *&#124;* **VT_\*)**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-326">**Variant**  *v* **(VT_BYREF** *&#124;* **VT_\*)**</span></span>|<span data-ttu-id="2fbb0-327">**Nesne**  *o*</span><span class="sxs-lookup"><span data-stu-id="2fbb0-327">**Object**  *o*</span></span>|<span data-ttu-id="2fbb0-328">Hiçbir zaman</span><span class="sxs-lookup"><span data-stu-id="2fbb0-328">Never</span></span>|
|<span data-ttu-id="2fbb0-329">**Değişken**  *v* **(VT_BYREF** *&#124;* **VT_)**</span><span class="sxs-lookup"><span data-stu-id="2fbb0-329">**Variant**  *v* **(VT_BYREF** *&#124;* **VT_)**</span></span>|<span data-ttu-id="2fbb0-330">**Başvuru nesnesi**  *o*</span><span class="sxs-lookup"><span data-stu-id="2fbb0-330">**Ref Object**  *o*</span></span>|<span data-ttu-id="2fbb0-331">Yalnızca tür değişmemiştir.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-331">Only if the type has not changed.</span></span>|

## <a name="see-also"></a><span data-ttu-id="2fbb0-332">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2fbb0-332">See also</span></span>

- [<span data-ttu-id="2fbb0-333">Varsayılan Sıralama Davranışı</span><span class="sxs-lookup"><span data-stu-id="2fbb0-333">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
- [<span data-ttu-id="2fbb0-334">Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler</span><span class="sxs-lookup"><span data-stu-id="2fbb0-334">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- <span data-ttu-id="2fbb0-335">[Yönlü öznitelikler](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2fbb0-335">[Directional Attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span></span>
- [<span data-ttu-id="2fbb0-336">Kopyalama ve Sabitleme</span><span class="sxs-lookup"><span data-stu-id="2fbb0-336">Copying and Pinning</span></span>](copying-and-pinning.md)
