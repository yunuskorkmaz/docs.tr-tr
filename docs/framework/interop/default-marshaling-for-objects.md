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
ms.openlocfilehash: 1b05d5c72491265b7617950550935e3c719421f3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076166"
---
# <a name="default-marshaling-for-objects"></a>Nesneler için Varsayılan Hazırlama
Parametreler ve alanlar olarak yazılan <xref:System.Object?displayProperty=nameWithType> yönetilmeyen koda aşağıdaki türlerden biri olarak kullanıma sunulabilir:  
  
-   Nesnesi bir parametre olduğunda bir değişken.  
  
-   Nesne yapısını alanı olduğunda bir arabirim.  
  
 Yalnızca COM birlikte çalışma hazırlama için nesne türlerini destekler. COM çeşitleri nesnelere hazırlamak için varsayılan davranıştır. Bu kurallar yalnızca türü için geçerli **nesne** ve türetilen bir türü kesin olarak belirtilmiş nesneler için geçerli değildir **nesne** sınıfı.  
  
## <a name="marshaling-options"></a>Hazırlama seçenekleri  
 Sıralama seçenekleri aşağıdaki tabloda gösterilmektedir **nesne** veri türü. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Özniteliği sağlayan çeşitli <xref:System.Runtime.InteropServices.UnmanagedType> numaralandırma değerleri için sıralama nesneleri.  
  
|Numaralandırma türü|Yönetilmeyen biçimi açıklaması|  
|----------------------|-------------------------------------|  
|**UnmanagedType.Struct**<br /><br /> (varsayılan parametreleri için)|Bir COM Stili değişken.|  
|**UnmanagedType.Interface**|Bir **IDispatch** arabirim, mümkünse; Aksi takdirde bir **IUnknown** arabirimi.|  
|**UnmanagedType.IUnknown**<br /><br /> (alanlar için varsayılan)|Bir **IUnknown** arabirimi.|  
|**UnmanagedType.IDispatch**|Bir **IDispatch** arabirimi.|  
  
 Aşağıdaki örnek, yönetilen arabirimi tanımını gösterir `MarshalObject`.  
  
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
  
 Aşağıdaki kod dışarı aktarmaları `MarshalObject` bir tür kitaplığı için arabirim.  
  
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
>  Birlikte çalışma sıralayıcısı, çağrıdan sonra ayrılan herhangi bir nesne değişkeni içinde otomatik olarak serbest bırakır.  
  
 Aşağıdaki örnek, biçimlendirilmiş değer türü gösterir.  
  
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
  
 Aşağıdaki kod biçimlendirilmiş türü için bir tür kitaplığı dışarı aktarır.  
  
```  
struct ObjectHolder {  
   VARIANT o1;  
   IDispatch *o2;  
}  
```  
  
## <a name="marshaling-object-to-interface"></a>Nesne arabirimi için hazırlama  
 Bir nesne, COM arabirim olarak sunulduğunda, bu yönetilen türü için sınıf arabirimi arabirimidir <xref:System.Object> ( **n_esne** arabirimi). Bu arabirim olarak yazılmış bir **IDispatch** (<xref:System.Runtime.InteropServices.UnmanagedType>) veya bir **IUnknown** (**UnmanagedType.IUnknown**) elde edilen tür kitaplığındaki. COM istemcileri dinamik olarak çağırmak yönetilen sınıf üyesi veya kendi türetilmiş sınıfları tarafından uygulanan herhangi bir üye **n_esne** arabirimi. İstemci Ayrıca, çağırabilirsiniz **QueryInterface** açıkça yönetilen tür tarafından uygulanan arabirimi elde edilir.  
  
## <a name="marshaling-object-to-variant"></a>Nesne değişken için hazırlama  
 İç değişken türünde bir nesne için bir değişken başvuruya çalışma zamanında, aşağıdaki kurallara göre belirlenir:  
  
