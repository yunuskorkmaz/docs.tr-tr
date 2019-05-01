---
title: Etkinlik Tanımı Kapsamı ve Görünürlüğü
ms.date: 03/30/2017
ms.assetid: ccdffa07-9503-4eea-a61b-17f1564368b7
ms.openlocfilehash: 27c43323a176c841f3d90cb9c52f25599bc0686d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945957"
---
# <a name="activity-definition-scoping-and-visibility"></a>Etkinlik Tanımı Kapsamı ve Görünürlüğü
Etkinlik tanımı kapsamı ve kapsamını belirleme gibi görünürlük ve bir nesnenin görünürlüğü olan etkinliğin üyelere erişim için diğer nesneleri ve etkinlikleri. Etkinlik tanımı aşağıdaki uygulamaları tarafından gerçekleştirilir:  
  
1. Üyeleri belirleyen (<xref:System.Activities.Argument>, <xref:System.Activities.Variable>, ve <xref:System.Activities.ActivityDelegate> nesneleri ve alt etkinlikler), kullanıcılara bir etkinlik sunar.  
  
2. Etkinlik yürütme mantığını uygulama  
  
 Uygulama, etkinliğin tüketicilere açık değildir ancak bunun yerine uygulamasının Ayrıntılar üyeler içerebilir.  Tür tanımına benzer, tanımlanan etkinlik tanımı ile ilgili bir etkinlik üye görünürlüğünü nitelemek Yazar etkinlik modeli sağlar.  Bu görünürlük üye kullanım, veri kapsamı gibi yönlerini yönetir.  
  
## <a name="scope"></a>Kapsam  
 Veri kapsamı ek olarak, etkinlik model görünürlük, etkinlik, doğrulama, hata ayıklama, izleme veya izleme gibi diğer yönleri için erişimi kısıtlayabilirsiniz. Görünürlük ve belirli bir kapsamda tanımının yürütme özellikleri kısıtlamak için kapsam yürütme özelliklerini kullanın. Tarafından yakalanan durum sınırlamak için ikincil kökleri kullanmak görünürlük ve kapsamını belirleme bir <xref:System.Activities.Statements.CompensableActivity> kapsamına tanım compensable etkinlikleri kullanılır.  
  
## <a name="definition-and-usage"></a>Tanımı ve kullanımı  
 Bir iş akışı temel etkinliği sınıflardan devralmaya ve etkinliklerini kullanarak yeni etkinlikleri yazma yazılır [yerleşik etkinlik Kitaplığı](net-framework-4-5-built-in-activity-library.md). Bir etkinliği kullanmak için etkinlik Yazar tanımı'nın her bileşeninin görünürlüğünü yapılandırmanız gerekir.  
  
### <a name="activity-members"></a>Etkinlik üyeleri  
 Etkinlik modeli bağımsız değişkenler, değişkenleri, temsilciler ve etkinlik tüketicilere kullanılabilmesini çocuk etkinliklerinin tanımlar. Her biri bu üyeleri olarak bildirilebilir `public` veya `private`. Genel üyeler, etkinlik tüketici tarafından yapılandırılır, ancak `private` üyeleri etkinlik yazarı tarafından sabit bir uygulama kullanın. Veri kapsamı için görünürlük kuralları aşağıdaki gibidir:  
  
1. Genel değişkenleri ortak üyeleri ve ortak bir alt etkinlik ortak üyeleri başvurabilirsiniz.  
  
2. Özel üyeler ve ortak bir alt etkinlik ortak üyeleri bağımsız değişkenler ve özel değişkenlere başvurabilir.  
  
 Bir etkinliğin tüketici tarafından ayarlanabilir üyesi hiçbir zaman özel yapılmalıdır.  
  
### <a name="authoring-models"></a>Model geliştirme  
 Özel etkinlikler kullanılarak tanımlanmış <xref:System.Activities.NativeActivity>, <xref:System.Activities.Activity>, <xref:System.Activities.CodeActivity>, veya <xref:System.Activities.AsyncCodeActivity>. Bu sınıflarından etkinlikler farklı görünürlüğe sahip farklı bir üye türleri açığa çıkarabilir.  
  
#### <a name="nativeactivity"></a>NativeActivity  
 Öğesinden türetilen etkinlikleri <xref:System.Activities.NativeActivity> kesinlik temelli kod olarak yazılmış ve isteğe bağlı olarak var olan etkinlikleri kullanılarak tanımlanabilir davranışa sahiptir. Etkinlikler türetme <xref:System.Activities.NativeActivity> çalışma zamanı tarafından kullanıma sunulan tüm özelliklere erişim verir. Böyle bir etkinlik herhangi bir üyesi olarak yalnızca bildirilebilir bağımsız değişkenler hariç, genel veya özel görünürlük kullanılarak tanımlanabilir `public`.  
  
 Sınıfından türetilen sınıfların üyeleri <xref:System.Activities.NativeActivity> kullanarak çalışma zamanı bildirilen <xref:System.Activities.NativeActivityMetadata> yapısı geçirilen <xref:System.Activities.NativeActivity.CacheMetadata%2A> yöntemi.  
  
