---
title: Etkinlik Tanımı Kapsamı ve Görünürlüğü
ms.date: 03/30/2017
ms.assetid: ccdffa07-9503-4eea-a61b-17f1564368b7
ms.openlocfilehash: c7f656fee4960a8c43ac58abafba400ed9b35bc1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96289171"
---
# <a name="activity-definition-scoping-and-visibility"></a>Etkinlik Tanımı Kapsamı ve Görünürlüğü

Bir nesnenin kapsamı ve görünürlüğü gibi etkinlik tanımı kapsamı ve görünürlüğü, diğer nesne veya etkinliklerin etkinliğin üyelerine erişmesine olanak sağlar. Etkinlik tanımı aşağıdaki uygulamalar tarafından gerçekleştirilir:  
  
1. Üyeler ( <xref:System.Activities.Argument> , <xref:System.Activities.Variable> , ve <xref:System.Activities.ActivityDelegate> nesneler ve alt etkinlikler), bir etkinliğin kullanıcılarına göre belirlenir.  
  
2. Etkinliğin yürütme mantığını uygulama  
  
 Uygulama, etkinliğin tüketicilerine gösterilmeyen ve uygulamanın ayrıntıları olan üyeleri içerebilir.  Tür tanımına benzer şekilde, etkinlik modeli, bir yazarın tanımlanmakta olan etkinliğin tanımıyla ilgili olarak bir etkinlik üyesinin görünürlüğünü niteliğini sağlamasına izin verir.  Bu görünürlük, veri kapsamı gibi üye kullanımının yönlerini yönetir.  
  
## <a name="scope"></a>Kapsam  

 Veri kapsama ek olarak, etkinlik modeli görünürlüğü, etkinliğin doğrulama, hata ayıklama, izleme veya izleme gibi diğer yönlerine erişimi kısıtlayabilir. Yürütme özellikleri, yürütme özelliklerini belirli bir tanım kapsamına kısıtlayan görünürlük ve kapsamları kullanır. İkincil kökler, bir ile yakalanan durumu, <xref:System.Activities.Statements.CompensableActivity> compensable etkinliklerinin kullanıldığı tanım kapsamına kısıtlamak için görünürlük ve kapsam kullanır.  
  
## <a name="definition-and-usage"></a>Tanım ve kullanım  

 Bir iş akışı, temel etkinlik sınıflarından devralarak ve [yerleşik etkinlik kitaplığındaki](net-framework-4-5-built-in-activity-library.md)Etkinlikler kullanılarak yazılır. Etkinlik kullanmak için, etkinlik yazarının tanımının her bir bileşeninin görünürlüğünü yapılandırması gerekir.  
  
### <a name="activity-members"></a>Etkinlik üyeleri  

 Etkinlik modeli, etkinliğin tüketiciler tarafından kullanılabilmesini sağlayan bağımsız değişkenleri, değişkenleri, temsilcileri ve alt etkinlikleri tanımlar. Bu üyelerin her biri, veya olarak bildirilemez `public` `private` . Ortak Üyeler etkinliğin tüketicisi tarafından yapılandırılır, ancak `private` Üyeler etkinliğin yazarı tarafından düzeltilen bir uygulama kullanır. Veri kapsamı için görünürlük kuralları aşağıdaki gibidir:  
  
1. Ortak üyeler ve ortak alt etkinliklerin genel üyeleri ortak değişkenlere başvurabilir.  
  
2. Özel Üyeler ve ortak alt etkinliklerin genel üyeleri bağımsız değişkenlere ve özel değişkenlere başvurabilir.  
  
 Bir etkinliğin tüketicisi tarafından ayarlanmayacak bir üye asla özel hale getirilmemelidir.  
  
### <a name="authoring-models"></a>Yazma modelleri  

 Özel Etkinlikler,, veya kullanılarak <xref:System.Activities.NativeActivity> tanımlanır <xref:System.Activities.Activity> <xref:System.Activities.CodeActivity> <xref:System.Activities.AsyncCodeActivity> . Bu sınıflardan türeten etkinlikler farklı görünürlüklerle farklı üye türleri kullanıma sunabilir.  
  
#### <a name="nativeactivity"></a>NativeActivity  

 Öğesinden türetilen etkinliklerin <xref:System.Activities.NativeActivity> , zorunlu kodda yazılmış davranışları vardır ve isteğe bağlı olarak, mevcut Etkinlikler kullanılarak tanımlanabilir. ' Den etkinliklerin türetme <xref:System.Activities.NativeActivity> , çalışma zamanının sunduğu tüm özelliklere erişim verir. Böyle bir etkinliğin herhangi bir üyesi, yalnızca olarak bildirilebilecek bağımsız değişkenler hariç ortak veya özel görünürlük kullanılarak tanımlanabilir `public` .  
  
 Sınıfından türetilmiş sınıfların üyeleri, <xref:System.Activities.NativeActivity> metoduna geçirilen struct kullanılarak çalışma zamanına göre bildirilmiştir <xref:System.Activities.NativeActivityMetadata> <xref:System.Activities.NativeActivity.CacheMetadata%2A> .  
  
