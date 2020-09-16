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
# <a name="default-marshaling-for-objects"></a>Nesneler için Varsayılan Hazırlama

Olarak yazılan parametreler ve alanlar <xref:System.Object?displayProperty=nameWithType> , aşağıdaki türlerden biri olarak yönetilmeyen koda gösterilebilir:

- Nesne bir parametre olduğunda bir değişken.

- Nesne bir yapı alanı olduğunda arabirim.

Yalnızca COM birlikte çalışması nesne türleri için sıralama destekler. Varsayılan davranış, nesneleri COM türevlerine sıralamakta kullanılır. Bu kurallar yalnızca tür **nesnesi** için geçerlidir ve **Object** sınıfından türetilmiş türü kesin belirlenmiş nesneler için uygulanmaz.

## <a name="marshaling-options"></a>Sıralama seçenekleri

Aşağıdaki tabloda, **nesne** veri türü için sıralama seçenekleri gösterilmektedir. <xref:System.Runtime.InteropServices.MarshalAsAttribute>Özniteliği <xref:System.Runtime.InteropServices.UnmanagedType> nesneleri sıralamak için birkaç numaralandırma değeri sağlar.

|Sabit listesi türü|Yönetilmeyen biçimin açıklaması|
|----------------------|-------------------------------------|
|**UnmanagedType. struct**<br /><br /> (parametreler için varsayılan)|COM stili bir varyant.|
|**UnmanagedType. Interface**|Mümkünse **IDispatch** arabirimi; Aksi takdirde, bir **IUnknown** arabirimi.|
|**UnmanagedType. IUnknown**<br /><br /> (alanlar için varsayılan)|Bir **IUnknown** arabirimi.|
|**UnmanagedType. IDispatch**|Bir **IDispatch** arabirimi.|

Aşağıdaki örnek için yönetilen arabirim tanımını gösterir `MarshalObject` .

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

Aşağıdaki kod, `MarshalObject` arabirimi bir tür kitaplığına dışarı aktarır.

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
> Birlikte çalışma sıralayıcısı, çağrıdan sonra değişken içinde tüm ayrılmış nesneleri otomatik olarak boşaltır.

Aşağıdaki örnek, biçimli bir değer türünü gösterir.

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

Aşağıdaki kod, biçimli türü bir tür kitaplığına dışarı aktarır.

```cpp
struct ObjectHolder {
   VARIANT o1;
   IDispatch *o2;
}
```

## <a name="marshaling-object-to-interface"></a>Nesne arabirime sıralanıyor

Bir nesne bir arabirim olarak COM 'a sunulduğunda, bu arabirim yönetilen tür için sınıf arabirimidir <xref:System.Object> ( **_object** arabirimi). Bu arabirim **IDispatch** <xref:System.Runtime.InteropServices.UnmanagedType> , sonuç türü kitaplığında bir IDispatch () veya **IUnknown** (**UnmanagedType. IUnknown**) olarak yazılır. COM istemcileri yönetilen sınıfın veya **_object** arabirimi aracılığıyla türetilmiş sınıfları tarafından uygulanan herhangi bir üyenin üyelerini dinamik olarak çağırabilir. İstemci Ayrıca, yönetilen tür tarafından açıkça uygulanan başka bir arabirim elde etmek için **QueryInterface** 'i çağırabilir.

## <a name="marshaling-object-to-variant"></a>Nesne varyanta sıralanıyor

Bir nesne bir varyanta sıralanışında, iç varyant türü çalışma zamanında aşağıdaki kurallara göre belirlenir:

- Nesne başvurusu null ise (Visual Basic**hiçbir şey** ), nesne **VT_EMPTY**türünde bir değişkenle sıralanır.

- Nesne, aşağıdaki tabloda listelenen herhangi bir türde bir örnek ise, sonuçta elde edilen varyant türü Sıralayıcı içinde yerleşik olan ve tabloda gösterilen kurallara göre belirlenir.

- Sıralama davranışını açıkça kontrol etmeniz gereken diğer nesneler <xref:System.IConvertible> arabirimi uygulayabilir. Bu durumda, değişken türü yönteminden döndürülen tür koduna göre belirlenir <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> . Aksi takdirde, nesne **VT_UNKNOWN**türünde bir değişken olarak sıralanır.

