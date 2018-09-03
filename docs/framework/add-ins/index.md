---
title: Eklentiler ve Genişletilebilirlik
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eb2485f2ecf0426360dba80d443500a92b5a7af6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43482229"
---
# <a name="add-ins-and-extensibility"></a>Eklentiler ve Genişletilebilirlik
<a name="top"></a> Genişletilmiş özellikler veya hizmetler bir Windows uygulaması için eklentiler sağlar. [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Geliştiriciler eklentileri geliştirmek ve bunları ana bilgisayar uygulamalarını etkinleştirmek için kullanabileceğiniz bir programlama modeli sağlar. Model bir ana bilgisayar ile eklenti arasındaki iletişim hattının oluşturularak elde eder. Model türleri kullanarak uygulanan <xref:System.AddIn>, <xref:System.AddIn.Hosting>, <xref:System.AddIn.Pipeline>, ve <xref:System.AddIn.Contract> ad alanları.  
  
 Bu genel bakış aşağıdaki bölümleri içerir:  
  
-   [Eklenti modeli](#addin_model)  
  
-   [Eklentiler ve konaklar arasında ayrım](#distinguishing_between_addins_and_hosts)  
  
-   [İlgili Konular](#related_topics)  
  
-   [Başvuru](#reference)  
  
> [!NOTE]
>  Yapı ardışık'ın eklenti ek örnek kodlar ve müşteri teknolojisi önizlemeler araçların bulabilirsiniz [CodePlex üzerinde Yönetilen Genişletilebilirlik ve eklenti Framework site](https://go.microsoft.com/fwlink/?LinkId=121190).  
  
<a name="addin_model"></a>   
## <a name="add-in-model"></a>Eklenti modeli  
 Bir dizi eklenti ile ana bilgisayar arasındaki tüm iletişim için sorumlu eklenti işlem hattı (iletişim kanalı olarak da bilinir) oluşturan parçaların eklenti modeli oluşur. İşlem hattı, bir eklenti ile bunun konağı arasında veri değişimi segmentleri simetrik iletişim modelidir. Konak ve eklenti arasındaki bu parçaları geliştirme, sürüm oluşturma desteği gerekli Soyutlama Katmanı ve eklentinin yalıtım sağlar.  
  
 Aşağıdaki resimde, işlem hattı gösterilmektedir.  
  
 ![Ekleme&#45;işlem hattı modelinde. ](../../../docs/framework/add-ins/media/addin1.png "AddIn1")  
Eklenti ardışık düzeni  
  
 Bu kesimler için derlemeleri, aynı uygulama etki alanında olması gerekli değildir. Bir eklenti kendi yeni bir uygulama etki alanına, var olan bir uygulama etki alanına veya ana bilgisayarın uygulama etki alanına da yükleyebilirsiniz. Kaynaklar ve güvenlik kapsamlarını paylaşmak add-INS sağlayan aynı uygulama etki alanına, birden çok eklentileri yükleyebilir.  
  
 Eklenti modeli destekler ve önerir, konak ve yalıtım sınırı (uzaktan iletişim sınırı olarak da bilinir) olarak adlandırılan eklentiyi arasında isteğe bağlı bir sınır. Bu sınır bir uygulama etki alanı ya da işlem sınırı olabilir.  
  
 İşlem hattı ortasında sözleşme kesim ana bilgisayarın uygulama etki alanı ve eklentinin uygulama etki alanı yüklenir. Sözleşme sanal yöntemleri tanımlar, konak ve türleri birbirleriyle exchange için eklenti kullanın.  
  
 Yalıtım sınırı geçmek için türler sözleşmeleri veya serializable türler olmalıdır. Sözleşmeleri olmayan türler veya serializable türler işlem hattındaki bağdaştırıcısı parçaları tarafından sözleşmelerine dönüştürülmesi gerekir.  
  
 Görünüm işlem hattının soyut taban sınıfları veya konak ve eklenti anlaşma tarafından tanımlandığı şekilde paylaşırlar, yöntem bir görünümünü sağlamak arabirimleri segmentler.  
  
 Geliştirme hakkında daha fazla bilgi için ardışık düzen segmentleri, bkz: [ardışık düzen geliştirme](../../../docs/framework/add-ins/pipeline-development.md).  
  
 Aşağıdaki bölümlerde, eklenti modeli özellikleri açıklanmaktadır.  
  
### <a name="independent-versioning"></a>Bağımsız bir sürüm oluşturma  
 Eklenti modeli ana bilgisayarlar ve eklentiler sürüme bağımsız olarak sağlar. Sonuç olarak, aşağıdaki senaryolarda eklenti modeli sağlar:  
  
-   Bir bağdaştırıcı oluşturma, bir konağın konak önceki bir sürümü için yerleşik bir eklenti kullanmasını sağlar.  
  
-   Bir bağdaştırıcı oluşturma, bir konağın konak daha sonraki bir sürümüyle oluşturulmuş bir eklenti kullanmasını sağlar.  
  
-   Add-INS kullanmak bir konak sağlayan bir bağdaştırıcı oluşturma için farklı bir konak üzerine kurulmuştur.  
  
### <a name="discovery-and-activation"></a>Bulma ve etkinleştirme  
 Bir eklenti, bir bilgi deposundan bulunan eklentileri temsil eden bir koleksiyondan bir belirteç kullanarak etkinleştirebilirsiniz. Eklentileri eklenti konağın görünümü tanımlayan türü için arama yaparak bulunamadı. Bir özel eklenti tarafından eklentiyi tanımlayan tür bulabilirsiniz. Bilgi deposunu iki önbellek dosyalardan oluşur: işlem hattı mağazaya ve eklenti.  
  
 Güncelleştirme ve bilgi deposunu yeniden oluşturma hakkında daha fazla bilgi için bkz: [eklenti bulma](https://msdn.microsoft.com/library/5d268dde-11df-4c4d-a022-f58d88bbc421). Eklentileri etkinleştirme hakkında daha fazla bilgi için bkz: [eklenti etkinleştirme](https://msdn.microsoft.com/library/bedcbcdf-5964-4215-b5f3-3299798b2b3f) ve [nasıl yapılır: eklentileri farklı yalıtım ve güvenlik ile etkinleştirme](https://msdn.microsoft.com/library/7afe7ec8-5158-4350-9119-5df0ecab8aa5).  
  
### <a name="isolation-levels-and-external-processes"></a>Yalıtım düzeyleri ve dış işlemleri  
 Eklenti modeli birkaç eklentileri veya bir eklenti ile bunun konağı arasında yalıtım düzeyini destekler. Az yalıtılmış başlayarak, bu düzeyler şunlardır:  
  
-   Eklenti aynı uygulama etki alanı konağı olarak çalıştırır. Yalıtım ve farklı uygulama etki alanları kullandığınızda aldığınız kaldırma özellikleri kaybetmek nedeniyle bu önerilmez.  
  
-   Birden çok eklentileri, ana bilgisayar tarafından kullanılan uygulama etki alanından farklı aynı uygulama etki alanına yüklenir.  
  
-   Her eklenti yalnızca kendi uygulama etki alanına yüklenir. Bu yalıtım en genel düzeydir.  
  
-   Birden çok eklentileri, bir dış işlem aynı uygulama etki alanına yüklenir.  
  
-   Her eklenti yalnızca bir dış işlem kendi uygulama etki alanına yüklenir. Bu en yalıtılmış bir senaryodur.  
  
 Dış işlemlere kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: eklentileri farklı yalıtım ve güvenlik ile etkinleştirme](https://msdn.microsoft.com/library/7afe7ec8-5158-4350-9119-5df0ecab8aa5).  
  
### <a name="lifetime-management"></a>Ömür Yönetimi  
 Uygulama etki alanı ve işlem sınırları eklenti modeli yayılan olduğundan, çöp toplamanın kendisini bırakın ve nesneleri geri kazanmak için yeterli değil. Eklenti modeli belirteçleri ve başvuru sayımı kullanan bir ömrü Yönetimi mekanizması sağlar ve ek programlama genellikle gerekli değildir. Daha fazla bilgi için [ömür Yönetimi](https://msdn.microsoft.com/library/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).  
  
 [Başa dön](#top)  
  
<a name="distinguishing_between_addins_and_hosts"></a>   
## <a name="distinguishing-between-add-ins-and-hosts"></a>Eklentiler ve konaklar arasında ayrım  
 Bir eklenti ile ana bilgisayar arasındaki fark yalnızca konak eklentiyi etkinleştirir bir olmasıdır. Konak bir sözcük işleme uygulama ve onun yazım denetleyicileri gibi iki büyük olabilir. veya konağın bir medya yürütücüsü katıştıran anlık ileti istemcisi gibi iki daha küçük olabilir. Eklenti modeli, hem istemci hem de sunucu senaryolarda eklentileri destekler. Posta sunucuları virüs taraması, istenmeyen posta filtreleri ve IP koruma sağlayan eklentileri sunucu eklentileri örnekleridir. İstemci eklentisi için sözcük işlemci, grafik programı, oyunlar ve virüs taraması için yerel e-posta istemcileri için özelleştirilmiş bir Özellik Başvurusu eklentileri örneklerindendir.  
  
 [Başa dön](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[İşlem Hattı Geliştirme](../../../docs/framework/add-ins/pipeline-development.md)|Eklentinin ana bilgisayar uygulamasına kesimlerinden iletişim hattının açıklar. İşlem hattı oluşturmak ve parçaları Visual Studio'da işlem hattını dağıtmak anlatan izlenecek yol konuları kod örnekleri sunmaktadır.|  
|[Uygulama Etki Alanları ve Derlemeler](https://msdn.microsoft.com/library/433b04ae-4ba8-4849-9dbd-79194f240346)|Güvenlik, güvenilirlik ve sürüm oluşturma için bir yalıtım sınırı sağlar uygulama etki alanları ve derlemeler arasındaki ilişkiyi açıklar.|  
  
 [Başa dön](#top)  
  
<a name="reference"></a>   
## <a name="reference"></a>Başvuru  
 <xref:System.AddIn?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Contract?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Hosting?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Pipeline?displayProperty=nameWithType>  
  
 [Başa dön](#top)