---
title: Birlikte Çalışma Özniteliklerini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- design-time attributes
- .NET Framework, exposing components to COM
- attributes [.NET Framework], design-time functionality
- conversion-tool attributes
- attributes [.NET Framework], interop-specific
- attributes [.NET Framework], conversion-tool
- interoperation with unmanaged code, applying attributes
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
- COM interop, applying attributes
ms.assetid: b6014613-641c-4912-9e2f-83a99210a037
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 83afabf58048620b3b9936560f2b3fdf1e2039d5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61643679"
---
# <a name="applying-interop-attributes"></a>Birlikte Çalışma Özniteliklerini Uygulama
<xref:System.Runtime.InteropServices> Ad alanı, üç kategoriye birlikte çalışması özel özniteliklerin sağlar: Bu tasarım zamanında tarafından uygulanan, COM birlikte çalışma araçları ve API'leri tarafından dönüştürme işlemi sırasında uygulanan ve, veya COM birlikte çalışma tarafından uygulanır.  
  
 Yönetilen kod için öznitelikleri uygulama görevini sahibi değilseniz bkz [Extending Metadata Using Attributes](../../../docs/standard/attributes/index.md). Başka bir özel öznitelikle gibi türleri, yöntemleri, özellikleri, Parametreler, alanları ve diğer üyeleri birlikte çalışması özel öznitelikleri uygulayabilirsiniz.  
  
## <a name="design-time-attributes"></a>Tasarım zamanı öznitelikleri  
 Tasarım zamanı öznitelikleri kullanarak, COM birlikte çalışma araçları ve API'leri tarafından gerçekleştirilen dönüştürme işleminin sonucunu ayarlayabilirsiniz. Aşağıdaki tabloda, yönetilen kaynak kodunuzu uygulayabilirsiniz öznitelikleri açıklar. COM birlikte çalışma araçları, bazı durumlarda bu tabloda açıklanan öznitelikleri de uygulayabilirsiniz.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|<xref:System.Runtime.InteropServices.AutomationProxyAttribute>|Tür Otomasyon Sıralayıcı veya özel ara sunucu ve saptama kullanılarak sıralanmış olup olmadığını belirtir.|  
|<xref:System.Runtime.InteropServices.ClassInterfaceAttribute>|Bir sınıf için üretilen bir arabirim türünü denetler.|  
|<xref:System.Runtime.InteropServices.CoClassAttribute>|Tür kitaplığından içeri aktarıldı özgün coclass'ı CLSID değeri tanımlar.<br /><br /> COM birlikte çalışma araçları, bu öznitelik genellikle uygulayın.|  
|<xref:System.Runtime.InteropServices.ComImportAttribute>|Coclass'ı veya arabirim tanımı bir COM tür kitaplığından içeri aktarıldığını belirtir. Çalışma zamanı bu bayrağı nasıl etkinleştirip türü hazırlamak bilmeniz kullanır. Bu öznitelik, bir tür kitaplığına dışarı türü engeller.<br /><br /> COM birlikte çalışma araçları, bu öznitelik genellikle uygulayın.|  
|<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>|Derlemenin COM, kullanımınız için kaydedildiğinde böylece kullanıcı tarafından yazılan kodu kayıt işlemi sırasında yürütülebilecek bir yöntem çağrılması gerektiğini gösterir.|  
|<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>|Sınıf için olay kaynakları arabirimi tanımlar.<br /><br /> COM birlikte çalışma araçları, bu öznitelik uygulayabilirsiniz.|  
|<xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>|COM derleme silindiğinde kullanıcı tarafından yazılan kodu işlemi sırasında çalıştırabilmeniz için bir yöntem çağrılması gerektiğini gösterir.|  
|<xref:System.Runtime.InteropServices.ComVisibleAttribute>|Öznitelik değeri eşittir olduğunda türleri görünmez COM işler **false**. Bu öznitelik, tek bir türün veya COM görünürlüğünü denetlemek için tüm derleme için uygulanabilir. Varsayılan olarak, tüm yönetilen, genel türler görünür; öznitelik, onları görünür yapmak için gerekli değildir.|  
|<xref:System.Runtime.InteropServices.DispIdAttribute>|Bir yöntem veya alan COM gönderme tanımlayıcısının (DISPID) belirtir. Bu öznitelik DISPID yöntemi, alan veya onu anlatan özelliği içerir.<br /><br /> COM birlikte çalışma araçları, bu öznitelik uygulayabilirsiniz.|  
|<xref:System.Runtime.InteropServices.FieldOffsetAttribute>|İle kullanıldığında, bir sınıf içinde her alan fiziksel konumunu gösteren **StructLayoutAttribute**ve **LayoutKind** açık ayarlanır.|  
|<xref:System.Runtime.InteropServices.GuidAttribute>|Bir sınıf, arabirim veya tüm tür kitaplığında genel benzersiz tanıtıcısı (GUID) belirtir. Kabul edilebilir oluşturucu bağımsız değişken türü için bir biçimde özniteliğine geçirilen bir dize olmalıdır **System.Guid**.<br /><br /> COM birlikte çalışma araçları, bu öznitelik uygulayabilirsiniz.|  
|<xref:System.Runtime.InteropServices.IDispatchImplAttribute>|Gösteren **IDispatch** çift arabirimler ve görüntü arabirimlerinde vystavit gösterme, ortak dil çalışma zamanı kullanan uygulama arabirimi|  
|<xref:System.Runtime.InteropServices.InAttribute>|Veri, çağırana sıralanmalıdır olduğunu gösterir. Öznitelik parametreleri için kullanılabilir.|  
|<xref:System.Runtime.InteropServices.InterfaceTypeAttribute>|Yönetilen arabirimi COM istemcilerine (çift, IUnknown türetilmiş veya IDispatch yalnızca) nasıl kullanıma sunulduğunu denetler.<br /><br /> COM birlikte çalışma araçları, bu öznitelik uygulayabilirsiniz.|  
|<xref:System.Runtime.InteropServices.LCIDConversionAttribute>|Bir yönetilmeyen yöntem imzası bir LCID parametresi beklediğini belirtir.<br /><br /> COM birlikte çalışma araçları, bu öznitelik uygulayabilirsiniz.|  
|<xref:System.Runtime.InteropServices.MarshalAsAttribute>|Veri alanlarını veya parametreleri yönetilen ve yönetilmeyen kod arasında nasıl sıralanması gerektiğini belirtir. Varsayılan hazırlama davranışı her veri türüne sahip olduğundan öznitelik her zaman isteğe bağlıdır.<br /><br /> COM birlikte çalışma araçları, bu öznitelik uygulayabilirsiniz.|  
|<xref:System.Runtime.InteropServices.OptionalAttribute>|Parametre isteğe bağlı olduğunu gösterir.<br /><br /> COM birlikte çalışma araçları, bu öznitelik uygulayabilirsiniz.|  
|<xref:System.Runtime.InteropServices.OutAttribute>|Bir alan veya parametre verileri çağrılan bir nesneden geri çağırıcısına sıralanması gerekir olduğunu gösterir.|  
|<xref:System.Runtime.InteropServices.PreserveSigAttribute>|HRESULT veya retval imza dönüşümü bastırır normalde birlikte çalışabilirlik çağrılar sırasında gerçekleşir. Öznitelik tür kitaplığı dışarı aktarma hem de sıralama etkiler.<br /><br /> COM birlikte çalışma araçları, bu öznitelik uygulayabilirsiniz.|  
|<xref:System.Runtime.InteropServices.ProgIdAttribute>|Bir .NET Framework sınıf ProgID belirtir. Öznitelik sınıfları için kullanılabilir.|  
|<xref:System.Runtime.InteropServices.StructLayoutAttribute>|Bir sınıfın alanlarının fiziksel düzenini denetler.<br /><br /> COM birlikte çalışma araçları, bu öznitelik uygulayabilirsiniz.|  
  