### <a name="marshaling-system-types-to-variant"></a>Sistem türlerini varyanta sıralama

Aşağıdaki tabloda, yönetilen nesne türleri ve bunlara karşılık gelen COM Variant türleri gösterilmektedir. Bu türler yalnızca çağrılan metodun imzası tür olduğunda dönüştürülür <xref:System.Object?displayProperty=nameWithType> .

|Nesne türü|COM varyant türü|
|-----------------|----------------------|
|Null nesne başvurusu (Visual Basic**hiçbir şey** ).|**VT_EMPTY**|
|<xref:System.DBNull?displayProperty=nameWithType>|**VT_NULL**|
|<xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>|**VT_ERROR**|
|<xref:System.Reflection.Missing?displayProperty=nameWithType>|**E_PARAMNOTFOUND** **VT_ERROR**|
|<xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>|**VT_DISPATCH**|
|<xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>|**VT_UNKNOWN**|
|<xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>|**VT_CY**|
|<xref:System.Boolean?displayProperty=nameWithType>|**VT_BOOL**|
|<xref:System.SByte?displayProperty=nameWithType>|**VT_I1**|
|<xref:System.Byte?displayProperty=nameWithType>|**VT_UI1**|
|<xref:System.Int16?displayProperty=nameWithType>|**VT_I2**|
|<xref:System.UInt16?displayProperty=nameWithType>|**VT_UI2**|
|<xref:System.Int32?displayProperty=nameWithType>|**VT_I4**|
|<xref:System.UInt32?displayProperty=nameWithType>|**VT_UI4**|
|<xref:System.Int64?displayProperty=nameWithType>|**VT_I8**|
|<xref:System.UInt64?displayProperty=nameWithType>|**VT_UI8**|
|<xref:System.Single?displayProperty=nameWithType>|**VT_R4**|
|<xref:System.Double?displayProperty=nameWithType>|**VT_R8**|
|<xref:System.Decimal?displayProperty=nameWithType>|**VT_DECIMAL**|
|<xref:System.DateTime?displayProperty=nameWithType>|**VT_DATE**|
|<xref:System.String?displayProperty=nameWithType>|**VT_BSTR**|
|<xref:System.IntPtr?displayProperty=nameWithType>|**VT_INT**|
|<xref:System.UIntPtr?displayProperty=nameWithType>|**VT_UINT**|
|<xref:System.Array?displayProperty=nameWithType>|**VT_ARRAY**|

`MarshalObject`Önceki örnekte tanımlanan arabirimi kullanarak, aşağıdaki kod örneği BIR com sunucusuna çeşitli çeşit çeşitlemelerini nasıl geçirebileceğinizi göstermektedir.

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

Karşılık gelen yönetilen türleri olmayan com türleri,,, ve gibi sarmalayıcı sınıflar kullanılarak sıralanabilir <xref:System.Runtime.InteropServices.ErrorWrapper> <xref:System.Runtime.InteropServices.DispatchWrapper> <xref:System.Runtime.InteropServices.UnknownWrapper> <xref:System.Runtime.InteropServices.CurrencyWrapper> . Aşağıdaki kod örneği, bir COM sunucusuna çeşitli çeşit çeşitlemelerini geçirmek için bu sarmalayıcılarını nasıl kullanacağınızı gösterir.

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

Sarmalayıcı sınıflar <xref:System.Runtime.InteropServices> ad alanında tanımlanır.

### <a name="marshaling-the-iconvertible-interface-to-variant"></a>Iverli arabirimini VARIANT 'a hazırlama

Önceki bölümde listelenenler dışındaki türler, arabirimini uygulayarak nasıl sıralandıklarından kontrol edebilir <xref:System.IConvertible> . Nesne **Iconverli** arabirimini UYGULARSA, com Variant türü, <xref:System.TypeCode> yönteminden döndürülen numaralandırmanın değeri ile çalışma zamanında belirlenir <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> .

Aşağıdaki tabloda, her bir değer için **TypeCode** numaralandırması ve KARŞıLıK gelen com Variant türü için olası değerler gösterilmektedir.

