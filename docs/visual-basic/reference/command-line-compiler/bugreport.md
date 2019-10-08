---
title: -bugreport
ms.date: 03/08/2018
helpviewer_keywords:
- -bugreport compiler option [Visual Basic]
- bugreport compiler option [Visual Basic]
- /bugreport compiler option [Visual Basic]
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
ms.openlocfilehash: 46d726332806f7d1f6e80dd7df31867051276b45
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002353"
---
# <a name="-bugreport"></a>-bugreport
Bir hata raporunu dosyaaktardığınızda kullanabileceğiniz bir dosya oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-bugreport:file  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`file`|Gerekli. Hata raporunuzu içerecek dosyanın adı. Ad bir boşluk içeriyorsa, dosya adını tırnak işaretleri ("") içine alın.|  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t-0 ' a aşağıdaki bilgiler eklenmiştir:  
  
- Derlemedeki tüm kaynak kodu dosyalarının bir kopyası.  
  
- Derlemede kullanılan derleyici seçeneklerinin bir listesi.  
  
- Derleyicinizle ilgili sürüm bilgileri, ortak dil çalışma zamanı ve işletim sistemi.  
  
- Varsa derleyici çıkışı.  
  
- Sorunun açıklaması, size sorulur.  
  
- Sorunun düzeltilmesi için bir açıklama, sizden sorulur.  
  
 Tüm kaynak kodu dosyalarının bir kopyası `file` ' a eklendiğinden, mümkün olan en kısa programda (şüpheli) kod hatasını yeniden oluşturmak isteyebilirsiniz.  
  
> [!IMPORTANT]
> @No__t-0 seçeneği, potansiyel olarak hassas bilgiler içeren bir dosya oluşturur. Bu geçerli saati, derleyici sürümünü, .NET Framework sürümünü, işletim sistemi sürümünü, Kullanıcı adını, derleyicinin çalıştırıldığı komut satırı bağımsız değişkenlerini, tüm kaynak kodunu ve başvurulan herhangi bir derlemenin ikili biçimini içerir. Bu seçeneğe, bir ASP.NET uygulamasının sunucu tarafı derlemesi için Web. config dosyasında komut satırı seçenekleri belirtilerek erişilebilir. Bunu önlemek için Machine. config dosyasını, kullanıcıların sunucuda derlenmesine izin vermeyecek şekilde değiştirin.  
  
 Bu seçenek `-errorreport:prompt`, `-errorreport:queue` veya `-errorreport:send` ile kullanılırsa ve uygulamanız iç derleyici hatasıyla karşılaşırsa, `file` ' teki bilgiler Microsoft Corporation 'a gönderilir. Bu bilgiler, Microsoft mühendislerinin hatanın nedenini belirlemesine yardımcı olur ve Visual Basic sonraki sürümünün artırılmasına yardımcı olabilir. Varsayılan olarak, Microsoft 'a hiçbir bilgi gönderilmez. Ancak, varsayılan olarak etkinleştirilen `-errorreport:queue` kullanarak bir uygulamayı derlediğinizde, uygulama kendi hata raporlarını toplar. Daha sonra, bilgisayarın Yöneticisi oturum açtığında, hata raporlama sistemi, yöneticinin oturum açmadan bu yana oluşan tüm hata raporlarını iletmesini sağlayan bir açılır pencere görüntüler.  
  
> [!NOTE]
> @No__t-0 seçeneği, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derleme yaptığınızda kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek `T2.vb` ' i derler ve tüm hata raporlama bilgilerini `Problem.txt` dosyasına koyar.  
  
```console  
vbc -bugreport:problem.txt t2.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [-Debug (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md)
- [-errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [securityPolicy için trustLevel öğesi (ASP.NET Settings şeması)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/as399f0x(v=vs.100))