#### <a name="activity"></a>Etkinlik  

 Kullanılarak oluşturulan etkinliklerin <xref:System.Activities.Activity> , diğer etkinlikleri oluşturarak kesinlikle tasarlanan davranışı vardır. <xref:System.Activities.Activity>Sınıfında, kullanılarak çalışma zamanı tarafından edinilen bir uygulama alt etkinliği vardır <xref:System.Activities.Activity.Implementation%2A> . Öğesinden türetilen bir etkinlik <xref:System.Activities.Activity> genel bağımsız değişkenler, genel değişkenler, içeri aktarılan ActivityDelegates ve içeri aktarılan etkinlikleri tanımlayabilir.  
  
 İçeri aktarılan ActivityDelegates ve Etkinlikler etkinliğin ortak alt öğeleri olarak bildirilmiştir, ancak etkinlik tarafından doğrudan zamanlanamaz. Bu bilgiler, etkinliğin hiçbir zaman yürütülebileceği konumlarda üst öğeye yönelik doğrulamaları çalıştırmayı önlemek için doğrulama sırasında kullanılır. Ayrıca, genel alt öğelere benzer şekilde içeri aktarılan alt öğeler, etkinliğin uygulamasına başvuruda bulunabilir ve zamanlanabilir. Bu, Activity1 adlı bir etkinliği içeri aktaran bir etkinliğin <xref:System.Activities.Statements.Sequence> , Activity1 zamanlaması olan uygulamasında bir içerdiği bir etkinlik olduğu anlamına gelir.  
  
#### <a name="codeactivity-asynccodeactivity"></a>CodeActivity/AsyncCodeActivity  

 Bu temel sınıf, kesinlik temelli kodda yazma davranışı için kullanılır. Bu sınıftan türetilmiş etkinliklerin yalnızca sergiledikleri bağımsız değişkenlere erişimi vardır. Bu, yalnızca bu etkinliklerin sergileyebileceği üyelerin ortak bağımsız değişkenlerle olduğu anlamına gelir. Bu etkinlikler için başka üye veya görünürlükleri uygulanmaz.  
  
#### <a name="summary-of-visibilities"></a>Görünürlüklıkların Özeti  

 Aşağıdaki tabloda, bu bölümde daha önce yer aldığı bilgiler özetlenmektedir.  
  
|Üye Türü|NativeActivity|Etkinlik|CodeActivity/AsyncCodeActivity|  
|-----------------|--------------------|--------------|--------------------------------------|  
|Arguments|Ortak/özel|Genel|uygulanamaz|  
|Değişkenler|Ortak/özel|Genel|uygulanamaz|  
|Alt etkinlikler|Ortak/özel|Ortak, bir sabit özel alt öğesi uygulamada tanımlandı.|uygulanamaz|  
|ActivityDelegates|Ortak/özel|Genel|uygulanamaz|  
  
 Genel olarak, bir etkinliğin tüketicisi tarafından ayarlanmayan bir üye genel hale getirilmemelidir.  
  
### <a name="execution-properties"></a>Yürütme Özellikleri  

 Bazı senaryolarda, belirli bir yürütme özelliğinin bir etkinliğin genel alt öğelerine kapsamını atamak yararlı olur. <xref:System.Activities.ExecutionProperties>Koleksiyon bu özelliği <xref:System.Activities.ExecutionProperties.Add%2A> yöntemiyle sağlar. Bu yöntem, belirli bir özelliğin tüm alt öğeler için mi yoksa yalnızca herkese açık olup olmadığını gösteren bir Boole parametresine sahiptir. Bu parametre olarak ayarlandıysa `true` , özelliği yalnızca ortak üyelere ve genel alt öğelerinin genel üyelerine görünür olur.  
  
### <a name="secondary-roots"></a>İkincil kökler  

 İkincil kök, çalışma zamanının, maaş etkinliklerinin durumunu yönetmeye yönelik iç mekanizmasıdır. Bir <xref:System.Activities.Statements.CompensableActivity> çalışmayı tamamladığında, durumu hemen temizlenmez. Bunun yerine, durum, Dengeleme bölümü tamamlanana kadar ikincil kökündeki çalışma zamanı tarafından korunur. İkincil kökle yakalanan konum ortamları, compensable etkinliğinin kullanıldığı tanım kapsamına karşılık gelir.
