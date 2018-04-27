---
title: -bugreport
ms.date: 03/08/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -bugreport compiler option [Visual Basic]
- bugreport compiler option [Visual Basic]
- /bugreport compiler option [Visual Basic]
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 097435a3d8acda6325b27abaf3ca0fd2839d344e
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="-bugreport"></a>-bugreport
Bir hata raporu dosyası oluştururken kullanabileceğiniz bir dosya oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-bugreport:file  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`file`|Gerekli. Hata raporu içeren dosyanın adı. Dosya adını tırnak işaretleri içine alın ("") adı boşluk içeriyorsa.|  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki bilgiler eklenir `file`:  
  
-   Derlemedeki tüm kaynak kodu dosyaları bir kopyası.  
  
-   Derlemede kullanılan derleyici seçenekleri listesi.  
  
-   Derleyici, ortak dil çalışma zamanı ve işletim sistemi hakkında sürüm bilgisi.  
  
-   Derleyici çıkışı, varsa.  
  
-   Kendisi için sizden istenir sorunun açıklaması.  
  
-   Kendisi için sizden istenir sorunu nasıl düşündüğünüz açıklaması düzeltilmelidir.  
  
 Tüm kaynak kodu dosyalarının bir kopyasını dahil olduğundan `file`, kısa olası programında (şüpheli) kod hatası yeniden oluşturmak isteyebilirsiniz.  
  
> [!IMPORTANT]
>  `-bugreport` Seçeneği olası duyarlı bilgileri içeren bir dosya oluşturur. Bu, geçerli saati, derleyici sürümü içerir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sürümü, işletim sistemi sürümü, kullanıcı adı, hangi derleyici çalıştırıldı, tüm kaynak kodu ve ikili biçimi herhangi başvurulan derleme komut satırı bağımsız değişkenleri. Bu seçenek, bir sunucu tarafı derlenmesi için Web.config dosyasındaki komut satırı seçenekleri belirterek erişilebilir bir [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] uygulama. Bunu önlemek için Machine.config dosyasının sunucuda derleme kullanıcıların izin vermeyecek şekilde değiştirin.  
  
 Bu seçenek ile kullanıldığında `-errorreport:prompt`, `-errorreport:queue`, veya `-errorreport:send`, bilgileri bir iç derleyici hatası uygulamanızı karşılaştığında `file` Microsoft Corporation'ın için gönderilir. Bu bilgileri Microsoft mühendisleri hatanın nedenini belirlemeye yardımcı olur ve Visual Basic sonraki sürümü artırmaya yardımcı. Varsayılan olarak, hiçbir bilgi Microsoft'a gönderilmez. Ancak, ne zaman, derleme bir uygulama kullanarak `-errorreport:queue`, varsayılan olarak etkindir, uygulamanın kendi hata raporlarını toplar. Ardından, bilgisayarın yönetici oturum açtığında, hata raporlama sistem oturum açma işleminden sonra oluştu herhangi bir hata raporlarını Microsoft'a iletmek yöneticinin sağlar bir açılır pencere görüntüler.  
  
> [!NOTE]
>  `/bugreport` Kullanılabilir olduğundan komut satırından derleme zaman yalnızca; seçeneği Visual Studio geliştirme ortamında kullanılabilir değil.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek derler `T2.vb` ve tüm hata raporlama bilgileri dosyasına yerleştirir `Problem.txt`.  
  
```  
vbc -bugreport:problem.txt t2.vb  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-debug (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md)  
 [-errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)  
 [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [securityPolicy (ASP.NET Ayarlar Şeması) için trustLevel ögesi](http://msdn.microsoft.com/library/729ab04c-03da-4ee5-86b1-be9d08a09369)
