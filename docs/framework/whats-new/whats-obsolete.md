---
title: .NET Framework artık kullanılmıyor
description: .NET sınıf kitaplığı 'nın üyeleri nasıl eski olarak işaretlediği hakkında bilgi alın. Kullanımdan kaldırılmış Teattribute özniteliğini, eski türleri ve üyeleri nasıl işleyeceğinizi ve daha fazlasını anlayın.
ms.custom: updateeachrelease
ms.date: 04/02/2019
helpviewer_keywords:
- obsolete [.NET Framework]
- what's obsolete [.NET Framework]
- deprecated [.NET Framework]
ms.assetid: d356a43a-73df-4ae2-a457-b9628074c7cd
ms.openlocfilehash: 2f39f5ec614b669f3a0f63677cb6f8a6f9ed11cf
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925806"
---
# <a name="whats-obsolete-in-the-net-framework-class-library"></a>.NET Framework sınıfı kitaplığındaki kullanım dışı Özellikler

Zamana göre .NET değişiklikleri. Her yeni sürüm yeni türler ve yeni işlevsellik sağlayan tür üyeleri ekler. Mevcut türler ve üyeleri zaman içinde de değişir. Örneğin, destekledikleri teknoloji yeni bir teknoloji ile değiştirildiklerinde bazı türler daha az önemli hale gelir ve bazı yöntemlerin yerini, bir şekilde daha yeni yöntemler almıştır.

.NET Framework ve ortak dil çalışma zamanı, geriye dönük uyumluluğu desteklemeye çalışır (bir .NET Framework sürümü ile geliştirilen uygulamaların bir sonraki .NET Framework sürümünde çalışmasına izin verir). Bu, bir türü veya tür üyesini kaldırmayı zorlaştırır. Bunun yerine, .NET, bir türün veya bir tür üyesinin artık eski veya kullanım dışı olarak işaretleyerek kullanılmayacağını gösterir. Bir türün veya üyenin kullanım dışı bırakılması, geliştiricilerin göz önünde bulundurulmasını ve kaldırılmasına yanıt vermek için zaman aldığını bilmesini sağlayacak şekilde işaretlemeyi içerir. Ancak, türü veya üyeyi kullanan mevcut kod, .NET 'in yeni sürümünde çalışmaya devam eder.

> [!NOTE]
> *Kullanımdan kalktı* ve *kullanım dışı bırakılmış* koşullar, .net türlerine ve üyelerine uygulandığında aynı anlama sahiptir.

## <a name="the-obsoleteattribute-attribute"></a>Kullanımdan kaldırma Teattribute özniteliği

.NET Framework, bir tür veya tür üyesinin özniteliği ile işaretleyerek artık kullanılmıyor olduğunu gösterir <xref:System.ObsoleteAttribute> . Özniteliği bir türe veya üyeye uygulamak, türün veya üyenin, bu üyeyi kullanan derlenmiş kodu bozmadan .NET Framework sonraki bir sürümünde kaldırılacağını belirtir.

Bir türün veya tür üyesinin kullanılmıyor olduğunu belirten ek olarak, <xref:System.ObsoleteAttribute> derleyicinin bu türü veya üyeyi içeren kaynak kodu nasıl işlediğini tanımlar. Derleyici kodu derleyebilir, ancak bir uyarı iletisi yayabilir veya bir hata olarak türün veya üyenin kullanımını ele alabilir. İlk durumda, kod başarıyla derleyebilir, ancak bir uyarı iletisi türün veya üyenin artık kullanılmıyor olduğunu gösterir. İkinci durumda, derleme başarısız olur.

Derleme bir uyarı iletisi yerine bir hata üretse bile, <xref:System.ObsoleteAttribute> çalışma zamanı davranışını etkilemez. Diğer bir deyişle, türü veya üyeyi kullanan ve başarıyla derlenen uygulamalar her zaman başarıyla çalışacaktır. Yalnızca türü veya üyeyi kullanan bir uygulamayı yeniden derleme girişimi başarısız olur.

## <a name="how-to-handle-obsolete-types-and-members"></a>Eski türleri ve üyeleri işleme

Mevcut kodu yükselttiğinizde ve yeniden derleyeceğinden, eski bir tür veya uygulamanızda bir derleyici uyarısı üreten bir üyenin kullanılması kusursuz kabul edilebilir. Ancak, uygulama kodunuzu değiştirip değiştirmeyeceğinizi öğrenmek için derleyici uyarı iletisini gözden geçirmeniz gerekir. İleti uygun bir alternatifi işaret etmez, aşağıdakilerden birini yapmalısınız:

- Mümkünse, türün veya üyenin kullanımını kaldırarak kodunuzu değiştirin.

     -veya-

- Kullanımdan kaldırma işlemine nasıl yanıt verileceğini öğrenmek için bu teknoloji alanının belgelerini gözden geçirin.

Mevcut kodu .NET Framework sonraki bir sürümüne karşı yeniden derleyemeyebilirsiniz. Bunun yerine, mevcut derlenmiş kodunuzun çalıştığı .NET Framework sürümünü belirtebilirsiniz. Örneğin, .NET Framework 3,5 'e göre derlenen app1.exe adlı bir uygulamanız olduğunu varsayalım, ancak uygulamanın .NET Framework 4,5 ' e karşı çalıştırılmasını istiyorsunuz. Bu, aşağıdaki adımları gerektirir:

1. Ana yürütülebilir dosyanız için bir yapılandırma dosyası oluşturun *ve.exe.config adı* olarak adlandırın; burada *appname* , uygulamanın yürütülebilir dosyasının adıdır. Örneğimizde *app1.exe* adlı uygulama için *app1.exe.config*adlı bir yapılandırma dosyası oluşturacaksınız.

2. Yapılandırma dosyasına aşağıdakini ekleyin.

    ```xml
    <configuration>
       <startup>
          <supportedRuntime version="v4.0" />
       </startup>
    </configuration>
    ```

.NET Framework belirli bir sürümünü hedeflemek için, aşağıdaki dize değerlerinden birini `version` özniteliğe atayın:

|.NET Framework sürümü|`version`dizisinde|
|-|-|
|4,8|v4.0|
|4,7 (4.7.1 ve 4.7.2 dahil)|v4.0|
|4,6 (4.6.1 ve 4.6.2 dahil)|v4.0|
|4,5 (4.5.1 ve 4.5.2 dahil)|v4.0|
|4|v4.0|
|3,5|v 2.0.50727|
|2,0|v 2.0.50727|
|1.1|v 1.1.4322|
|1,0|v 1.0.3705|

## <a name="obsolete-apis-for-net-framework-45-and-later-versions"></a>.NET Framework 4,5 ve üzeri sürümler için kullanılmayan API 'Ler

- [Kullanılmayan türler](obsolete-types.md)
- [Eski Üyeler](obsolete-members.md)

## <a name="obsolete-apis-for-previous-versions"></a>Önceki sürümler için kullanımdan kaldırılmış API 'Ler

- [.NET Framework 4 ' te kullanılmıyor türler](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee461503(v=vs.100))
- [.NET Framework 4 ' te kullanılmayan Üyeler](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee471421(v=vs.100))
- [.NET Framework 3,5 listesi artık kullanılmıyor](https://docs.microsoft.com/previous-versions/cc835481(v=msdn.10))
- [.NET Framework 2,0 listesi artık kullanılmıyor](https://docs.microsoft.com/previous-versions/aa497286(v=msdn.10))

## <a name="see-also"></a>Ayrıca bkz.

- [\<supportedRuntime>Dosyalarında](../configure-apps/file-schema/startup/supportedruntime-element.md)