|Kodunu|COM varyant türü|
|--------------|----------------------|
|**TypeCode. Empty**|**VT_EMPTY**|
|**TypeCode. Object**|**VT_UNKNOWN**|
|**TypeCode. DBNull**|**VT_NULL**|
|**TypeCode. Boolean**|**VT_BOOL**|
|**TypeCode. Char**|**VT_UI2**|
|**TypeCode. SByte**|**VT_I1**|
|**TypeCode. Byte**|**VT_UI1**|
|**TypeCode. Int16**|**VT_I2**|
|**TypeCode. UInt16**|**VT_UI2**|
|**TypeCode. Int32**|**VT_I4**|
|**TypeCode. UInt32**|**VT_UI4**|
|**TypeCode. Int64**|**VT_I8**|
|**TypeCode. UInt64**|**VT_UI8**|
|**TypeCode. Single**|**VT_R4**|
|**TypeCode. Double**|**VT_R8**|
|**TypeCode. Decimal**|**VT_DECIMAL**|
|**TypeCode. DateTime**|**VT_DATE**|
|**TypeCode. String**|**VT_BSTR**|
|Desteklenmez.|**VT_INT**|
|Desteklenmez.|**VT_UINT**|
|Desteklenmez.|**VT_ARRAY**|
|Desteklenmez.|**VT_RECORD**|
|Desteklenmez.|**VT_CY**|
|Desteklenmez.|**VT_VARIANT**|

COM çeşidinin değeri, **IConvertible.to** *tür* arabirimi çağırarak belirlenir **; burada** *tür* , **ıtypbleble. GetTypeCode**'dan döndürülen türe karşılık gelen dönüştürme yordamdır. Örneğin, **ıtypbleble. GetTypeCode** 'dan **TypeCode. Double** döndüren bir nesne **VT_R8**türünde bir com değişkeni olarak sıralanır. **Iverbleface** arabirimine atama yaparak ve metodunu çağırarak, değişkenin DEĞERINI (com çeşidinin **dblVal** alanında depolanır) elde edebilirsiniz <xref:System.IConvertible.ToDouble%2A> .

## <a name="marshaling-variant-to-object"></a>Değişkeni nesneye sıralama

Bir değişkeni bir nesneye, türü ve bazen değeri, oluşturulan değişkenin değerini, üretilen nesnenin türünü belirler. Aşağıdaki tabloda her bir varyant türü ve COM 'dan .NET Framework bir varyant geçirildiğinde sıralayıcı tarafından oluşturulan ilgili nesne türü tanımlanmaktadır.

|COM varyant türü|Nesne türü|
|----------------------|-----------------|
|**VT_EMPTY**|Null nesne başvurusu (Visual Basic**hiçbir şey** ).|
|**VT_NULL**|<xref:System.DBNull?displayProperty=nameWithType>|
|**VT_DISPATCH**|**System. __ComObject** veya (pdispVal = = null) ise null|
|**VT_UNKNOWN**|**System. __ComObject** veya (punkVal = = null) ise null|
|**VT_ERROR**|<xref:System.UInt32?displayProperty=nameWithType>|
|**VT_BOOL**|<xref:System.Boolean?displayProperty=nameWithType>|
|**VT_I1**|<xref:System.SByte?displayProperty=nameWithType>|
|**VT_UI1**|<xref:System.Byte?displayProperty=nameWithType>|
|**VT_I2**|<xref:System.Int16?displayProperty=nameWithType>|
|**VT_UI2**|<xref:System.UInt16?displayProperty=nameWithType>|
|**VT_I4**|<xref:System.Int32?displayProperty=nameWithType>|
|**VT_UI4**|<xref:System.UInt32?displayProperty=nameWithType>|
|**VT_I8**|<xref:System.Int64?displayProperty=nameWithType>|
|**VT_UI8**|<xref:System.UInt64?displayProperty=nameWithType>|
|**VT_R4**|<xref:System.Single?displayProperty=nameWithType>|
|**VT_R8**|<xref:System.Double?displayProperty=nameWithType>|
|**VT_DECIMAL**|<xref:System.Decimal?displayProperty=nameWithType>|
|**VT_DATE**|<xref:System.DateTime?displayProperty=nameWithType>|
|**VT_BSTR**|<xref:System.String?displayProperty=nameWithType>|
|**VT_INT**|<xref:System.Int32?displayProperty=nameWithType>|
|**VT_UINT**|<xref:System.UInt32?displayProperty=nameWithType>|
|**VT_ARRAY** &#124; **VT_**\*|<xref:System.Array?displayProperty=nameWithType>|
|**VT_CY**|<xref:System.Decimal?displayProperty=nameWithType>|
|**VT_RECORD**|Karşılık gelen paketlenmiş değer türü.|
|**VT_VARIANT**|Desteklenmez.|

