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
ms.openlocfilehash: 554ea7c54973852510e539000baf03bdce8e7bcf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="applying-interop-attributes"></a>Birlikte Çalışma Özniteliklerini Uygulama
<xref:System.Runtime.InteropServices> Ad alanı, üç kategoride birlikte çalışmaya özgü özniteliklerin sağlar: olanlar sizin tarafınızdan tasarım zamanında uygulanan, olanlar COM birlikte çalışma Araçlar ve API'ler tarafından dönüştürme işlemi sırasında uygulanan ve bu da siz veya COM birlikte çalışma tarafından uygulanan.  
  
 Yönetilen kod için öznitelikleri uygulama görevini alışık istiyorsanız bkz [genişletme meta verileri kullanarak özniteliklerini](../../../docs/standard/attributes/index.md). Diğer özel öznitelikleri gibi türleri, yöntemler, özellikler, parametreleri, alanları ve diğer üyeleri birlikte çalışmaya özgü öznitelikleri uygulayabilirsiniz.  
  
## <a name="design-time-attributes"></a>Tasarım zamanı öznitelikleri  
 Tasarım zamanı öznitelikleri kullanarak COM birlikte çalışma Araçlar ve API'ler tarafından gerçekleştirilen dönüştürme işleminin sonucunu ayarlayabilirsiniz. Aşağıdaki tabloda, yönetilen kaynak kodunuzu uygulayabilirsiniz öznitelikleri açıklanmaktadır. COM birlikte çalışma araçları, durum, bu tabloda açıklanan öznitelikleri de uygulanabilir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|<xref:System.Runtime.InteropServices.AutomationProxyAttribute>|Tür Otomasyon Sıralayıcı veya özel proxy ve saplama kullanılarak sıralanmış olup olmadığını belirtir.|  
|<xref:System.Runtime.InteropServices.ClassInterfaceAttribute>|Sınıfı için üretilen arabirimi türünü denetler.|  
|<xref:System.Runtime.InteropServices.CoClassAttribute>|Tür kitaplığından içeri aktarıldı özgün coclass'ı CLSID tanımlar.<br /><br /> COM birlikte çalışma araçları genellikle bu özniteliğini uygulayın.|  
|<xref:System.Runtime.InteropServices.ComImportAttribute>|Coclass'ı veya arabirim tanımı bir COM tür kitaplığından içeri aktarıldı gösterir. Çalışma zamanı Bu bayrak nasıl etkinleştirip türü hazırlamak bilmeniz kullanır. Bu öznitelik türü geri bir tür kitaplığı dışarı engelliyor.<br /><br /> COM birlikte çalışma araçları genellikle bu özniteliğini uygulayın.|  
|<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>|COM, kullanımdan için kaydedilen derleme, böylece kullanıcı tarafından yazılan kodu kayıt işlemi sırasında yürütülebilir bir yöntem çağrılması gerektiğini gösterir.|  
|<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>|Sınıfı için olayların kaynakları arabirimlerini tanımlar.<br /><br /> COM birlikte çalışma araçları, bu öznitelik uygulayabilirsiniz.|  
|<xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>|Derleme COM kaydı olduğunda kullanıcı tarafından yazılan kodu işlemi sırasında çalıştırabilmeniz için bir yöntem çağrılması gerektiğini gösterir.|  
|<xref:System.Runtime.InteropServices.ComVisibleAttribute>|Öznitelik değeri eşit olduğunda türleri görünmez COM işler **false**. Bu öznitelik, tek bir türün veya tüm bütünleştirilmiş COM görünürlüğü denetlemek için uygulanabilir. Varsayılan olarak, tüm yönetilen, genel türleri görünür; öznitelik görünür hale getirmek için gerekli değildir.|  
|<xref:System.Runtime.InteropServices.DispIdAttribute>|Yöntem veya alan COM gönderme tanımlayıcısını (DISPID) belirtir. Bu öznitelik DISPID yöntemi, alan veya açıkladığı özelliği içerir.<br /><br /> COM birlikte çalışma araçları, bu öznitelik uygulayabilirsiniz.|  
|<xref:System.Runtime.InteropServices.FieldOffsetAttribute>|İle kullanıldığında bir sınıftaki her bir alan fiziksel konumunu gösterir **StructLayoutAttribute**ve **LayoutKind** Explicit için ayarlanır.|  
|<xref:System.Runtime.InteropServices.GuidAttribute>|Genel benzersiz tanıtıcısı (GUID), bir sınıf, arabirim veya tüm tür kitaplığı belirtir. Özniteliğe geçirilen dize türü için kabul edilebilir oluşturucu bağımsız değişken bir biçimde olmalıdır **System.Guid**.<br /><br /> COM birlikte çalışma araçları, bu öznitelik uygulayabilirsiniz.|  
|<xref:System.Runtime.InteropServices.IDispatchImplAttribute>|Belirten **IDispatch** arabirim uygulaması çift arabirimler ve COM dispinterfaces gösterme, ortak dil çalışma zamanı kullanır|  
|<xref:System.Runtime.InteropServices.InAttribute>|Veri içinde çağırana sıralanmalıdır olduğunu gösterir. Öznitelik parametreleri için kullanılabilir.|  
|<xref:System.Runtime.InteropServices.InterfaceTypeAttribute>|Yönetilen arabirimi COM istemcileri (ikili, IUnknown türetilmiş veya yalnızca IDispatch) nasıl kullanıma sunulan denetler.<br /><br /> COM birlikte çalışma araçları, bu öznitelik uygulayabilirsiniz.|  
|<xref:System.Runtime.InteropServices.LCIDConversionAttribute>|Bir yönetilmeyen yöntemi imzası bir LCID parametresi beklediğini belirtir.<br /><br /> COM birlikte çalışma araçları, bu öznitelik uygulayabilirsiniz.|  
|<xref:System.Runtime.InteropServices.MarshalAsAttribute>|Veri alanları ya da parametreleri yönetilen ve yönetilmeyen kod arasında nasıl sıralanması gerektiğini gösterir. Varsayılan hazırlama davranışı her veri türüne sahip olduğundan öznitelik her zaman isteğe bağlıdır.<br /><br /> COM birlikte çalışma araçları, bu öznitelik uygulayabilirsiniz.|  
|<xref:System.Runtime.InteropServices.OptionalAttribute>|Parametre isteğe bağlı olduğunu gösterir.<br /><br /> COM birlikte çalışma araçları, bu öznitelik uygulayabilirsiniz.|  
|<xref:System.Runtime.InteropServices.OutAttribute>|Bir alan veya parametre verileri çağrılan bir nesneden geri çağırıcısına sıralanması gerekir olduğunu gösterir.|  
|<xref:System.Runtime.InteropServices.PreserveSigAttribute>|HRESULT veya retval imza dönüşümü bastırır normalde birlikte çalışabilirlik çağrılar sırasında gerçekleşir olduğunu. Tür kitaplığını dışarı aktarma yanı sıra hazırlama öznitelik etkiler.<br /><br /> COM birlikte çalışma araçları, bu öznitelik uygulayabilirsiniz.|  
|<xref:System.Runtime.InteropServices.ProgIdAttribute>|.NET Framework sınıf ProgID belirtir. Öznitelik sınıfları için kullanılabilir.|  
|<xref:System.Runtime.InteropServices.StructLayoutAttribute>|Bir sınıfın alanlarının fiziksel düzenini denetler.<br /><br /> COM birlikte çalışma araçları, bu öznitelik uygulayabilirsiniz.|  
  
