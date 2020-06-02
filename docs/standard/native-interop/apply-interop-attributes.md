---
title: Birlikte Çalışma Özniteliklerini Uygulama
description: Bu makale, System. Runtime. InteropServices ad alanının tasarım zamanı ve dönüştürme aracı öznitelikleri dahil COM birlikte çalışma özniteliklerini özetler.
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
ms.openlocfilehash: f9ccf59e52c1ef27649cd70a57f7b24bb5a8e9bf
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291337"
---
# <a name="applying-interop-attributes"></a>Birlikte Çalışma Özniteliklerini Uygulama
<xref:System.Runtime.InteropServices>Ad alanı, birlikte çalışabilirlik 'e özgü özniteliklerin üç kategorisini sağlar: tasarım zamanında sizin tarafınızdan, dönüştürme işlemi SıRASıNDA com birlikte çalışma araçları ve API 'leri tarafından uygulanan ve sizin tarafınızdan ya da com birlikte çalışma tarafından uygulanan bunlar.  
  
 Yönetilen koda öznitelik uygulama görevi hakkında bilginiz yoksa, bkz. [öznitelikleri kullanarak meta verileri genişletme](../attributes/index.md). Diğer özel öznitelikler gibi türler, Yöntemler, özellikler, parametreler, alanlar ve diğer üyelere birlikte çalışma için özel öznitelikler de uygulayabilirsiniz.  
  
## <a name="design-time-attributes"></a>Tasarım zamanı öznitelikleri  
 Tasarım zamanı özniteliklerini kullanarak, COM birlikte çalışma araçları ve API 'Leri tarafından gerçekleştirilen dönüştürme sürecinin sonucunu ayarlayabilirsiniz. Aşağıdaki tabloda, yönetilen kaynak kodunuza uygulayabileceğiniz öznitelikler açıklanmaktadır. COM birlikte çalışma araçları, bazen bu tabloda açıklanan öznitelikleri de uygulayabilir.  
  
|Öznitelik|Description|  
|---------------|-----------------|  
|<xref:System.Runtime.InteropServices.AutomationProxyAttribute>|Türün Otomasyon sıralayıcısı veya özel bir ara sunucu ve saplama kullanılarak sıralanması gerekip gerekmediğini belirtir.|  
|<xref:System.Runtime.InteropServices.ClassInterfaceAttribute>|Bir sınıf için oluşturulan arabirimin türünü denetler.|  
|<xref:System.Runtime.InteropServices.CoClassAttribute>|Bir tür kitaplığından içeri aktarılan özgün coclass 'ın CLSID değerini tanımlar.<br /><br /> COM birlikte çalışma araçları genellikle bu özniteliği uygular.|  
|<xref:System.Runtime.InteropServices.ComImportAttribute>|Bir coclass veya arabirim tanımının bir COM tür kitaplığından içeri aktarıldığını belirtir. Çalışma zamanı, türü etkinleştirme ve sıralama yöntemini öğrenmek için bu bayrağı kullanır. Bu öznitelik, türün bir tür kitaplığına geri verilmesini yasaklar.<br /><br /> COM birlikte çalışma araçları genellikle bu özniteliği uygular.|  
|<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>|Derleme COM 'dan kullanılmak üzere kaydedildiğinde bir yöntemin çağrılması gerektiğini gösterir. böylece, kayıt işlemi sırasında Kullanıcı tarafından yazılan kodun yürütülmesi gerekir.|  
|<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>|Sınıf için olay kaynakları olan arabirimleri tanımlar.<br /><br /> COM birlikte çalışabilirlik araçları, bu özniteliği uygulayabilir.|  
|<xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>|Derleme COM 'tan kaydolmasından sonra, Kullanıcı tarafından yazılan kodun işlem sırasında yürütülebilmesi için bir yöntemin çağrılması gerektiğini gösterir.|  
|<xref:System.Runtime.InteropServices.ComVisibleAttribute>|Öznitelik değeri **false**değerine eşitse, türleri com olarak görünmez hale gelir. Bu öznitelik, COM görünürlüğünü denetlemek için tek bir türe veya bir derlemenin tamamına uygulanabilir. Varsayılan olarak, tüm yönetilen, genel türler görünür; özniteliğin görünür olması için gerekli değildir.|  
|<xref:System.Runtime.InteropServices.DispIdAttribute>|Bir yöntemin veya alanın COM dağıtım tanımlayıcısını (DISPID) belirtir. Bu öznitelik, açıkladığı yöntemin, alanın veya özelliğin DISPID 'sini içerir.<br /><br /> COM birlikte çalışabilirlik araçları, bu özniteliği uygulayabilir.|
|<xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute>|.NET ' te uygulanan bir COM sınıfının varsayılan arabirimini gösterir.<br /><br /> COM birlikte çalışabilirlik araçları, bu özniteliği uygulayabilir.|
|<xref:System.Runtime.InteropServices.FieldOffsetAttribute>|**StructLayoutAttribute**ile kullanıldığında bir sınıfın içindeki her alanın fiziksel konumunu gösterir ve **LayoutKind** açık olarak ayarlanır.|  
|<xref:System.Runtime.InteropServices.GuidAttribute>|Bir sınıfın, arabirimin veya bütün bir tür kitaplığının genel benzersiz tanımlayıcısını (GUID) belirtir. Özniteliğe geçirilen dize, **System. Guid**türü için kabul edilebilir bir Oluşturucu bağımsız değişkeni olan bir biçim olmalıdır.<br /><br /> COM birlikte çalışabilirlik araçları, bu özniteliği uygulayabilir.|  
|<xref:System.Runtime.InteropServices.IDispatchImplAttribute>|Ortak dil çalışma zamanının, COM 'a yönelik ikili arabirimler ve dispınterfaces kullanılırken hangi **IDispatch** arabirimi uygulamasının kullandığını gösterir.|  
|<xref:System.Runtime.InteropServices.InAttribute>|Verilerin arayana sıralanması gerektiğini gösterir. Öznitelik parametrelerine kullanılabilir.|  
|<xref:System.Runtime.InteropServices.InterfaceTypeAttribute>|Yönetilen bir arabirimin COM istemcilerine nasıl sunulduğunu denetler (yalnızca çift, IUnknown ile türetilmiş veya IDispatch).<br /><br /> COM birlikte çalışabilirlik araçları, bu özniteliği uygulayabilir.|  
|<xref:System.Runtime.InteropServices.LCIDConversionAttribute>|Yönetilmeyen bir yöntem imzasının bir LCıD parametresi beklediğini belirtir.<br /><br /> COM birlikte çalışabilirlik araçları, bu özniteliği uygulayabilir.|  
|<xref:System.Runtime.InteropServices.MarshalAsAttribute>|Alanlardaki veya parametrelerdeki verilerin yönetilen ve yönetilmeyen kod arasında nasıl sıralanması gerektiğini gösterir. Her veri türünün varsayılan sıralama davranışına sahip olması nedeniyle öznitelik her zaman isteğe bağlıdır.<br /><br /> COM birlikte çalışabilirlik araçları, bu özniteliği uygulayabilir.|  
|<xref:System.Runtime.InteropServices.OptionalAttribute>|Parametrenin isteğe bağlı olduğunu gösterir.<br /><br /> COM birlikte çalışabilirlik araçları, bu özniteliği uygulayabilir.|  
|<xref:System.Runtime.InteropServices.OutAttribute>|Bir alan veya parametre içindeki verilerin, çağıran bir nesneden çağırana geri sıralanması gerektiğini gösterir.|  
|<xref:System.Runtime.InteropServices.PreserveSigAttribute>|Normalde birlikte çalışabilirlik çağrıları sırasında gerçekleşgeçen HRESULT veya retval imza dönüşümünü bastırır. Öznitelik, sıralama ve tür kitaplığı dışarı aktarma işlemlerini etkiler.<br /><br /> COM birlikte çalışabilirlik araçları, bu özniteliği uygulayabilir.|  
|<xref:System.Runtime.InteropServices.ProgIdAttribute>|Bir .NET Framework sınıfının ProgID 'sini belirtir. , Öznitelik sınıfları için kullanılabilir.|  
|<xref:System.Runtime.InteropServices.StructLayoutAttribute>|Bir sınıfın alanlarının fiziksel yerleşimini denetler.<br /><br /> COM birlikte çalışabilirlik araçları, bu özniteliği uygulayabilir.|  
  
