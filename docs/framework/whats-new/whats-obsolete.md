---
title: "&#39; teki .NET Framework Sınıf Kitaplığı'te eski"
ms.custom: updateeachrelease
ms.date: 10/17/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
helpviewer_keywords:
- obsolete [.NET Framework]
- what's obsolete [.NET Framework]
- deprecated [.NET Framework]
ms.assetid: d356a43a-73df-4ae2-a457-b9628074c7cd
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d5fc41473c4a3ea812013ee7e5204c22d0a694d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="what39s-obsolete-in-the-net-framework-class-library"></a>&#39; teki .NET Framework Sınıf Kitaplığı'te eski
.NET Framework zaman içinde değişir. Her yeni sürümü yeni türleri ve yeni işlevsellik sağlar tür üyeleri ekler. Ayrıca varolan türleri ve üyeleri zamanla değiştirin. Örneğin, bazı türleri destekledikleri teknolojisi tarafından yeni bir teknoloji değiştirilir daha az önemli hale gelmiştir ve bazı yöntemler daha kullanışlı ya da daha tam özellikli yeni yöntemler tarafından değiştirilen.  
  
 Geriye dönük uyumluluk (.NET Framework'ün sonraki sürümünde çalıştırmak için .NET Framework'ün bir sürüm geliştirilen uygulamaların izin verecek şekilde) desteklemek .NET Framework ve ortak dil çalışma zamanı çalışmalar yapılmaktadır. Bu, yalnızca bir tür veya bir tür üyesi kaldırmak zorlaştırır. Bunun yerine, .NET Framework bir tür veya bir tür üyesi artık kullanılmayan veya kullanım dışı olarak işaretleyerek kullanılması gerektiğini gösterir. Bir tür veya üye onaysız kılınmadan, böylece geliştiriciler, azalttıktan ve onun kaldırma yanıt zamanınız kullanan işaretleme içerir. Ancak, tür veya üye kullanan var olan kod, .NET Framework'ün yeni sürümde çalışmaya devam eder.  
  
> [!NOTE]
>  Koşulları *eski* ve *kullanım dışı* türleri ve .NET Framework üyelerini uygulandığında aynı anlamı yoktur.  
  
## <a name="the-obsoleteattribute-attribute"></a>ObsoleteAttribute özniteliği  
 .NET Framework türü veya tür üyesi ile işaretleyerek eski gösterir <xref:System.ObsoleteAttribute> özniteliği. Öznitelik bir tür veya üye uygulamadan kesme kullanmadan .NET Framework bazı gelecek sürümünde tür veya üye kaldırılacak bu üyeyi kullanan kodu derlenmiş gösterir.  
  
 Bir tür veya bir tür üyesi eski olarak olduğunu belirten ek olarak <xref:System.ObsoleteAttribute> derleyici bu tür veya üye içeren kaynak kodu işleme biçimini tanımlar. Derleyici Kodu derlemek ancak bir uyarı iletisi yayma ya da hata olarak tür veya üye kullanımını davranabilirsiniz. İlk durumda, kodu başarılı bir şekilde derleyebilir, ancak tür veya üye kullanımdan kalkmıştır bir uyarı iletisi gösterir. İkinci durumda, derleme başarısız oluyor.  
  
 Derleme bir uyarı iletisi yerine bir hata oluşturursa bile <xref:System.ObsoleteAttribute> çalışma zamanı davranışını etkilemez. Diğer bir deyişle, tür veya üye kullanan ve başarıyla derlediğiniz uygulamalar her zaman başarıyla çalışacaktır. Yalnızca tür veya üye kullanan bir uygulama derleyin denemesi başarısız olur.  
  
## <a name="how-to-handle-obsolete-types-and-members"></a>Eski türler ve üyeleri nasıl ele alınacağını  
 Yükseltme ve var olan kodu yeniden derleyin, eski türü veya uygulamanızda derleyici uyarısı üreten üye edilebilir kullanmaktır. Ancak, uygulama kodunuzun değiştirmelisiniz olup olmadığını belirlemek için derleyici uyarı iletisi gözden geçirmelidir. İleti için uygun bir alternatif işaret etmiyorsa, aşağıdakilerden birini yapmanız gerekir:  
  
-   Kodunuzu, tür veya üye, kullanımını mümkünse kaldırarak değiştirin.  
  
     veya  
  
-   İçin kullanımdan yanıt vereceğinizi belirlemek bu teknoloji alanı belgelerini gözden geçirin.  
  
 .NET Framework'ün sonraki bir sürümünü karşı var olan kodu derleyin değil seçebilirsiniz. Bunun yerine, göre var olan kodu çalıştırır derlenmiş .NET Framework sürümünü belirtebilirsiniz. Örneğin, karşı derlenen app1.exe adlı bir uygulamanız olduğunu varsayın [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)], ancak uygulamayı karşı çalıştırmak istediğiniz [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Bu, aşağıdaki adımları gerektirir:  
  
1.  Ana yürütülebilir dosyanın için bir yapılandırma dosyası oluşturun ve adlandırın *appName*. exe.config, burada *appName* uygulama yürütülebilir dosyasının adıdır. Örneğimizde App1.exe adı geçen uygulama için app1.exe.config adlı bir yapılandırma dosyası oluşturursunuz.  
  
2.  Aşağıdaki yapılandırma dosyasına ekleyin.  
  
    ```xml  
    <configuration>  
       <startup>   
          <supportedRuntime version="v4.0" />  
       </startup>  
    </configuration>  
    ```  
  
 Aşağıdaki tabloda, atayabilirsiniz dize değerlerini listeler `version` belirli bir .NET Framework sürümünü hedefleyecek şekilde özniteliği.  
  
|.NET Framework sürümü|`version`dize|
|-|-|  
|4.7 (4.7.1 dahil)|v4.0|  
|4.6 (4.6.1 ve 4.6.2 dahil)|v4.0|  
|4.5 (4.5.1 ve 4.5.2 dahil)|v4.0|  
|4|v4.0|  
|3.5|v2.0.50727|  
|2,0|v2.0.50727|  
|1.1|V1.1.4322|  
|1.0|V1.0.3705|  
  
## <a name="obsolete-lists-for-the-net-framework-45-and-46"></a>.NET Framework 4.5 ve 4.6 için artık kullanılmayan listeleri  
 [Eski Türler](../../../docs/framework/whats-new/obsolete-types.md)  
  
 [Eski Üyeler](../../../docs/framework/whats-new/obsolete-members.md)  
  
## <a name="obsolete-lists-for-previous-versions"></a>Önceki sürümler için artık kullanılmayan listeleri  
 [.NET Framework 4'te eski türler](http://go.microsoft.com/fwlink/?LinkId=224224)  
  
 [.NET Framework 4'te eski üyeler](http://go.microsoft.com/fwlink/?LinkId=224227)  
  
 [.NET framework 3.5 artık kullanılmayan liste](http://go.microsoft.com/fwlink/?LinkId=163710)  
  
 [.NET framework 2.0 artık kullanılmayan liste](http://go.microsoft.com/fwlink/?LinkID=125264)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [\<supportedRuntime > öğesi](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)
