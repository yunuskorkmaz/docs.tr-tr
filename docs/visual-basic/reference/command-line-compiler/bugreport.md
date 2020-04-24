---
title: -bugreport
ms.date: 03/08/2018
helpviewer_keywords:
- -bugreport compiler option [Visual Basic]
- bugreport compiler option [Visual Basic]
- /bugreport compiler option [Visual Basic]
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
ms.openlocfilehash: 02d84bceb0242988c70889ddd5d3dc7530f6e808
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793542"
---
# <a name="-bugreport"></a>-bugreport

Bir hata raporunu dosyaaktardığınızda kullanabileceğiniz bir dosya oluşturur.

## <a name="syntax"></a>Sözdizimi

```console
-bugreport:file
```

## <a name="arguments"></a>Bağımsız Değişkenler

|Sözleşme Dönemi|Tanım|
|---|---|
|`file`|Gereklidir. Hata raporunuzu içerecek dosyanın adı. Ad bir boşluk içeriyorsa, dosya adını tırnak işaretleri ("") içine alın.|

## <a name="remarks"></a>Açıklamalar

Aşağıdaki bilgiler öğesine `file`eklenir:

- Derlemedeki tüm kaynak kodu dosyalarının bir kopyası.

- Derlemede kullanılan derleyici seçeneklerinin bir listesi.

- Derleyicinizle ilgili sürüm bilgileri, ortak dil çalışma zamanı ve işletim sistemi.

- Varsa derleyici çıkışı.

- Sorunun açıklaması, size sorulur.

- Sorunun düzeltilmesi için bir açıklama, sizden sorulur.

Tüm kaynak kodu dosyalarının bir kopyası içine `file`eklendiğinden, en kısa olası programda (şüpheli) kod hatasını yeniden oluşturmak isteyebilirsiniz.

> [!IMPORTANT]
> Bu `-bugreport` seçenek potansiyel olarak hassas bilgiler içeren bir dosya oluşturur. Bu geçerli saati, derleyici sürümünü, .NET Framework sürümünü, işletim sistemi sürümünü, Kullanıcı adını, derleyicinin çalıştırıldığı komut satırı bağımsız değişkenlerini, tüm kaynak kodunu ve başvurulan herhangi bir derlemenin ikili biçimini içerir. Bu seçeneğe, bir ASP.NET uygulamasının sunucu tarafı derlemesi için Web. config dosyasında komut satırı seçenekleri belirtilerek erişilebilir. Bunu önlemek için Machine. config dosyasını, kullanıcıların sunucuda derlenmesine izin vermeyecek şekilde değiştirin.

Bu `-errorreport:prompt`seçenek, `-errorreport:queue`veya `-errorreport:send`ile kullanılırsa ve uygulamanız iç derleyici hatasıyla karşılaşırsa, içindeki `file` bilgiler Microsoft Corporation 'a gönderilir. Bu bilgiler, Microsoft mühendislerinin hatanın nedenini belirlemesine yardımcı olur ve Visual Basic sonraki sürümünün artırılmasına yardımcı olabilir. Varsayılan olarak, Microsoft 'a hiçbir bilgi gönderilmez. Ancak, varsayılan olarak etkinleştirilen bir uygulamayı kullanarak `-errorreport:queue`derlerken, uygulama hata raporlarını toplar. Daha sonra, bilgisayarın Yöneticisi oturum açtığında, hata raporlama sistemi, yöneticinin oturum açmadan bu yana oluşan tüm hata raporlarını iletmesini sağlayan bir açılır pencere görüntüler.

> [!NOTE]
> Bu `-bugreport` seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derleme yaptığınızda kullanılabilir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, *T2. vb* dosyasını derler ve hata raporlama bilgilerini *sorunlu. txt*dosyasına koyar.

```console
vbc -bugreport:problem.txt t2.vb
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](index.md)
- [-Debug (Visual Basic)](debug.md)
- [-errorreport](errorreport.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)
- [securityPolicy için trustLevel öğesi (ASP.NET Settings şeması)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/as399f0x(v=vs.100))