## <a name="conversion-tool-attributes"></a>Dönüştürme aracı öznitelikleri  
 Aşağıdaki tabloda, COM birlikte çalışma araçları dönüştürme işlemi sırasında uygulanan öznitelikleri açıklanmaktadır. Tasarım zamanında özniteliklerden geçerli değil.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|<xref:System.Runtime.InteropServices.ComAliasNameAttribute>|Bir parametre veya alan türü için COM diğer adı gösterir. Yapabilir alanları, öznitelik parametreleri kullanılması veya dönüş değerleri.|  
|<xref:System.Runtime.InteropServices.ComConversionLossAttribute>|Bu bir tür kitaplığından derleme içeri aktarılırken bir sınıf veya arabirim hakkında bilgi kesildi gösterir.|  
|<xref:System.Runtime.InteropServices.ComEventInterfaceAttribute>|Kaynak arabirimi ve olay arabiriminin yöntemlerini uygulayan sınıf tanımlar.|  
|<xref:System.Runtime.InteropServices.ImportedFromTypeLibAttribute>|Derleme ilk olarak bir COM tür kitaplığından içeri aktarıldı gösterir. Bu öznitelik asıl tür kitaplığı tür kitaplığı tanımını içerir.|  
|<xref:System.Runtime.InteropServices.TypeLibFuncAttribute>|İçeren **FUNCFLAGS** , ilk olarak aktarılmadı COM tür kitaplığından bu işlev için.|  
|<xref:System.Runtime.InteropServices.TypeLibTypeAttribute>|İçeren **TYPEFLAGS** , ilk olarak aktarılmadı COM tür kitaplığından bu tür.|  
|<xref:System.Runtime.InteropServices.TypeLibVarAttribute>|İçeren **VARFLAGS** , ilk olarak aktarılmadı bu değişkeni COM tür kitaplığı.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.InteropServices>  
 [.NET Framework Bileşenlerini COM'da Gösterme](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [Öznitelikler](../../../docs/standard/attributes/index.md)  
 [Birlikte Çalışma için .NET Türlerini Niteleme](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md)  
 [COM için Bütünleştirilmiş Kod Paketleme](../../../docs/framework/interop/packaging-an-assembly-for-com.md)
