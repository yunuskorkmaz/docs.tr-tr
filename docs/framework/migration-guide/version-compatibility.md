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
ms.openlocfilehash: 1f27385fadd872d2ff6f84cabe079811142008df
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59143656"
---
# <a name="version-compatibility-in-the-net-framework"></a>.NET Framework'te Sürüm Uyumluluğu
Geriye dönük uyumluluk, bir platformun belirli bir sürümü için geliştirilen bir uygulamanın o platformun sonraki sürümlerinde çalışır anlamına gelir. .NET Framework, geriye dönük uyumluluğu en üst düzeye çıkarmaya çalışır: .NET Framework'ün sonraki sürümlerinde .NET Framework sürümü için yazılan kaynak kodu derlemeniz gerekir ve .NET Framework'ün sonraki sürümlerinde .NET Framework sürümünde çalışan ikili dosyaları aynı şekilde davranır.  
  
<a name="Apps"></a>   
## <a name="version-compatibility-for-apps"></a>Uygulamalar için sürüm uyumluluğu  
 Varsayılan olarak, bir uygulama derlendiği .NET Framework sürümünde çalışır. Bu sürüm yoksa ve uygulama yapılandırma dosyası desteklenen sürümleri tanımlamıyorsa, bir .NET Framework başlatma hatası oluşabilir. Bu durumda, uygulamayı çalıştırma denemesi başarısız olur.  
  
 Uygulamanızın üzerinde çalıştığı belirli sürümler tanımlamak için bir veya daha fazla Ekle [ \<supportedRuntime >](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) uygulamanızın yapılandırma dosyasına öğeleri. Her `<supportedRuntime>` öğesi çalışma zamanı ile ilk desteklenen bir sürümünü listeler en çok tercih edilen sürümü ve son sırada en az tercih edilen sürümü belirten.  
  
```xml  
<configuration>  
   <startup>  
      <supportedRuntime version="v2.0.50727" />  
      <supportedRuntime version="v4.0" />  
   </startup>  
</configuration>  
```  
  
 Daha fazla bilgi için [nasıl yapılır: Bir uygulamayı destek .NET Framework 4 veya 4.x yapılandırma](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md).  
  
## <a name="version-compatibility-for-components"></a>Bileşenler için sürüm uyumluluğu  
 Uygulama, onu çalışır, ancak bir bileşen bunu yapamaz .NET Framework sürümünü denetleyebilir. Bileşenler ve sınıf kitaplıkları belirli bir uygulama bağlamında yüklenir ve bu nedenle otomatik olarak uygulamanın çalıştığı .NET Framework sürümünde çalışır.  
  
 Bu kısıtlama nedeniyle, uyumluluk garantileri bileşenler için özellikle büyük/küçük harf önemlidir. .NET Framework 4 ile başlayarak, bir bileşene uygulayarak birden çok sürüm genelinde uyumlu kalmasını bekleme derecesini belirtebilirsiniz <xref:System.Runtime.Versioning.ComponentGuaranteesAttribute?displayProperty=nameWithType> bileşenin özniteliği. Araçlar, uyumluluk olası ihlallerini bir bileşenin gelecek garanti algılamak için bu özniteliği kullanabilirsiniz.  
  
