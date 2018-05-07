---
title: .NET Framework'te Sürüm Uyumluluğu
ms.custom: updateeachrelease
ms.date: 04/10/2018
helpviewer_keywords:
- .NET Framework, version compatibility
- .NET Framework 4.5, compatibility with earlier versions
- .NET Framework versions, compatibility
ms.assetid: 2f25e522-456a-48c3-8a53-e5f39275649f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 15c5455bd604765ebcd78aa418d2f74f4141628d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="version-compatibility-in-the-net-framework"></a>.NET Framework'te Sürüm Uyumluluğu
Geriye dönük uyumluluk bir platform, belirli bir sürümü için geliştirilen bir uygulamayı, platform sonraki sürümlerinde çalıştırılacağı anlamına gelir. Geriye dönük uyumluluk en üst düzeye çıkarmak .NET Framework çalışır: kaynak için bir .NET Framework sürümünü, .NET Framework'ün sonraki sürümlerinde derleme ve .NET Framework bir sürümünü çalıştıran ikili dosyaları davranır aynı üzerinde yazılan kod .NET Framework'ın sonraki sürümleri.  
  
<a name="Apps"></a>   
## <a name="version-compatibility-for-apps"></a>Uygulamalar için sürüm uyumluluğu  
 Varsayılan olarak, bir uygulama için oluşturulan .NET Framework sürümünü çalıştırır. Bu sürümü mevcut değil ve uygulama yapılandırma dosyası desteklenen sürümleri tanımlamaz, .NET Framework başlatma hatası ortaya çıkabilir. Bu durumda, uygulamayı çalıştırma denemesi başarısız olur.  
  
 Uygulamanızın üzerinde çalışacağı belirli sürümlerini tanımlamak için bir veya daha fazla ekleyin [ \<supportedRuntime >](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) , uygulamanızın yapılandırma dosyasına öğeleri. Her `<supportedRuntime>` öğesi listeler çalışma zamanı ilk ile desteklenen bir sürümünü belirtme en çok tercih edilen sürüm ve son az tercih edilen sürümünü belirtme.  
  
```xml  
<configuration>  
   <startup>  
      <supportedRuntime version="v2.0.50727" />  
      <supportedRuntime version="v4.0" />  
   </startup>  
</configuration>  
```  
  
 Daha fazla bilgi için bkz: [nasıl yapılır: bir uygulama destek .NET Framework 4 veya 4.x yapılandırma](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md).  
  
## <a name="version-compatibility-for-components"></a>Bileşenleri için sürüm uyumluluğu  
 Bir uygulamayı .NET, onu çalışır, ancak bir bileşeni olamaz Framework sürümünü kontrol edebilirsiniz. Bileşenleri ve sınıf kitaplıkları belirli bir uygulama bağlamında yüklenir ve bu nedenle otomatik olarak uygulamanın çalıştığı .NET Framework sürümünü çalıştırın.  
  
 Bu kısıtlama nedeniyle uyumluluk garanti bileşenleri için özellikle büyük/küçük harf önemlidir. .NET Framework 4 ile başlayarak, kendisine bir bileşen beklenmektedir uygulayarak birden çok sürümleri arasında uyumlu kalmasını derecesini belirtebilirsiniz <xref:System.Runtime.Versioning.ComponentGuaranteesAttribute?displayProperty=nameWithType> özniteliği bu bileşen için. Araçlar, bu öznitelik uyumluluk olası ihlallerini gelecekte bir bileşenin sürümlerini garanti algılamak için kullanabilirsiniz.  
  
