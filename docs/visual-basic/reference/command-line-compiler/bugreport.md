---
description: Daha fazla bilgi edinin:-bugreport
title: -bugreport
ms.date: 03/08/2018
helpviewer_keywords:
- -bugreport compiler option [Visual Basic]
- bugreport compiler option [Visual Basic]
- /bugreport compiler option [Visual Basic]
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
ms.openlocfilehash: 45831073121991774e462bce26040c575e0a0dc2
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100468219"
---
# <a name="-bugreport"></a>-bugreport

Bir hata raporunu dosyaaktardığınızda kullanabileceğiniz bir dosya oluşturur.

## <a name="syntax"></a>Söz dizimi

```console
-bugreport:file
```

## <a name="arguments"></a>Bağımsız değişkenler

|Terim|Tanım|
|---|---|
|`file`|Gereklidir. Hata raporunuzu içerecek dosyanın adı. Ad bir boşluk içeriyorsa, dosya adını tırnak işaretleri ("") içine alın.|

## <a name="remarks"></a>Açıklamalar

Aşağıdaki bilgiler öğesine eklenir `file` :

- Derlemedeki tüm kaynak kodu dosyalarının bir kopyası.

- Derlemede kullanılan derleyici seçeneklerinin bir listesi.

- Derleyicinizle ilgili sürüm bilgileri, ortak dil çalışma zamanı ve işletim sistemi.

- Varsa derleyici çıkışı.

- Sorunun açıklaması, size sorulur.

- Sorunun düzeltilmesi için bir açıklama, sizden sorulur.

Tüm kaynak kodu dosyalarının bir kopyası içine eklendiğinden `file` , en kısa olası programda (şüpheli) kod hatasını yeniden oluşturmak isteyebilirsiniz.

> [!IMPORTANT]
> Bu `-bugreport` seçenek potansiyel olarak hassas bilgiler içeren bir dosya oluşturur. Bu geçerli saati, derleyici sürümünü, .NET Framework sürümünü, işletim sistemi sürümünü, Kullanıcı adını, derleyicinin çalıştırıldığı komut satırı bağımsız değişkenlerini, tüm kaynak kodunu ve başvurulan herhangi bir derlemenin ikili biçimini içerir. Bu seçeneğe, bir ASP.NET uygulamasının sunucu tarafı derlemesi için Web.config dosyasında komut satırı seçenekleri belirtilerek erişilebilir. Bunu önlemek için Machine.config dosyasını, kullanıcıların sunucuda derlenmesine izin vermeyecek şekilde değiştirin.

Bu seçenek, veya ile kullanılırsa `-errorreport:prompt` `-errorreport:queue` `-errorreport:send` ve uygulamanız iç derleyici hatasıyla karşılaşırsa, Içindeki bilgiler `file` Microsoft Corporation 'a gönderilir. Bu bilgiler, Microsoft mühendislerinin hatanın nedenini belirlemesine yardımcı olur ve Visual Basic sonraki sürümünün artırılmasına yardımcı olabilir. Varsayılan olarak, Microsoft 'a hiçbir bilgi gönderilmez. Ancak, varsayılan olarak etkinleştirilen bir uygulamayı kullanarak derlerken, `-errorreport:queue` uygulama hata raporlarını toplar. Daha sonra, bilgisayarın Yöneticisi oturum açtığında, hata raporlama sistemi, yöneticinin oturum açmadan bu yana oluşan tüm hata raporlarını iletmesini sağlayan bir açılır pencere görüntüler.

> [!NOTE]
> `-bugreport`Bu seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derleme yaptığınızda kullanılabilir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, *T2. vb* ' i derler ve tüm hata raporlama bilgilerini dosya *Problem.txt* koyar.

```console
vbc -bugreport:problem.txt t2.vb
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic Command-Line derleyicisi](index.md)
- [-Debug (Visual Basic)](debug.md)
- [-errorreport](errorreport.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)
- [securityPolicy için trustLevel öğesi (ASP.NET Settings şeması)](/previous-versions/dotnet/netframework-4.0/as399f0x(v=vs.100))