-   Nesne başvurusu null ise (**hiçbir şey** Visual Basic'te), nesne türünde bir değişken için sıralanır **VT_EMPTY**.  
  
-   Nesne aşağıdaki tabloda listelenen herhangi bir türde bir örnek ise, sonuçta elde edilen değişken türü Sıralayıcı içinde oluşturulan ve tabloda belirtilen kurallar tarafından belirlenir.  
  
-   Hazırlama davranışı açıkça denetlemek için gereken diğer nesnelerin uygulayabilirsiniz <xref:System.IConvertible> arabirimi. Bu durumda, döndürülen tür kod değişken türü belirlenir <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> yöntemi. Aksi takdirde, nesne türünde bir değişken sıralanır **VT_UNKNOWN**.  
  
### <a name="marshaling-system-types-to-variant"></a>Değişken için sistem türlerini hazırlama  
 Aşağıdaki tabloda, yönetilen nesne türlerini ve bunların karşılık gelen COM değişken türlerine gösterir. Çağrılan yöntem imzası türü olduğunda, bu tür dönüştürülür <xref:System.Object?displayProperty=nameWithType>.  
  
|Nesne türü|COM değişken türü|  
|-----------------|----------------------|  
|Null Nesne başvurusu (**hiçbir şey** Visual Basic'te).|**VT_EMPTY**|  
|<xref:System.DBNull?displayProperty=nameWithType>|**VT_NULL**|  
|<xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>|**VT_ERROR**|  
|<xref:System.Reflection.Missing?displayProperty=nameWithType>|**VT_ERROR** ile **E_PARAMNOTFOUND**|  
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
  
 Kullanarak `MarshalObject` önceki örnekte, aşağıdaki kod örneğinde tanımlanan arabirimi çeşitleri çeşitli türlerdeki bir COM sunucuya geçirmek nasıl gösterir.  
  
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
  
 Karşılık gelen yönetilen türleri COM türleri sıralanmış sarmalayıcı sınıflar gibi kullanarak <xref:System.Runtime.InteropServices.ErrorWrapper>, <xref:System.Runtime.InteropServices.DispatchWrapper>, <xref:System.Runtime.InteropServices.UnknownWrapper>, ve <xref:System.Runtime.InteropServices.CurrencyWrapper>. Aşağıdaki kod örneği, bu sarmalayıcılar çeşitleri çeşitli türlerdeki bir COM sunucuya geçirmek için nasıl kullanılacağını gösterir.  
  
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
  
 Sarmalayıcı sınıflar tanımlanan <xref:System.Runtime.InteropServices> ad alanı.  
  
### <a name="marshaling-the-iconvertible-interface-to-variant"></a>IConvertible arabirimi değişken için hazırlama  
 Önceki bölümde listelenen nasıl bunlar uygulayarak sıralanmış denetleyebilirsiniz daha diğer türleri <xref:System.IConvertible> arabirimi. Nesne uyguluyorsa **IConvertible** arabirimi, COM değişken türü, çalışma zamanında değeri tarafından belirlenir <xref:System.TypeCode> döndürüldüğü numaralandırma <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> yöntemi.  
  
 İçin olası değerler aşağıdaki tabloda gösterilmektedir **TypeCode** sabit listesi ve her bir değer için karşılık gelen COM değişken türü.  
  
|Typecode'u işlenemiyor|COM değişken türü|  
|--------------|----------------------|  
|**TypeCode.Empty**|**VT_EMPTY**|  
|**TypeCode.Object**|**VT_UNKNOWN**|  
|**TypeCode.DBNull**|**VT_NULL**|  
|**TypeCode.Boolean**|**VT_BOOL**|  
|**TypeCode.Char**|**VT_UI2**|  
|**TypeCode.Sbyte**|**VT_I1**|  
|**TypeCode.Byte**|**VT_UI1**|  
|**TypeCode.Int16**|**VT_I2**|  
|**TypeCode.UInt16**|**VT_UI2**|  
|**TypeCode.Int32**|**VT_I4**|  
|**TypeCode.UInt32**|**VT_UI4**|  
|**TypeCode.Int64**|**VT_I8**|  
|**TypeCode.UInt64**|**VT_UI8**|  
|**TypeCode.Single**|**VT_R4**|  
|**TypeCode.Double**|**VT_R8**|  
|**TypeCode.Decimal**|**VT_DECIMAL**|  
|**TypeCode.DateTime**|**VT_DATE**|  
|**TypeCode.String**|**VT_BSTR**|  
|Desteklenmez.|**VT_INT**|  
|Desteklenmez.|**VT_UINT**|  
|Desteklenmez.|**VT_ARRAY**|  
|Desteklenmez.|**VT_RECORD**|  
|Desteklenmez.|**VT_CY**|  
|Desteklenmez.|**VT_VARIANT**|  
  
 COM değişken değerini çağırarak belirlenir **IConvertible.To** *türü* arabirimi, burada **için** *türü* dönüştürme öğesinden döndürülen türüne karşılık gelen yordamı **IConvertible.GetTypeCode**. Örneğin, döndüren bir nesne **TypeCode.Double** gelen **IConvertible.GetTypeCode** COM türünde sıralanmış **VT_R8**. Değişken değeri elde edebilirsiniz (depolanan **dblVal** COM değişkeni alan) tarafından atamayı **IConvertible** arabirimi ve arama <xref:System.IConvertible.ToDouble%2A> yöntemi.  
  
## <a name="marshaling-variant-to-object"></a>VARIANT nesnesi için hazırlama  
 Üretilen ne zaman bir nesne, türü ve bazen değerini sıralanmış değişken için bir VARIANT'ı hazırlama nesne türünü belirler. Aşağıdaki tabloda her değişken türünde bir değişken COM'dan .NET Framework geçirildiğinde Sıralayıcı oluşturur karşılık gelen nesne türünü belirler.  
  
|COM değişken türü|Nesne türü|  
|----------------------|-----------------|  
|**VT_EMPTY**|Null Nesne başvurusu (**hiçbir şey** Visual Basic'te).|  
|**VT_NULL**|<xref:System.DBNull?displayProperty=nameWithType>|  
|**VT_DISPATCH**|**System.comobject'e** veya null ise (pdispVal == null)|  
|**VT_UNKNOWN**|**System.comobject'e** veya null ise (punkVal == null)|  
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
|**VT_RECORD**|Paketlenmiş değer türü karşılık gelen.|  
|**VT_VARIANT**|Desteklenmez.|  
  
 Değişken türleri için COM'dan geçirilen yönetilen kod ve daha sonra geri COM için aynı değişken türünde çağrı süresi boyunca koruyamayabilir. Türünde bir değişken olduğunda ne olacağını düşünün **gt; vt_dıspatch &** COM'dan .NET Framework geçirilir. Hazırlama sırasında değişken dönüştürülür bir <xref:System.Object?displayProperty=nameWithType>. Varsa **nesne** ardından geçirilen geri COM için geri türünde bir değişken için sıralanır **VT_UNKNOWN**. Başlangıçta nesne oluşturmak için kullanılan bir değişken aynı türde bir nesne için COM yönetilen koddan başvuruya üretilen değişken olacağını garanti yoktur.  
  
## <a name="marshaling-byref-variants"></a>ByRef çeşitleri hazırlama  
 Değere veya başvuruya göre çeşitleri kendilerini geçirilebilir ancak **VT_BYREF** bayrağı de kullanılabilir herhangi bir değişken türü değişken içeriğini yerine başvuruya göre geçirilen belirtmek için değere göre. Çeşitleri başvuruya göre sıralama ve bir değişken ile hazırlama arasındaki farkı **VT_BYREF** bayrağı kafa karıştırıcı olabilir. Aşağıdaki çizim farklılıkları açıklar:  
  
 ![Değişken gösteren diyagram yığında geçirildi.](./media/default-marshaling-for-objects/interop-variant-passed-value-reference.gif)  
Değere ve başvuruya göre geçirilen çeşitleri  
  
 **Nesneleri ve değişkenleri değere göre sıralama için varsayılan davranış**  
  
-   Nesneleri, COM yönetilen koddan geçirirken, nesnenin içeriğini tanımlanan kuralların kullanarak sıralayıcı tarafından oluşturulan yeni bir değişken içine kopyalanır [değişken hazırlama nesnesine](#marshaling-object-to-variant). Yönetilmeyen tarafında değişken yapılan değişiklikleri çağrısından dönüşte özgün nesneye geri yayılmaz.  
  
-   Çeşitleri için yönetilen kod COM'dan geçirirken, değişken içeriğini tanımlanan kuralların kullanarak yeni oluşturulan bir nesneye kopyalanır [hazırlama değişken nesneye](#marshaling-variant-to-object). Yönetilen tarafında nesneye yapılan değişiklikleri geri çağrısından dönüşte özgün değişken için yayılmaz.  
  
 **Nesneleri ve değişkenleri başvuruya göre hazırlama için varsayılan davranış**  
  
 Değişiklikleri tekrar çağırana yayılmasına parametreleri başvuruya göre geçirilmelidir. Örneğin, kullanabilirsiniz **ref** anahtar sözcüğünü C# (veya **ByRef** yönetilen kod Visual Basic) başvuru ile parametreleri iletme. COM, başvuru parametreleri gibi bir işaretçi kullanılarak geçirilen bir **değişken \*** .  
  
-   Bir nesne için COM başvuruya göre geçirme, Sıralayıcı yeni bir değişken oluşturur ve çağrı yapılmadan önce değişken bir nesne başvurusu içeriğini kopyalar. Değişken, kullanıcının değişken içeriğini değiştirmek ücretsiz olduğu yönetilmeyen işleve geçirilir. Geri çağrısından, yönetilmeyen tarafında değişken yapılan tüm değişiklikler özgün nesneye geri yayılır. Ardından bir çağrısına geçirilen değişken türünde bir değişken türünde farklıdır, değişiklikleri geri farklı türde bir nesne için yayılır. Diğer bir deyişle, çağrısına geçirilen nesne türü çağrısından döndürülen nesnenin türü farklı olabilir.  
  
-   Bir değişken başvuru ile yönetilen kod için geçirirken, Sıralayıcı yeni bir nesne oluşturur ve çağrı yapmadan önce değişken içeriğini nesnesine kopyalar. Nesnesine bir başvuru, kullanıcının bir nesneyi değiştirmek ücretsiz olduğu yönetilen bir işleve geçirilir. Geri çağrısından, başvurulan nesneye yapılan tüm değişiklikler özgün değişkenine geri yayılır. Nesne türü çağrısına geçirilen nesnenin türü farklı olması durumunda, özgün değişken türü değiştirilir ve değeri değişken geri yayılır. Yeniden çağrısına geçirilen değişken türünü çağrısından döndürülen değişken türünden farklı olabilir.  
  
 **Bir değişken VT_BYREF bayrağı ayarlanmış hazırlama için varsayılan davranış**  
  
-   Yönetilen kod için değere göre geçirilen bir değişken olabilir **VT_BYREF** bayrağı ayarlanmış değişken bir değer yerine bir başvuru içerdiğini belirtmek için. Bu durumda, değişken değer olarak geçilemez çünkü değişken hala bir nesneye sıralanır. Sıralayıcı otomatik olarak başvuru varyantı içeriğini ve çağrı yapmadan önce yeni oluşturulan bir nesneye kopyalar. Nesne, daha sonra yönetilen işleve geçirilir; Bununla birlikte, geri çağrısından, nesneyi geri özgün değişken dağıtılmadı. Yönetilen nesneye yapılan değişiklikler kaybolur.  
  
    > [!CAUTION]
    >  Değişken olsa bile, değer olarak geçilemez bir değişken değerini değiştirmek için bir yolu yoktur **VT_BYREF** bayrağı ayarlanmış.  
  
-   Yönetilen kod için başvuruya göre geçirilen bir değişken bulundurabilirsiniz **VT_BYREF** bayrağı ayarlanmış başka bir başvuru varyantı içerdiğini belirtmek için. Değişken sıralanmış olduğundan bulursa, bir **ref** değişken başvuruyla geçirildi çünkü nesne. Sıralayıcı otomatik olarak başvuru varyantı içeriğini ve çağrı yapmadan önce yeni oluşturulan bir nesneye kopyalar. Geçirilen nesne olarak yalnızca nesneyi aynı türde ise geri çağrısından, nesnenin değerini geri başvuru özgün değişken içinde yayılır. Diğer bir deyişle, yayma ile bir değişken türünü değiştirmez **VT_BYREF** bayrağı ayarlanmış. Nesne türü aramasında değiştirilirse bir <xref:System.InvalidCastException> çağrısından dönüşte gerçekleşir.  
  
 Aşağıdaki tabloda çeşitleri ve nesneler için yayma kuralları özetlenmektedir.  
  
|Başlangıç|Bitiş|Değişiklikleri geri yayılmaz|  
|----------|--------|-----------------------------|  
|**Değişken***v*|**Nesne***o*|hiçbir zaman|  
|**Nesne***o*|**Değişken***v*|hiçbir zaman|  
|**Değişken*****\*****BD*|**Ref nesne***o*|Her zaman|  
|**Ref nesne***o*|**Değişken*****\*****BD*|Her zaman|  
|**Değişken***v* **(VT_BYREF** *&#124;* **VT_\*)** |**Nesne***o*|hiçbir zaman|  
|**Değişken***v* **(VT_BYREF** *&#124;* **VT_)** |**Ref nesne***o*|Yalnızca türü değişmemişse.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Varsayılan Sıralama Davranışı](default-marshaling-behavior.md)
- [Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler](blittable-and-non-blittable-types.md)
- [Yönlü Öznitelikler](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))
- [Kopyalama ve Sabitleme](copying-and-pinning.md)