COM 'dan yönetilen koda geçirilen ve sonra COM 'a geri dönüş değişken türleri, çağrının süresi boyunca aynı varyant türünü korumayabilir. **VT_DISPATCH** türünde BIR değişken COM 'tan .NET Framework geçirildiğinde ne olacağını düşünün. Sıralama sırasında, değişken öğesine dönüştürülür <xref:System.Object?displayProperty=nameWithType> . **Nesne** daha sonra com 'a geri geçirilirse, **VT_UNKNOWN**türünde bir varyanta geri getirilir. Bir nesne yönetilen koddan COM 'a sıralandığınızda üretilen varyantın, başlangıçta nesneyi oluşturmak için kullanılan değişkenle aynı türde olacağını garanti etmez.

## <a name="marshaling-byref-variants"></a>ByRef türevlerini sıralama

Varyantlar değere veya başvuruya göre geçirilebilir olsa da, değişken içeriğinin değer yerine başvuruya göre geçtiğini göstermek için **VT_BYREF** bayrağı herhangi bir varyant türüyle birlikte kullanılabilir. Başvuruya göre sıralama ve bir değişkeni **VT_BYREF** bayrak kümesiyle sıralama arasındaki fark kafa karıştırıcı olabilir. Aşağıdaki çizim farklılıkları açıklığa kavuşturulur:

![Yığına geçilen varyansı gösteren diyagram.](./media/default-marshaling-for-objects/interop-variant-passed-value-reference.gif)
Değer ve başvuruya göre geçirilen çeşitler

**Nesneleri ve çeşitlemeleri değere göre hazırlama için varsayılan davranış**

- Nesneleri yönetilen koddan COM 'a geçirirken nesnenin içeriği sıralayıcı tarafından oluşturulan yeni bir varyanta kopyalanır ve bu, [nesneyi değişken olarak hazırlama](#marshaling-object-to-variant)bölümünde tanımlanan kurallar kullanılarak yapılır. Yönetilmeyen taraftaki VARIANT üzerinde yapılan değişiklikler, çağrıdan döndürülen özgün nesneye geri yayılmaz.

- Değişkenleri COM 'dan yönetilen koda geçirirken, varyantın içeriği, [değişken sıralama](#marshaling-variant-to-object)içinde tanımlanan kuralları kullanarak yeni oluşturulan bir nesneye kopyalanır. Yönetilen taraftaki nesnede yapılan değişiklikler, çağrıdan döndürülen özgün varyanta geri yayılmaz.

**Başvuruya göre nesneleri ve türevleri hazırlama için varsayılan davranış**

Değişiklikleri çağırana geri yaymak için, parametrelerin başvuruya göre geçirilmesi gerekir. Örneğin, parametreleri başvuruya göre geçirmek için C# ' deki **ref** anahtar sözcüğünü (veya Visual Basic yönetilen kodda **ByRef** ) kullanabilirsiniz. COM 'da, başvuru parametreleri **değişken \* **gibi bir işaretçi kullanılarak geçirilir.

- Bir nesneyi bir COM 'a başvuruya göre geçirirken Sıralayıcı yeni bir değişken oluşturur ve Nesne başvurusunun içeriğini çağrı yapılmadan önce varyanta kopyalar. Değişken, kullanıcının varyantın içeriğini değiştirmek için boş olduğu yönetilmeyen işleve geçirilir. Çağrıdan geri döndüğünüzde, yönetilmeyen taraftaki VARIANT üzerinde yapılan tüm değişiklikler özgün nesneye geri yayılır. Değişken türü, çağrıya geçirilen varyantın türünden farklıysa, değişiklikler farklı türdeki bir nesneye geri yayılır. Diğer bir deyişle, çağrıya geçirilen nesnenin türü, çağrıdan döndürülen nesne türünden farklı olabilir.