## <a name="backward-compatibility-and-the-net-framework-45"></a>Geriye dönük uyumluluk ve .NET Framework 4.5  
 .NET Framework 4.5 ve sonraki sürümleri geriye dönük olarak uyumlu .NET Framework'ün önceki sürümleriyle oluşturulan uygulamaları ile. Diğer bir deyişle, uygulamaları ve bileşenleri önceki sürümleriyle oluşturulan değişiklik yapılmadan .NET Framework 4.5 ve sonraki sürümlerinde çalışır. Ancak, .NET Framework 4.5 veya sonraki sürümler çalıştırmayı uygulamanızı etkinleştirmek için bir yapılandırma dosyası sağlamanız gerekebilir şekilde varsayılan olarak, uygulamalar, bunlar geliştirilmiştir, ortak dil çalışma zamanı sürümünde çalıştırın. Daha fazla bilgi için bkz: [uygulamalar için sürüm uyumluluğu](#Apps) bu makalenin önceki bölümünde.  
  
 Uygulamada, bu uyumluluk teknikleri programlama değişiklikler ve .NET Framework içinde görünen göz önüne değişikliklerden ayrılabilir. Örneğin, .NET Framework 4. 5'deki performans iyileştirmeleri önceki sürümlerinde oluşmadı bir yarış durumu getirebilir. Benzer şekilde, .NET Framework derlemeleri sabit kodlanmış yolunu kullanarak, belirli bir .NET Framework sürümü ile bir eşitlik karşılaştırması gerçekleştirme ve yansıma kullanarak bir özel alanın değerini alma geriye dönük olarak uyumlu yöntemler değildir. Ayrıca, her .NET Framework sürümü hata düzeltmeleri ve bazı uygulamalar ve bileşenler uyumluluğunu etkileyebilecek güvenlikle ilgili değişiklikleri içerir.  
  
 Uygulama veya bileşen de .NET Framework 4.5 beklendiği gibi çalışmazsa (kendi noktası sürümleri de dahil olmak üzere [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1 veya 4.7.2, aşağıdaki denetim listelerini kullanın:  
  
-  Uygulamanızı geliştirilmiştir, .NET Framework 4. 0'ile başlayan .NET Framework'ün herhangi bir sürümünü çalıştırmak için bkz: [.NET Framework'te uygulama uyumluluğu](application-compatibility.md) hedeflenen .NET Framework sürüm arasındaki değişiklikleri listesini oluşturmak için ve uygulamanızın çalıştığı sürümü.  

- Bir .NET Framework 3.5 uygulaması varsa, ayrıca bkz. [.NET Framework 4 geçiş sorunları](../../../docs/framework/migration-guide/net-framework-4-migration-issues.md).

- Bir .NET Framework 2.0 uygulaması varsa, ayrıca bkz. [.NET Framework 3.5 SP1'deki değişiklikleri](http://go.microsoft.com/fwlink/?LinkId=186989).

- Bir .NET Framework 1.1 uygulaması varsa, ayrıca bkz. [.NET Framework 2.0 değişiklikleri](http://go.microsoft.com/fwlink/?LinkID=125263).  
  
-   .NET Framework 4.5 veya kendi noktasında sürümleri çalıştırmak için mevcut kaynak kodunda yeniden derlenmesi veya bir uygulama ya da hedefler bileşeni yeni bir sürümü geliştiriyorsanız [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] veya kendi noktası bir var olan kaynak kodu temel, denetimden serbest [ Sınıf Kitaplığı'nda ne kullanılmıyor](../../../docs/framework/whats-new/whats-obsolete.md) için Kullanımdan kalktı türleri ve üyeleri ve açıklanan geçici çözümü uygulayın. (Önceden derlenmiş kod türleri ve kullanılmayan olarak işaretlenen üyeleri karşı çalışmaya devam eder.)  
  
-   Karar verirseniz bir değişiklik [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] onay uygulamanızı bozuk [çalışma zamanı Ayarları Şeması](../../../docs/framework/configure-apps/file-schema/runtime/index.md) bir çalışma zamanı ayar, uygulamanızın yapılandırma dosyasına önceki davranışını geri yüklemek için kullanabileceğiniz olup olmadığını belirlemek için.  
  
-   Bir sorun belgelenmemiştir bir sorunla karşılaşırsanız, açmak [.NET Geliştirici topluluğu site](https://developercommunity.visualstudio.com/spaces/61/index.html) veya bir sorunu açın [Microsoft/dotnet GitHub deposuna](https://github.com/microsoft/dotnet/issues).
  
## <a name="compatibility-and-side-by-side-execution"></a>Uyumluluk ve yan yana yürütme  
 Sorununuz için uygun bir geçici çözüm bulamazsanız, .NET Framework 4.5 (veya kendi noktası sürümlerin) 1.1, 2.0 ve 3.5 sürümleri yan yana çalışır ve sürüm 4 değiştiren bir yerinde güncelleştirmesidir unutmayın. 1.1, 2.0 ve 3.5 sürümlerini hedefleyen uygulamalar için en iyi ortamında uygulamayı çalıştırmak için hedef makinede .NET Framework'ün uygun sürümüne yükleyebilirsiniz. Yan yana yürütme hakkında daha fazla bilgi için bkz: [yan yana yürütme](../../../docs/framework/deployment/side-by-side-execution.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yenilikler](../../../docs/framework/whats-new/index.md)  
 [Sınıf Kitaplığında Artık Kullanılmayanlar](../../../docs/framework/whats-new/whats-obsolete.md)  
 [Uygulama Uyumluluğu](../../../docs/framework/migration-guide/application-compatibility.md)  
 [Microsoft .NET Framework destek yaşam döngüsü ilkesi](http://go.microsoft.com/fwlink/p/?LinkId=248212)  
 [.NET framework 4 geçiş sorunları](../../../docs/framework/migration-guide/net-framework-4-migration-issues.md)