## <a name="conversion-tool-attributes"></a>Dönüştürme aracı öznitelikleri  
 Aşağıdaki tabloda, COM birlikte çalışma araçları dönüştürme işlemi sırasında uygulanan öznitelikleri açıklanmaktadır. Tasarım zamanında bu öznitelikler geçerli değildir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|<xref:System.Runtime.InteropServices.ComAliasNameAttribute>|COM diğer adında bir parametre veya alan türünü gösterir. Alanlar, öznitelik parametreleri veya dönüş değerleri kullanabilirsiniz.|  
|<xref:System.Runtime.InteropServices.ComConversionLossAttribute>|Bu tür kitaplığından derleme içeri aktarılırken bir sınıf veya arabirim hakkında bilgi kaybı olmadığını gösterir.|  
|<xref:System.Runtime.InteropServices.ComEventInterfaceAttribute>|Kaynak arabirimi ve olay arabirimin yöntemlerini uygulayan bir sınıf tanımlar.|  
|<xref:System.Runtime.InteropServices.ImportedFromTypeLibAttribute>|Derleme ilk olarak bir COM tür kitaplığından içeri aktarıldığını belirtir. Bu öznitelik, özgün tür kitaplığına tür kitaplığı tanımı içeriyor.|  
|<xref:System.Runtime.InteropServices.TypeLibFuncAttribute>|İçeren **FUNCFLAGS** , başlangıçta içeri aktarılmadı COM tür kitaplığındaki bu işlev için.|  
|<xref:System.Runtime.InteropServices.TypeLibTypeAttribute>|İçeren **TYPEFLAGS** , başlangıçta içeri aktarılmadı COM tür kitaplığındaki bu tür.|  
|<xref:System.Runtime.InteropServices.TypeLibVarAttribute>|İçeren **VARFLAGS** , başlangıçta içeri aktarılmadı bu değişkeni COM tür kitaplığındaki.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices>
- [.NET Framework Bileşenlerini COM'da Gösterme](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)
- [Öznitelikler](../../../docs/standard/attributes/index.md)
- [Birlikte Çalışma için .NET Türlerini Niteleme](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md)
- [COM için Bütünleştirilmiş Kod Paketleme](../../../docs/framework/interop/packaging-an-assembly-for-com.md)