- Başvuruya göre yönetilen koda bir varyant geçirirken, Sıralayıcı yeni bir nesne oluşturur ve çağrıyı yapmadan önce değişkenin içeriğini nesnesine kopyalar. Nesnesine bir başvuru, kullanıcının nesneyi değiştirmek için ücretsiz olarak yönetilen işleve geçirilir. Çağrıdan geri döndüğünüzde, başvurulan nesnede yapılan tüm değişiklikler özgün varyanta geri yayılır. Nesnenin türü, çağrıya geçirilen nesne türünden farklıysa, özgün varyantın türü değiştirilir ve değer varyanta geri yayılır... Yine, çağrıya geçirilen varyantın türü, çağrıdan döndürülen VARIANT türünden farklı olabilir.

 **VT_BYREF bayrak kümesiyle bir değişkeni hazırlama için varsayılan davranış**

- Değere göre yönetilen koda geçirilen bir değişken, değişkenin bir değer yerine bir başvuru içerdiğini göstermek için **VT_BYREF** bayrak kümesine sahip olabilir. Bu durumda, değişken değer ile geçirildiğinden değişken hala bir nesne olarak sıralanır. Sıralayıcı, varyantın içeriğini otomatik olarak referans yapar ve çağrıyı yapmadan önce yeni oluşturulan bir nesneye kopyalar. Nesne daha sonra yönetilen işleve geçirilir; Ancak, çağrıdan dönüşte, nesne özgün varyanta geri yayılmaz. Yönetilen nesnede yapılan değişiklikler kaybedilir.

  > [!CAUTION]
  > Değişken **VT_BYREF** bayrak kümesine sahip olsa bile, değer tarafından geçirilen bir değişkenin değerini değiştirme yolu yoktur.

- Başvuruya göre yönetilen koda geçirilen bir değişken, değişkenin başka bir başvuru içerdiğini belirtmek için de **VT_BYREF** bayrak verebilir. Varsa, değişken başvuruya göre geçirildiğinden bir **başvuru** nesnesine göre sıralanır. Sıralayıcı, varyantın içeriğini otomatik olarak referans yapar ve çağrıyı yapmadan önce yeni oluşturulan bir nesneye kopyalar. Çağrıdan dönüşte, nesnenin değeri yalnızca nesnenin geçirildiği nesneyle aynı türde olması durumunda, özgün varyant içindeki başvuruya geri yayılır. Diğer bir deyişle, yayma **VT_BYREF** bayrak kümesiyle bir varyant türünü değiştirmez. Çağrı sırasında nesnenin türü değiştirilirse, <xref:System.InvalidCastException> çağrıdan döndürülen bir meydana gelir.

Aşağıdaki tabloda, çeşitler ve nesneler için yayma kuralları özetlenmektedir.

|Kaynak|Amaç|Geri yayılan değişiklikler|
|----------|--------|-----------------------------|
|**Değişken**  *v*|**Nesne**  *o*|Asla|
|**Nesne**  *o*|**Değişken**  *v*|Asla|
|**Değişken** ***\**** *BD*     |**Başvuru nesnesi**  *o*|Her zaman|
|**Başvuru nesnesi**  *o*|**Değişken** ***\**** *BD*     |Her zaman|
|**Değişken**  *v* **(VT_BYREF** *&#124;* **VT_ \* )**|**Nesne**  *o*|Asla|
|**Değişken**  *v* **(VT_BYREF** *&#124;* **VT_)**|**Başvuru nesnesi**  *o*|Yalnızca tür değişmemiştir.|

## <a name="see-also"></a>Ayrıca bkz.

- [Varsayılan Sıralama Davranışı](default-marshaling-behavior.md)
- [Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler](blittable-and-non-blittable-types.md)
- [Yönlü öznitelikler](/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))
- [Kopyalama ve Sabitleme](copying-and-pinning.md)
