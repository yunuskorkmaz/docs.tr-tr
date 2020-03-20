---
title: .NET Framework'de neler geçersizdir?
ms.custom: updateeachrelease
ms.date: 04/02/2019
helpviewer_keywords:
- obsolete [.NET Framework]
- what's obsolete [.NET Framework]
- deprecated [.NET Framework]
ms.assetid: d356a43a-73df-4ae2-a457-b9628074c7cd
ms.openlocfilehash: 7cfebfde859a95495e9d2d5e42bd034ad5d55e61
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79143141"
---
# <a name="whats-obsolete-in-the-net-framework-class-library"></a>.NET Framework sınıf kitaplığında geçersiz olanlar

.NET zaman içinde değişir. Her yeni sürüm, yeni işlevler sağlayan yeni türler ve tür üyeleri ekler. Varolan türler ve üyeleri de zaman içinde değişir. Örneğin, destekledikleri teknoloji yeni bir teknolojiyle değiştirildikçe bazı türler daha az önem eger ve bazı yöntemlerin yerini bir şekilde üstün olan yeni yöntemler alır.

.NET Framework ve ortak dil çalışma süresi geriye dönük uyumluluğu desteklemeye çalışır (.NET Framework'ün bir sürümüyle geliştirilen uygulamaların .NET Framework'ün bir sonraki sürümünde çalışmasına izin verir). Bu, yalnızca bir türü veya bir tür üyesini kaldırmayı zorlaştırır. Bunun yerine,.NET, bir tür veya tür üyesinin artık eski veya amortismanlı olarak işaretlenerek kullanılmaması gerektiğini belirtir. Bir türü veya bir üyeyi küçümsemek, geliştiricilerin bu türün ortadan kaldırılacağını ve kaldırılmasına yanıt vermek için zamana sahip olacağının farkında olması için işaretlemeyi içerir. Ancak, türü veya üyeyi kullanan varolan kod .NET'in yeni sürümünde çalışmamaya devam eder.

> [!NOTE]
> .NET türleri ve üyelerine uygulandığında *eski* ve *amortismana uygulanan* terimler aynı anlama gelir.

## <a name="the-obsoleteattribute-attribute"></a>EskiÖz Öznitelik özniteliği

.NET Framework, bir tür veya tür üyesinin <xref:System.ObsoleteAttribute> öznitelik ile işaretleyerek eski olduğunu gösterir. Bir türe veya üyeye öznitelik uygulanması, bu üyeyi kullanan derlenmiş kodu bozmadan .NET Framework'ün gelecekteki bazı sürümünde tür veya üyenin kaldırılacağını gösterir.

Bir tür veya tür üyesinin eski olduğunu belirtmenin <xref:System.ObsoleteAttribute> yanı sıra, derleyicinin bu türü veya üyeyi içeren kaynak kodu nasıl işleyeceğini tanımlar. Derleyici kodu derleyebilir, ancak bir uyarı iletisi yatabilir veya tür veya üyenin kullanımını bir hata olarak değerlendirebilir. İlk durumda, kod başarıyla derlenebilir, ancak bir uyarı iletisi türün veya üyenin geçersiz olduğunu gösterir. İkinci durumda, derleme başarısız olur.

Derleme uyarı iletisi yerine bir hata <xref:System.ObsoleteAttribute> üretse bile, çalışma zamanı davranışını etkilemez. Diğer bir arada, türü veya üyeyi kullanan ve başarılı bir şekilde derlenen uygulamalar her zaman başarılı bir şekilde çalışır. Yalnızca türü veya üyeyi kullanan bir uygulamayı yeniden derleme girişimi başarısız olur.

## <a name="how-to-handle-obsolete-types-and-members"></a>Eski türleri ve üyeleri işlemek için nasıl

Varolan kodu yükselttidiğinizde ve yeniden derlediğinizde, eski bir tür veya uygulamanızda derleyici uyarısı üreten üye yi kullanarak mükemmel bir şekilde kabul edilebilir. Ancak, uygulama kodunuzu değiştirip değiştirmemeniz gerekmediğini belirlemek için derleyici uyarı iletisini gözden geçirmelisiniz. İleti uygun bir alternatife işaret etmiyorsa, aşağıdakilerden birini yapmalısınız:

- Mümkünse türü veya üyekullanımını kaldırarak kodunuzu değiştirin.

     -veya-

- Amortismana nasıl yanıt verileceksiniz belirlemek için bu teknoloji alanı için belgeleri gözden geçirin.

Varolan kodu .NET Framework'ün sonraki bir sürümüne göre yeniden derlememeyi seçebilirsiniz. Bunun yerine, .NET Framework'ün mevcut derlenmiş kodunuzu çalıştırdığı sürümünü belirtebilirsiniz. Örneğin, .NET Framework 3.5'e karşı derlenmiş app1.exe adında bir uygulamanız olduğunu, ancak uygulamanın .NET Framework 4.5'e karşı çalışmasını istediğinizi varsayalım. Bu, aşağıdaki adımları gerektirir:

1. Ana yürütülebilirliğiniz için bir yapılandırma dosyası oluşturun ve *appName*.exe.config adını ve *appName'nin* yürütülebilir uygulamanın adı olduğunu belirtin. Örneğimizde *app1.exe* adlı uygulama için *app1.exe.config*adlı bir yapılandırma dosyası oluşturursunuz.

2. Yapılandırma dosyasına aşağıdakileri ekleyin.

    ```xml
    <configuration>
       <startup>
          <supportedRuntime version="v4.0" />
       </startup>
    </configuration>
    ```

.NET Framework'ün belirli bir sürümünü hedeflemek için, `version` özniteliğe aşağıdaki dize değerlerinden birini atayın:

|.NET Framework sürümü|`version`Dize|
|-|-|
|4.8|v4.0|
|4.7 (4.7.1 ve 4.7.2 dahil)|v4.0|
|4.6 (4.6.1 ve 4.6.2 dahil)|v4.0|
|4.5 (4.5.1 ve 4.5.2 dahil)|v4.0|
|4|v4.0|
|3,5|v2.0.50727|
|2,0|v2.0.50727|
|1.1|v1.1.4322|
|1.0|v1.0.3705|

## <a name="obsolete-apis-for-net-framework-45-and-later-versions"></a>.NET Framework 4.5 ve sonraki sürümler için eski API'ler

- [Eski Türler](obsolete-types.md)
- [Eski Üyeler](obsolete-members.md)

## <a name="obsolete-apis-for-previous-versions"></a>Önceki sürümler için eski API'ler

- [.NET Framework 4'te Eski Türler](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee461503(v=vs.100))
- [.NET Framework 4'te Eski Üyeler](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee471421(v=vs.100))
- [.NET Framework 3.5 Eski Liste](https://docs.microsoft.com/previous-versions/cc835481(v=msdn.10))
- [.NET Framework 2.0 Eski Liste](https://docs.microsoft.com/previous-versions/aa497286(v=msdn.10))

## <a name="see-also"></a>Ayrıca bkz.

- [\<desteklenenRuntime> Öğesi](../configure-apps/file-schema/startup/supportedruntime-element.md)