## <a name="conversion-tool-attributes"></a>Dönüştürme-araç öznitelikleri  
 Aşağıdaki tabloda, dönüştürme işlemi sırasında COM birlikte çalışma araçlarının uygulandığı öznitelikler açıklanmaktadır. Bu öznitelikleri tasarım zamanında uygulamayın.  
  
|Öznitelik|Description|  
|---------------|-----------------|  
|<xref:System.Runtime.InteropServices.ComAliasNameAttribute>|Bir parametre veya alan türü için COM diğer adını gösterir. Parametreleri, alanları veya dönüş değerlerini öznitelik olarak kullanabilirsiniz.|  
|<xref:System.Runtime.InteropServices.ComConversionLossAttribute>|Bir sınıf veya arabirim ile ilgili bilgilerin bir tür kitaplığından derlemeye aktarıldığında kaybedildiğini gösterir.|  
|<xref:System.Runtime.InteropServices.ComEventInterfaceAttribute>|Kaynak arabirimini ve olay arabiriminin yöntemlerini uygulayan sınıfını tanımlar.|  
|<xref:System.Runtime.InteropServices.ImportedFromTypeLibAttribute>|Derlemenin başlangıçta bir COM tür kitaplığından alındığını gösterir. Bu öznitelik, özgün tür kitaplığının tür kitaplığı tanımını içerir.|  
|<xref:System.Runtime.InteropServices.TypeLibFuncAttribute>|Bu işlev için ilk olarak COM tür kitaplığından içeri aktarılan işlev **bayraklarını** içerir.|  
|<xref:System.Runtime.InteropServices.TypeLibTypeAttribute>|Bu tür için ilk olarak COM tür kitaplığından içeri aktarılan **TYPEFLAGS** içerir.|  
|<xref:System.Runtime.InteropServices.TypeLibVarAttribute>|Bu değişken için başlangıçta içeri aktarılmış olan **VARFLAGS** com tür kitaplığından içerir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices>
- [.NET Framework Bileşenlerini COM'da Gösterme](../../framework/interop/exposing-dotnet-components-to-com.md)
- [Öznitelikler](../attributes/index.md)
- [Birlikte Çalışma için Niteleyici .NET Türleri](qualify-net-types-for-interoperation.md)
- [COM için bir .NET Framework derlemesi paketleme](../../framework/interop/packaging-an-assembly-for-com.md)