## <a name="backward-compatibility-and-the-net-framework-45"></a>Geriye dönük uyumluluk ve .NET Framework 4.5  
 Geriye dönük olarak uyumlu .NET Framework 4.5 ve sonraki sürümlerinde .NET Framework'ün önceki sürümleriyle oluşturulmuş uygulamalar. Diğer bir deyişle, uygulamaları ve bileşenleri önceki sürümlerle derlenmiş değişiklik yapılmadan .NET Framework 4.5 ve sonraki sürümlerinde çalışır. Ancak, varsayılan olarak, uygulamanızın .NET Framework 4.5 veya sonraki sürümler üzerinde çalışmasını etkinleştirmek için bir yapılandırma dosyası sağlamanız gerekebilir. Bu nedenle, bunlar geliştirilen, ortak dil çalışma zamanı sürümünde uygulamalar çalıştırın. Daha fazla bilgi için [uygulamalar için sürüm uyumluluğu](#Apps) bu makalenin önceki kısımlarında bölümü.  
  
 Uygulamada bu uyumluluk .NET Framework ve programlama tekniklerindeki görünüşte değişimlerle bölünebilir. Örneğin, .NET Framework 4.5 performans geliştirmeleri, önceki sürümlerinde gerçekleşmeyen bir yarış durumu açığa çıkarabilir. Benzer şekilde, .NET Framework derlemelerine yönelik sabit kodlanmış bir yol kullanarak, belirli bir .NET Framework sürümü ile denklik karşılaştırması gerçekleştirme ve yansıma kullanarak bir özel alanın değerinin alınması geriye dönük olarak uyumlu uygulamalar değildir. Ayrıca, .NET Framework'ün her sürümü, hata düzeltmeleri ve bazı uygulamaların ve bileşenlerin uyumluluğunu etkileyebilecek güvenlikle ilgili değişiklikler içerir.  
  
 Uygulama veya bileşen .NET Framework 4.5 üzerinde beklendiği gibi çalışmazsa (onun nokta sürümleri dahil olmak üzere [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1 veya 4.7.2, aşağıdaki denetim listelerini kullanın:  
  
-  Uygulamanızı geliştirilmiştir, .NET Framework 4.0 ile başlayan .NET Framework'ün herhangi bir sürümünü çalıştırmak için bkz: [.NET Framework'te uygulama uyumluluğu](application-compatibility.md) hedeflenen .NET Framework sürümünüz arasında değişiklik listesini oluşturmak için ve uygulamanızın üzerinde çalıştığı sürümü.  

- Bir .NET Framework 3.5 uygulamanız varsa, ayrıca bkz: [.NET Framework 4 geçiş sorunları](../../../docs/framework/migration-guide/net-framework-4-migration-issues.md).

- Bir .NET Framework 2.0 uygulamanız varsa, ayrıca bkz: [.NET Framework 3.5 SP1 içindeki değişiklikleri](https://go.microsoft.com/fwlink/?LinkId=186989).

- Bir .NET Framework 1.1 uygulamanız varsa, ayrıca bkz: [.NET Framework 2.0 içindeki değişiklikleri](https://go.microsoft.com/fwlink/?LinkID=125263).  
  
-   .NET Framework 4.5 veya onun nokta sürümleri çalıştırmak için mevcut kaynak kodu derliyorsanız veya bir uygulama veya bileşen hedefleyen yeni bir sürümünü geliştiriyorsanız [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] veya bir varolan kaynak kod temel, denetimden nokta sürümlerini [ Sınıf Kitaplığı'nda ne kullanılmıyor](../../../docs/framework/whats-new/whats-obsolete.md) için eski türler ve üyeler ve açıklanan geçici çözümü uygulayın. (Önceden derlenmiş kod türleri ve üyeleri artık kullanılmıyor olarak işaretlenmiş karşı çalışmaya devam eder.)  
  
-   Belirlerseniz bir değişiklik [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] onay uygulamanızı bozduğunu [çalışma zamanı Ayarları Şeması](../../../docs/framework/configure-apps/file-schema/runtime/index.md) bir çalışma zamanı ayarı uygulamanızın yapılandırma dosyasında önceki davranışı geri yüklemek için kullanabileceğiniz olup olmadığını belirlemek için.  
  
-   Belgelenmemiş bir sorunla karşılaşırsanız, bir sorun açın [.NET Geliştirici topluluğu sitesini](https://developercommunity.visualstudio.com/spaces/61/index.html) veya bir sorun açın [Microsoft/dotnet GitHub deposunu](https://github.com/microsoft/dotnet/issues).
  
## <a name="compatibility-and-side-by-side-execution"></a>Uyumluluk ve yan yana yürütme  
 Yönelik uygun geçici bir çözüm bulamazsanız, .NET Framework 4.5 (veya onun nokta sürümleri biri) 1.1, 2.0 ve 3.5 sürümleri ile yan yana çalışır ve sürüm 4 yerini alan bir yerinde güncelleştirme olduğunu unutmayın. 1.1, 2.0 ve 3.5 sürümlerini hedefleyen uygulamalar için uygulamayı en iyi ortamında çalıştırmak amacıyla hedef makineye .NET Framework'ün uygun sürümünü yükleyebilirsiniz. Yan yana yürütme hakkında daha fazla bilgi için bkz. [yan yana yürütme](../../../docs/framework/deployment/side-by-side-execution.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yenilikler](../../../docs/framework/whats-new/index.md)
- [Sınıf Kitaplığında Artık Kullanılmayanlar](../../../docs/framework/whats-new/whats-obsolete.md)
- [Uygulama Uyumluluğu](../../../docs/framework/migration-guide/application-compatibility.md)
- [Microsoft .NET Framework Destek Ömrü İlkesi](https://go.microsoft.com/fwlink/p/?LinkId=248212)
- [.NET framework 4 geçiş sorunları](../../../docs/framework/migration-guide/net-framework-4-migration-issues.md)
