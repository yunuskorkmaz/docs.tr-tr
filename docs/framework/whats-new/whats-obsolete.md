---
title: Hangi&#39;s eski .NET Framework sınıf kitaplığı
ms.custom: updateeachrelease
ms.date: 04/10/2018
helpviewer_keywords:
- obsolete [.NET Framework]
- what's obsolete [.NET Framework]
- deprecated [.NET Framework]
ms.assetid: d356a43a-73df-4ae2-a457-b9628074c7cd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8af9d0f3c31e9178e815dc8fb00f192b8da3e5de
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54541267"
---
# <a name="what39s-obsolete-in-the-net-framework-class-library"></a>Hangi&#39;s eski .NET Framework sınıf kitaplığı
.NET Framework, zaman içinde değişir. Her yeni sürümü, yeni türler ve yeni işlevleri sağlayan bir tür üyeleri ekler. Ayrıca varolan türleri ve üyeleri zamanla değişir. Örneğin, bazı türleri destekledikleri teknoloji tarafından yeni bir teknoloji değiştirilir daha az önemli hale gelir ve bazı yöntemler daha kullanışlı ya da daha tam özellikli olan yeni yöntemlerle olandır.  
  
 .NET Framework ve ortak dil çalışma zamanı desteği (bir .NET Framework'ün sonraki sürüm üzerinde çalıştırmak için .NET Framework sürümü ile geliştirilen uygulamaları olanak tanır) geriye dönük uyumluluk çaba harcar. Bu, yalnızca bir tür veya tür üyesi kaldırmak zorlaştırır. Bunun yerine, .NET Framework türü veya tür üyesi artık kullanılmayan veya kullanım dışı olarak işaretleyerek kullanılması gerektiğini gösterir. Bir tür veya üye kullanım dışı bırakılıyor, böylece geliştiriciler, kaybolur ve yanıtlamak için bunun kaldırılması için zamanınız farkında İmleme içerir. Ancak, türe veya üyeye kullanan mevcut kodu .NET Framework'ün yeni sürümde çalışmaya devam eder.  
  
> [!NOTE]
>  Koşulları *eski* ve *kullanım dışı* türleri ve üyeleri .NET Framework'ün uygulandığında anlamı yoktur.  
  
## <a name="the-obsoleteattribute-attribute"></a>ObsoleteAttribute özniteliği  
 .NET Framework tür veya üyenin türü ile işaretleyerek eski gösterir <xref:System.ObsoleteAttribute> özniteliği. Öznitelik bir türe veya üyeye uygulama .NET Framework bu üyeyi kullanan son derlenen kod olmadan bazı gelecek sürümünde türe veya üyeye kaldırılacak gösterir.  
  
 Bir tür veya tür üye eski olduğunu belirten ek olarak <xref:System.ObsoleteAttribute> derleyici bu tür veya üye içeren kaynak kodu nasıl işlediğini tanımlar. Derleyici, kodu derlemek ancak bir uyarı iletisi yayma ya da hata olarak türe veya üyeye kullanımını davranabilirsiniz. İlk durumda, kod başarıyla derleme, ancak bir uyarı iletisi türe veya üyeye geçersiz olduğunu gösterir. İkinci durumda, derleme başarısız oluyor.  
  
 Derleme hata yerine bir uyarı iletisi üretse <xref:System.ObsoleteAttribute> çalışma zamanı davranışını etkilemez. Diğer bir deyişle, türe veya üyeye kullanan ve başarıyla derlediğiniz uygulamalar her zaman başarılı bir şekilde çalışır. Yalnızca türe veya üyeye kullanan bir uygulamayı yeniden derle denemesi başarısız olur.  
  
## <a name="how-to-handle-obsolete-types-and-members"></a>Kullanılmayan türlerin ve üyelerin nasıl ele alınacağını  
 Yükseltme ve mevcut kodu yeniden derlemeniz, bir eski türü veya uygulamanızdaki bir derleyici uyarısı üreten üye edilebilir kullanmaktır. Ancak, uygulama kodunuzu değiştirmeniz olup olmadığını belirlemek için derleyici uyarı iletisini gözden geçirmelisiniz. İleti için uygun bir alternatif işaret etmiyorsa, aşağıdakilerden birini yapmalısınız:  
  
-   Türe veya üyeye, kullanımını mümkünse kaldırarak kodunuzu değiştirin.  
  
     -veya-  
  
-   Nasıl için kullanımdan kaldırılma yanıtlanacağını belirlemek bu teknoloji alanı için belgeleri gözden geçirin.  
  
 .NET Framework'ün daha sonraki bir sürüme karşı mevcut kodu yeniden derlemeniz değil tercih edebilirsiniz. Bunun yerine, karşı mevcut kodu çalıştırır derlenmiş .NET Framework sürümünü belirtebilirsiniz. Örneğin, karşı derlenen app1.exe adlı bir uygulama olduğunu varsayın [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)], ancak uygulamayı karşı çalıştırmak istediğiniz [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Bu, aşağıdaki adımları gerektirir:  
  
1.  Ana, yürütülebilir dosya için bir yapılandırma dosyası oluşturun ve adlandırın *appName*. exe.config olarak, burada *appName* uygulama yürütülebilir adıdır. Bizim örneğimizde App1.exe adlı uygulama için app1.exe.config adlı bir yapılandırma dosyası oluşturursunuz.  
  
2.  Aşağıdaki yapılandırma dosyasına ekleyin.  
  
    ```xml  
    <configuration>  
       <startup>   
          <supportedRuntime version="v4.0" />  
       </startup>  
    </configuration>  
    ```  
  
 Aşağıdaki tablo, atayabileceğiniz dize değerleri listeler `version` belirli bir .NET Framework sürümünü hedefleyecek şekilde özniteliği.  
  
|.NET Framework sürümü|`version` dize|
|-|-|  
|4.7 (4.7.1 ve 4.7.2 dahil)|v4.0|  
|4.6 (4.6.1 ve 4.6.2 dahil)|v4.0|  
|4.5 (4.5.1 ve 4.5.2'yi dahil)|v4.0|  
|4|v4.0|  
|3.5|v2.0.50727|  
|2,0|v2.0.50727|  
|1.1|v1.1.4322|  
|1.0|v1.0.3705|  
  
## <a name="obsolete-lists-for-the-net-framework-45-and-later-versions"></a>Listeleri .NET Framework 4.5 ve sonraki sürümler için eski  
 [Eski Türler](../../../docs/framework/whats-new/obsolete-types.md)  
  
 [Eski Üyeler](../../../docs/framework/whats-new/obsolete-members.md)  
  
## <a name="obsolete-lists-for-previous-versions"></a>Önceki sürümler için eski listeler  
 [.NET Framework 4 içinde eski türler](https://go.microsoft.com/fwlink/?LinkId=224224)  
  
 [.NET Framework 4 içinde eski üyeler](https://go.microsoft.com/fwlink/?LinkId=224227)  
  
 [.NET framework 3.5 eski listesi](https://go.microsoft.com/fwlink/?LinkId=163710)  
  
 [.NET framework 2.0 eski listesi](https://go.microsoft.com/fwlink/?LinkID=125264)  
  
## <a name="see-also"></a>Ayrıca bkz.
- [\<supportedRuntime > öğesi](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)