#### <a name="activity"></a>Etkinlik  
 Kullanılarak oluşturulan etkinlikleri <xref:System.Activities.Activity> diğer etkinlikleri oluşturma aracılığıyla kesinlikle tasarlanmıştır davranışa sahiptir. <xref:System.Activities.Activity> Sınıfında çalışma zamanını kullanarak elde edilen, bir uygulama alt etkinlik <xref:System.Activities.Activity.Implementation%2A>. Türetilen bir etkinlik <xref:System.Activities.Activity> genel bağımsız değişkenler, genel değişkenler, içeri aktarılan ActivityDelegates ve içeri aktarılan etkinlikleri tanımlayabilirsiniz.  
  
 İçeri aktarılan ActivityDelegates ve etkinlikler etkinliğin Genel alt öğesi olarak bildirilir ancak etkinlik tarafından doğrudan zamanlanamaz. Bu bilgileri, etkinlik hiçbir zaman burada yürütecek konumlarda üst taraftaki doğrulamaları çalıştırmaktan kaçınmak için doğrulama sırasında kullanılır. Aynı zamanda, olduğu gibi ortak öğeleri için içeri aktarılan öğeleri için başvurulan ve etkinliğin uygulama tarafından zamanlandı. Yani Activity1 adlı bir etkinliği alır bir etkinlik içerebilir bir <xref:System.Activities.Statements.Sequence> kendi uygulamasında Activity1 zamanlar.  
  
#### <a name="codeactivity-asynccodeactivity"></a>CodeActivity / AsyncCodeActivity  
 Bu temel sınıf davranışı kesinlik temelli kod yazmak için kullanılır. Bu sınıftan türetilen etkinlikleri ortaya bağımsız değişkenler yalnızca erişebilir. Bu, bu etkinlikleri açığa çıkarabilir üyeler yalnızca genel bağımsız değişkenleri olduğunu gösterir. Diğer üyeleri veya görünürlüğe bu etkinlikleri için geçerlidir.  
  
#### <a name="summary-of-visibilities"></a>Görünürlüklerini özeti  
 Aşağıdaki tabloda, bu bölümdeki bilgiler özetlenmektedir.  
  
|Üye Türü|NativeActivity|Etkinlik|CodeActivity / AsyncCodeActivity|  
|-----------------|--------------------|--------------|--------------------------------------|  
|Arguments|Genel / özel|Ortak|Uygulanamaz|  
|Değişkenler|Genel / özel|Ortak|Uygulanamaz|  
|Bağımlı etkinlikler|Genel / özel|Ortak bir uygulama içinde tanımlanan özel alt düzeltildi.|Uygulanamaz|  
|ActivityDelegates|Genel / özel|Ortak|Uygulanamaz|  
  
 Genel olarak, bir etkinlik tüketici tarafından ayarlanamaz üyesi ortak yapılmaması gerekir.  
  
### <a name="execution-properties"></a>Yürütme özellikleri  
 Bazı senaryolarda, aktivite ortak alt belirli yürütme özelliğine kapsamını belirlemek yararlıdır. <xref:System.Activities.ExecutionProperties> Koleksiyonu sağlar, bu özellik sayesinde <xref:System.Activities.ExecutionProperties.Add%2A> yöntemi. Tüm alt öğelerini, veya yalnızca ortak olan için kapsamı belirli bir özellik olup olmadığını belirten bir Boole parametresi bu yöntem vardır. Bu parametre ayarlanırsa `true`, özelliği yalnızca Genel üyeler ve Genel alt öğelerini ortak üyeleri için görünür olacak.  
  
### <a name="secondary-roots"></a>İkincil kökler  
 İkincil bir kök maaş etkinlikler için durumu yönetmek için çalışma zamanının iç mekanizmadır. Olduğunda bir <xref:System.Activities.Statements.CompensableActivity> bitirdi çalışıyorsa, durumu hemen temizlenmez. Bunun yerine, maaş bölüm tamamlanıncaya kadar durumu ikincil kök çalışma zamanı tarafından korunur. İkincil kök ile yakalanan konumu ortamları Compensable etkinliğinde kullanılan tanımı kapsamına karşılık gelir.
