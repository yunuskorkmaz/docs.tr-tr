---
title: Nesneler için Varsayılan Sıralama
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- objects, interop marshaling
- interop marshaling, objects
ms.assetid: c2ef0284-b061-4e12-b6d3-6a502b9cc558
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6980db381322d354cace38709586e50681ae0a7e
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
---
# <a name="default-marshaling-for-objects"></a>Nesneler için Varsayılan Hazırlama
Parametreler ve alanlar olarak yazılan <xref:System.Object?displayProperty=nameWithType> yönetilmeyen kod için şu türlerden biri olarak gösterilebilir:  
  
-   Nesne bir parametre olduğunda bir değişken.  
  
-   Nesne yapısı alan olduğunda bir arabirim.  
  
 Nesne türleri için hazırlama yalnızca COM birlikte çalışma destekler. COM çeşitleri nesnelere sıralamakta varsayılan davranıştır. Bu kurallar yalnızca türü için geçerli **nesne** ve türetilen kesin türü belirtilmiş nesne için geçerli değildir **nesne** sınıfı.  
  
 Bu konu hakkında nesnetürleri hazırlama aşağıdaki ek bilgileri sağlar:  
  
-   [Hazırlama seçenekleri](#cpcondefaultmarshalingforobjectsanchor7)  
  
-   [Arabirim nesnesine hazırlama](#cpcondefaultmarshalingforobjectsanchor2)  
  
-   [Nesne değişken için hazırlama](#cpcondefaultmarshalingforobjectsanchor3)  
  
-   [VARIANT nesnesi için hazırlama](#cpcondefaultmarshalingforobjectsanchor4)  
  
-   [ByRef çeşitleri hazırlama](#cpcondefaultmarshalingforobjectsanchor6)  
  
<a name="cpcondefaultmarshalingforobjectsanchor7"></a>   
## <a name="marshaling-options"></a>Hazırlama seçenekleri  
 Hazırlama seçenekleri aşağıdaki tabloda gösterilmektedir **nesne** veri türü. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Özniteliği sağlayan birkaç <xref:System.Runtime.InteropServices.UnmanagedType> numaralandırma değerleri sıralama nesnelere.  
  
|Numaralandırma türü|Yönetilmeyen biçimi açıklaması|  
|----------------------|-------------------------------------|  
|**UnmanagedType.Struct**<br /><br /> (varsayılan parametreler için)|Bir COM Stili değişken.|  
|**UnmanagedType.Interface**|Bir **IDispatch** arabirim, mümkünse; Aksi halde, bir **IUnknown** arabirimi.|  
|**UnmanagedType.IUnknown**<br /><br /> (alanlar için varsayılan)|Bir **IUnknown** arabirimi.|  
|**UnmanagedType.IDispatch**|Bir **IDispatch** arabirimi.|  
  
 Aşağıdaki örnek yönetilen arabirimi tanımını gösterir `MarshalObject`.  
  
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
  
 Aşağıdaki kod dışarı `MarshalObject` bir tür kitaplığı için arabirim.  
  
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
>  Birlikte çalışma Sıralayıcı değişken içinde herhangi bir ayrılmış nesne çağrısından sonra otomatik olarak boşaltır.  
  
 Aşağıdaki örnekte bir biçimlendirilmiş değer türü gösterilmektedir.  
  
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
  
<a name="cpcondefaultmarshalingforobjectsanchor2"></a>   
## <a name="marshaling-object-to-interface"></a>Arabirim nesnesine hazırlama  
 Bir nesne COM arabirim olarak sunulduğunda, bu arabirim sınıfı için yönetilen türü arabirimdir <xref:System.Object> ( **_Object** arabirimi). Bu arabirim olarak yazılan bir **IDispatch** (<xref:System.Runtime.InteropServices.UnmanagedType>) veya bir **IUnknown** (**UnmanagedType.IUnknown**) sonuçta elde edilen türü Kitaplığı'nda. COM istemcileri dinamik olarak çağırma yönetilen sınıf üyeleri veya türetilmiş sınıflarından tarafından uygulanan herhangi bir üye **_Object** arabirimi. İstemci ayrıca çağırabilirsiniz **QueryInterface** açıkça yönetilen türü tarafından uygulanan arabirimi elde edilir.  
  
<a name="cpcondefaultmarshalingforobjectsanchor3"></a>   
## <a name="marshaling-object-to-variant"></a>Nesne değişken için hazırlama  
 Bir nesne için bir değişken sıralanmış, iç değişken türü aşağıdaki kurallara göre çalışma zamanında belirlenir:  
  
-   Nesne başvurusu null ise (**hiçbir şey** Visual Basic'te), nesne türünde bir değişken için sıralanmış **VT_EMPTY**.  
  
-   Aşağıdaki tabloda listelenen herhangi bir türde bir örneğiyse, sonuçta elde edilen değişken türü Sıralayıcı yerleşik ve tabloda gösterilen kuralları tarafından belirlenir.  
  
-   Açıkça hazırlama davranışı denetlemek için gereken diğer nesneleri uygulayabilirsiniz <xref:System.IConvertible> arabirimi. Bu durumda, döndürülen türü kodu değişken türü saptanır <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> yöntemi. Nesne türünde bir değişken Aksi halde, sıralanmış **VT_UNKNOWN**.  
  
### <a name="marshaling-system-types-to-variant"></a>Değişken için sistem türlerini hazırlama  
 Aşağıdaki tabloda, yönetilen nesne türlerini ve bunların karşılık gelen COM değişken türlerine gösterir. Çağrılan yöntem imzası türü olduğunda bu tür dönüştürülür <xref:System.Object?displayProperty=nameWithType>.  
  
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
  
 Kullanarak `MarshalObject` önceki örnekte, aşağıdaki kod örneğinde tanımlanan arabirimi çeşitleri çeşitli türleri COM sunucuya geçirmek nasıl gösterir.  
  
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
  
 Karşılık gelen yönetilen türleri COM türleri sıralanmış sarmalayıcı sınıflar gibi kullanılarak <xref:System.Runtime.InteropServices.ErrorWrapper>, <xref:System.Runtime.InteropServices.DispatchWrapper>, <xref:System.Runtime.InteropServices.UnknownWrapper>, ve <xref:System.Runtime.InteropServices.CurrencyWrapper>. Aşağıdaki kod örneğinde bu sarmalayıcıları çeşitleri çeşitli türleri COM sunucuya geçirmek için nasıl kullanılacağı gösterilmektedir.  
  
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
  
 Sarmalayıcı sınıfları tanımlanan <xref:System.Runtime.InteropServices> ad alanı.  
  
### <a name="marshaling-the-iconvertible-interface-to-variant"></a>IConvertible arabirimi değişken için hazırlama  
 Önceki bölümde listelenenler nasıl bunlar uygulayarak sıralanmış denetleyebilirsiniz daha diğer türleri <xref:System.IConvertible> arabirimi. Nesne uyguluyorsa **IConvertible** arabirimi, COM değişken türü, çalışma zamanında değeri tarafından belirlenir <xref:System.TypeCode> döndürülen numaralandırma <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> yöntemi.  
  
 İçin olası değerler aşağıdaki tabloda gösterilmektedir **TypeCode** numaralandırma ve her bir değer için karşılık gelen COM değişken türü.  
  
|TypeCode|COM değişken türü|  
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
|Desteklenmiyor.|**VT_INT**|  
|Desteklenmiyor.|**VT_UINT**|  
|Desteklenmiyor.|**VT_ARRAY**|  
|Desteklenmiyor.|**VT_RECORD**|  
|Desteklenmiyor.|**VT_CY**|  
|Desteklenmiyor.|**VT_VARIANT**|  
  
 COM değişken değerini çağrılarak belirlenen **IConvertible.To** *türü* arabirimi, burada **için** *türü* dönüştürme döndürüldü türüne karşılık gelen yordamı **IConvertible.GetTypeCode**. Örneğin, döndüren bir nesne **TypeCode.Double** gelen **IConvertible.GetTypeCode** türünde COM değişken sıralanmış **VT_R8**. Değişken değeri elde edebilirsiniz (depolanan **dblVal** COM variant alanını) çevrim tarafından **IConvertible** arabirimi ve arama <xref:System.IConvertible.ToDouble%2A> yöntemi.  
  
<a name="cpcondefaultmarshalingforobjectsanchor4"></a>   
## <a name="marshaling-variant-to-object"></a>VARIANT nesnesi için hazırlama  
 Üretti. ne zaman bir nesne, türü ve bazen değerini sıralanmış değişken için bir değişken hazırlama nesne türünü belirler. Aşağıdaki tabloda, her bir değişken türü ve bir değişken için .NET Framework COM geçirildiğinde Sıralayıcı oluşturur karşılık gelen nesne türünü tanımlar.  
  
|COM değişken türü|Nesne türü|  
|----------------------|-----------------|  
|**VT_EMPTY**|Null Nesne başvurusu (**hiçbir şey** Visual Basic'te).|  
|**VT_NULL**|<xref:System.DBNull?displayProperty=nameWithType>|  
|**VT_DISPATCH**|**System.__ComObject** ya da null ise (pdispVal null ==)|  
|**VT_UNKNOWN**|**System.__ComObject** ya da null ise (punkVal null ==)|  
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
|**VT_ARRAY** &#124; **VT_\***|<xref:System.Array?displayProperty=nameWithType>|  
|**VT_CY**|<xref:System.Decimal?displayProperty=nameWithType>|  
|**VT_RECORD**|Paketlenmiş değer türüne karşılık gelen.|  
|**VT_VARIANT**|Desteklenmiyor.|  
  
 VARIANT türleri COM gelen geçirilen yönetilen kodu ve ardından geri COM aynı değişken türü çağrı süresince korumak değil. Türünde bir değişken olduğunda ne olacağını düşünün **VT_DISPATCH** COM .NET Framework geçirilir. Hazırlama sırasında değişken dönüştürülür bir <xref:System.Object?displayProperty=nameWithType>. Varsa **nesne** sonra geçirilen geri COM için geri türünde bir değişken için sıralanmış olduğundan **VT_UNKNOWN**. Başlangıçta nesne üretmek için kullanılan değişken aynı türde bir nesne COM yönetilen koddan sıralanmış zaman üretilen değişken olacaktır garantisi yoktur.  
  
<a name="cpcondefaultmarshalingforobjectsanchor6"></a>   
## <a name="marshaling-byref-variants"></a>ByRef çeşitleri hazırlama  
 Türevleri kendilerini değere veya başvuruya göre geçirilen rağmen **VT_BYREF** bayrağı de kullanılabilir ile herhangi bir değişken türü değişken içeriğini yerine başvuruya geçirilen göstermek için değeri. Çeşitleri başvuruya göre sıralama ve bir türevi hazırlama arasındaki farkı **VT_BYREF** bayrağı ayarlanmış kafa karıştırıcı olabilir. Aşağıdaki çizimde farklılıkları açıklar.  
  
 ![Değişken geçilen yığınındaki](./media/interopvariant.gif "interopvariant")  
Değer ve başvuru tarafından geçirilen çeşitleri  
  
 **Nesneleri ve değişkenleri değere göre sıralama için varsayılan davranış**  
  
-   Nesneleri COM yönetilen koddan geçirirken, nesnenin içeriğinin tanımlanan kuralların kullanarak sıralayıcı tarafından oluşturulan yeni bir değişken içine kopyalanır [değişken hazırlama nesnesine](#cpcondefaultmarshalingforobjectsanchor3). Yönetilmeyen tarafında değişken yapılan değişiklikleri geri dönüş çağrısından özgün nesne için yayılmaz.  
  
-   Çeşitleri yönetilen kod için COM geçirirken, değişken içerikleri tanımlanan kuralların kullanarak yeni oluşturulan bir nesne için kopyalanır [hazırlama değişken nesnesine](#cpcondefaultmarshalingforobjectsanchor4). Yönetilen tarafında nesnede yapılan değişiklikleri geri dönüş çağrısından özgün değişken için yayılmaz.  
  
 **Nesneleri ve değişkenleri başvuruya göre sıralama için varsayılan davranış**  
  
 Çağırana geri değişiklikleri yaymak için parametreleri başvuruyla geçirilmelidir. Örneğin, kullanabileceğiniz **ref** C# anahtar sözcüğü (veya **ByRef** Visual Basic'te yönetilen kod) başvuruya göre parametreleri geçirmek için. COM'da, başvuru parametreleri bir işaretçi gibi kullanılarak geçirilen bir **değişken \*** .  
  
-   Bir nesne COM başvuruya göre geçirme, Sıralayıcı yeni bir değişken oluşturur ve çağrı yapılmadan önce nesne başvurusu içeriğini değişken kopyalar. Değişken, kullanıcının değişken içeriğini değiştirmek boş olduğu yönetilmeyen işleve geçirilir. Çağrısından getirisi yönetilmeyen tarafında değişken yapılan değişiklikler orijinal nesneyi yayılır. Değişken türü çağrısı geçirilen değişken türünü farklıysa, değişiklikleri geri farklı bir türde bir nesne için yayılır. Diğer bir deyişle, çağrısına geçirilen nesne türünü çağrısından döndürülen nesne türünü farklı olabilir.  
  
-   Bir değişken başvurusu tarafından yönetilen koda geçirirken, Sıralayıcı yeni bir nesne oluşturur ve arama yapmadan önce değişken içeriğini nesnesine kopyalar. Nesneye bir başvurusu, kullanıcının bir nesneyi değiştirmek boş olduğu yönetilen bir işleve geçirilir. Çağrısından getirisi başvurulan nesneye yapılan değişiklikler özgün değişkenine yayılır. Nesne türünü çağrısı geçirilen nesne türünü farklıysa, özgün değişken türünü değiştirilir ve geri değişken değeri yayılır. Yeniden çağrısına geçirilen değişken türünü çağrısından döndürülen variant türü farklı olabilir.  
  
 **Bir değişken VT_BYREF bayrağı ayarlanmış hazırlama için varsayılan davranış**  
  
-   Yönetilen kod için değeri tarafından geçirilen bir değişken olabilir **VT_BYREF** bayrağı değişken değeri yerine bir başvuru içeriyor belirtmek üzere ayarlanmış. Bu durumda, değişken değeri tarafından geçtiğinden değişken hala bir nesneye başvuruya. Sıralayıcı otomatik olarak değişken içeriğini dereferences ve arama yapmadan önce yeni oluşturulan nesnesine kopyalar. Nesne daha sonra yönetilen işlevdeki geçirilir; Ancak, çağrısından getirisi geri özgün türevi nesne dağıtılmaz. Yönetilen nesneye yapılan değişiklikler kaybolur.  
  
    > [!CAUTION]
    >  Değişken olsa bile değer ile geçirilen bir değişken değerini değiştirmek mümkün **VT_BYREF** bayrağı ayarlanmış.  
  
-   Yönetilen kod için başvuru tarafından geçirilen bir değişken de sağlayabilirsiniz **VT_BYREF** bayrağı değişken başka bir başvuru içeriyor belirtmek üzere ayarlanmış. Değişken sıralanmış olduğundan bulursa, bir **ref** değişken başvuruya göre geçtiğinden nesne. Sıralayıcı otomatik olarak değişken içeriğini dereferences ve arama yapmadan önce yeni oluşturulan nesnesine kopyalar. Nesne geçirilen gibi yalnızca nesne aynı türde ise çağrısından getirisi nesnenin değerini geri başvuru özgün türevi içinde yayılır. Diğer bir deyişle, yayma ile bir değişken türü değiştirmez **VT_BYREF** bayrağı ayarlanmış. Nesne türü aramasında değişirse bir <xref:System.InvalidCastException> çağrısından döndürülen oluşur.  
  
 Aşağıdaki tabloda çeşitleri ve nesneler için yayma kuralları özetler.  
  
|From|Amaç|Geri yayılma değişiklikleri|  
|----------|--------|-----------------------------|  
|**Değişken***v*|**Nesne***o* |Hiçbir zaman|  
|**Nesne***o* |**Değişken***v*|Hiçbir zaman|  
|**Değişken*****\*****pv*|**Ref nesne***o* |Her zaman|  
|**Ref nesne***o* |**Değişken*****\*****pv*|Her zaman|  
|**Değişken***v* **(VT_BYREF** *&#124;* **VT_\*)** |**Nesne***o* |Hiçbir zaman|  
|**Değişken***v* **(VT_BYREF** *&#124;* **VT_)** |**Ref nesne***o* |Yalnızca türü değişmemişse.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Varsayılan Hazırlama Davranışı](default-marshaling-behavior.md)  
 [Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler](blittable-and-non-blittable-types.md)  
 [Tek yönlü öznitelikleri](https://msdn.microsoft.com/library/241ac5b5-928e-4969-8f58-1dbc048f9ea2(v=vs.100))  
 [Kopyalama ve Sabitleme](copying-and-pinning.md)
