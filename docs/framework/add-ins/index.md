---
title: Eklentiler ve Genişletilebilirlik
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- extensibility [.NET Framework], add-ins
- add-ins [.NET Framework]
- add-ins [.NET Framework], about
- hosts [.NET Framework], compared to add-ins
- .NET Framework, add-ins
- add-in pipeline [.NET Framework], about
- add-ins [.NET Framework], compared to hosts
- .NET Framework, extensibility
- versioning [.NET Framework], add-ins
ms.assetid: 8dd45b02-7218-40f9-857d-40d7b98b850b
caps.latest.revision: 42
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4d288d321063512f91ad94b417bb1a6bf38c9ef9
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2018
---
# <a name="add-ins-and-extensibility"></a>Eklentiler ve Genişletilebilirlik
<a name="top"></a>Eklentiler genişletilmiş özellikler veya bir ana bilgisayar uygulaması için hizmetleri sağlar. [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Geliştiriciler eklentiler geliştirmek ve bunları kendi ana bilgisayar uygulamasında etkinleştirmek için kullanabileceğiniz bir programlama modelidir. Model bu konak ve eklenti arasındaki iletişim ardışık düzeni oluşturarak elde eder. Model türler kullanılarak uygulanır <xref:System.AddIn>, <xref:System.AddIn.Hosting>, <xref:System.AddIn.Pipeline>, ve <xref:System.AddIn.Contract> ad alanları.  
  
 Bu genel bakışta aşağıdaki bölümleri içerir:  
  
-   [Eklenti modeli](#addin_model)  
  
-   [Eklentiler ve ana bilgisayarlar arasında ayrım](#distinguishing_between_addins_and_hosts)  
  
-   [İlgili Konular](#related_topics)  
  
-   [Başvuru](#reference)  
  
> [!NOTE]
>  Konumundaki yapı ardışık'ın eklenti ek örnek kod ve müşteri teknolojisi önizlemeleri araçların bulabilirsiniz [CodePlex üzerinde Yönetilen Genişletilebilirlik ve eklenti Framework site](http://go.microsoft.com/fwlink/?LinkId=121190).  
  
<a name="addin_model"></a>   
## <a name="add-in-model"></a>Eklenti modeli  
 Eklenti ve ana bilgisayar arasındaki tüm iletişimi sorumlu olan eklenti ardışık düzeni (iletişim ardışık olarak da bilinir) oluşturan kesimleri bir dizi eklenti modeli oluşur. Ardışık düzen, eklenti ve ana bilgisayar arasında veri değişimi kesimleri simetrik iletişimi modelidir. Bu kesimler konak ile eklenti geliştirme sürüm desteği gerekli Soyutlama Katmanı ve eklentisinin yalıtım sağlar.  
  
 Aşağıdaki çizimde, ardışık düzen gösterir.  
  
 ![Ekleme &#45; ardışık düzen modeli. ] (../../../docs/framework/add-ins/media/addin1.png "AddIn1")  
Eklenti ardışık düzeni  
  
 Bu kesimler derlemelerde aynı uygulama etki alanında olması gerekli değildir. Kendi yeni uygulama etki alanına, var olan bir uygulama etki alanına veya ana bilgisayarın uygulama etki alanına bile bir eklenti yükleyebilirsiniz. Kaynakları ve güvenlik kapsamları paylaşmak eklentileri sağlayan aynı uygulama etki alanına, birden çok eklentileri yükleyebilir.  
  
 Eklenti modelini destekler ve önerir, konak ve yalıtım sınırı (remoting sınır olarak da bilinir) olarak adlandırılan eklentiyi arasında isteğe bağlı bir sınır. Bu sınır, bir uygulama etki alanı ya da işlem sınırı olabilir.  
  
 Ardışık Düzen ortasında sözleşme segment ana bilgisayarın uygulama etki alanı ve eklentinin uygulama etki alanı yüklenir. Sanal yöntemler sözleşmesini tanımlayan, konak ve birbirleriyle türleri exchange eklentisini kullanın.  
  
 Yalıtım sınırı iletilecek türleri sözleşmeleri veya seri hale getirilebilir türler olmalıdır. Sözleşmeleri olmayan türler veya seri hale getirilebilir türler sözleşmelerine ardışık bağdaştırıcısı segmentlerinde dönüştürülmelidir.  
  
 Ardışık Düzen görünümü parçalarını soyut taban sınıfları veya ana bilgisayar ve eklenti anlaşma tarafından tanımlanan paylaştıkları, yöntemleri bir görünümünü sağlayan arabirimleri markalarıdır.  
  
 Geliştirme hakkında daha fazla bilgi için kanal kesimleri, bkz: [ardışık düzen geliştirme](../../../docs/framework/add-ins/pipeline-development.md).  
  
 Aşağıdaki bölümlerde eklenti modeli özelliklerini açıklar.  
  
### <a name="independent-versioning"></a>Bağımsız sürüm oluşturma  
 Eklenti modeli, konakları ve sürüme eklentileri bağımsız olarak olanak sağlar. Sonuç olarak, eklenti modeli aşağıdaki senaryolara olanak sağlar:  
  
-   Bir bağdaştırıcı oluşturma ana bilgisayarı, önceki bir sürümü için yerleşik bir eklenti kullanmak bir konak sağlar.  
  
-   Bir bağdaştırıcı oluşturma konak daha sonraki bir sürümü için yerleşik bir eklenti kullanmak bir konak sağlar.  
  
-   Eklentiler kullanmak bir konak sağlayan bir bağdaştırıcısı oluşturmak için farklı bir konak yerleşiktir.  
  
### <a name="discovery-and-activation"></a>Bulma ve etkinleştirme  
 Bir eklenti, bir bilgi deposundan bulunan eklentileri temsil eden bir koleksiyon uygulamasından bir belirteç kullanarak etkinleştirebilirsiniz. Eklentiler Eklenti ana bilgisayarın görünümü tanımlayan tür için arama yaparak bulunamadı. Bir özel eklenti tarafından eklenti tanımlayan tür bulabilirsiniz. Bilgi deposunu iki önbellek dosyaları içerir: ardışık düzen mağazaya ve eklenti.  
  
 Güncelleştirme ve bilgi deposunu yeniden oluşturma hakkında daha fazla bilgi için bkz: [eklenti bulma](http://msdn.microsoft.com/library/5d268dde-11df-4c4d-a022-f58d88bbc421). Eklentiler etkinleştirme hakkında daha fazla bilgi için bkz: [eklentisini etkinleştirme](http://msdn.microsoft.com/library/bedcbcdf-5964-4215-b5f3-3299798b2b3f) ve [nasıl yapılır: farklı yalıtım ve güvenlik ile eklentileri etkinleştirmek](http://msdn.microsoft.com/library/7afe7ec8-5158-4350-9119-5df0ecab8aa5).  
  
### <a name="isolation-levels-and-external-processes"></a>Yalıtım düzeylerinde ve dış işlemleri  
 Eklenti modeli birkaç eklentileri veya ek bileşeni ve ana bilgisayar arasında yalıtım düzeyini destekler. Az yalıtılmış başlayarak, bu düzeylerin aşağıdaki gibidir:  
  
-   Eklenti aynı uygulama etki alanı konağı olarak çalışır. Farklı uygulama etki alanları kullandığınızda aldığınız kaldırma yetenekleri ve yalıtım kaybetmek çünkü bu önerilmez.  
  
-   Birden çok eklentiler, ana bilgisayar tarafından kullanılan uygulama etki alanından farklı aynı uygulama etki alanına yüklenir.  
  
-   Her eklenti yalnızca kendi uygulama etki alanına yüklenir. En yaygın yalıtım düzeyini budur.  
  
-   Birden çok eklentiler bir dış işlem aynı uygulama etki alanına yüklenir.  
  
-   Her eklenti özel olarak bir dış işlem kendi uygulama etki alanına yüklenir. Bu en yalıtılmış bir senaryodur.  
  
 Dış işlemlere kullanma hakkında daha fazla bilgi için bkz: [nasıl yapılır: farklı yalıtım ve güvenlik ile eklentileri etkinleştirme](http://msdn.microsoft.com/library/7afe7ec8-5158-4350-9119-5df0ecab8aa5).  
  
### <a name="lifetime-management"></a>Ömür Yönetimi  
 Uygulama etki alanı ve işlem sınırları eklenti modeli yayılan olduğundan atık toplama kendisi tarafından serbest bırakır ve nesneleri geri kazanmak için yeterli değil. Eklenti modeli belirteçleri ve başvuru sayımı kullanır bir yaşam süresi management mekanizma sağlar ve genellikle ek programlama gerektirmez. Daha fazla bilgi için bkz: [yaşam süresi Management](http://msdn.microsoft.com/library/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).  
  
 [Başa dön](#top)  
  
<a name="distinguishing_between_addins_and_hosts"></a>   
## <a name="distinguishing-between-add-ins-and-hosts"></a>Eklentiler ve ana bilgisayarlar arasında ayrım  
 Bir eklenti ve bir ana bilgisayar arasındaki farkı yalnızca ana bilgisayarın bir eklenti etkinleştiren olmasıdır. Konak bir sözcük işleme uygulama ve onun yazım denetleyicileri gibi iki daha büyük olabilir; veya konağın bir medya oynatıcı katıştırır bir anlık ileti sistemi istemcisi gibi iki daha küçük olabilir. Eklenti modeli eklentileri hem istemci hem de sunucu senaryolarda destekler. Posta sunucusu virüs taraması, istenmeyen posta filtreleri ve IP koruması sağlama eklentiler sunucu eklentileri örneklerindendir. İstemci eklenti örnekleri başvuru eklentiler için sözcük işlemci, grafik programları ve oyunları ve virüs yerel e-posta istemcileri için tarama için özel özellikler içerir.  
  
 [Başa dön](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[İşlem Hattı Geliştirme](../../../docs/framework/add-ins/pipeline-development.md)|Eklenti konak uygulamaya bölümlerinin iletişim kanalı açıklar. Kod örnekleri ardışık düzenini oluşturmak ve ardışık düzeninde kesimleri dağıtmak anlatan izlenecek konularda sağlar [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].|  
|[Uygulama Etki Alanları ve Derlemeler](http://msdn.microsoft.com/library/433b04ae-4ba8-4849-9dbd-79194f240346)|Güvenlik, güvenilirlik ve sürüm oluşturma için bir yalıtım sınırı sağlayan uygulama etki alanları ve derlemeler arasındaki ilişkiyi açıklar.|  
  
 [Başa dön](#top)  
  
<a name="reference"></a>   
## <a name="reference"></a>Başvuru  
 <xref:System.AddIn?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Contract?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Hosting?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Pipeline?displayProperty=nameWithType>  
  
 [Başa dön](#top)