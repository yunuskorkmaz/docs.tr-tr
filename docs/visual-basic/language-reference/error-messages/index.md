---
title: Hata İletileri (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- errors [Visual Basic]
- error messages
- trappable errors
- errors [Visual Basic], trappable
ms.assetid: f2dda05b-baef-41f5-8bb1-598bd7cf239f
ms.openlocfilehash: 822c0f266e7dd68f063043d98a9f4af308ae93fd
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59338143"
---
# <a name="error-messages-visual-basic"></a>Hata İletileri (Visual Basic)
Yazma, derleme veya Visual Basic uygulamasını çalıştırın, aşağıdaki türde hatalar oluşabilir:  
  
1. Visual Studio'da bir uygulama yazdığınızda, tasarım zamanı hataları.  
  
2. Visual Studio'da veya bir komut isteminde bir uygulama derlerken, derleme zamanı hataları.  
  
3. Visual Studio'da veya tek başına yürütülebilir bir dosya olarak bir uygulamayı çalıştırdığınızda, çalışma zamanı hataları.  
  
 Belirli bir hata giderme hakkında daha fazla bilgi için bkz: [Visual Basic programcıları için ek kaynaklar](../../../visual-basic/getting-started/additional-resources.md).  
  
## <a name="run-time-errors"></a>Çalışma zamanı hataları  
 Bir Visual Basic uygulamasının sistem yürütülemiyor bir eylem gerçekleştirmeye çalışırsa, bir çalışma zamanı hatası oluşur ve Visual Basic oluşturur bir `Exception` nesne. Visual Basic, özel hatalar her türlü verinin oluşturabileceği yazın, dahil olmak üzere `Exception` kullanarak nesneleri, `Throw` deyimi. Uygulama hata özel durum yakalandı, ileti ve hata numarasını görüntüleyerek belirleyebilirsiniz. Bir hata oluştu değil, uygulama sona erer.  
  
 Kod, yakalama ve çalışma zamanı hataları inceleyin. Hata üreten kodun içine, bir `Try` bloğu içinde eşleşen bir hatadır yakalayabilir `Catch` blok. Çalışma zamanı sırasında hataları yakalar ve kodunuzda yanıtlanması hakkında daha fazla bilgi için bkz: [deneyin... Catch... Finally deyimini](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="compile-time-errors"></a>Derleme zamanı hataları  
 Visual Basic Derleyicisi kodundaki bir sorunla karşılaşırsa, bir derleme zamanı hatası oluşur. Kod Düzenleyicisi'nde, hangi kod satırının Bu kod satırı altında dalgalı çizgi görünüyor hata nedeni kolayca belirleyebilirsiniz. Dalgalı çizgi veya açık ya da işaret ederseniz hata iletisi görüntülenir **hata listesi**, diğer iletiler de gösterilmektedir.  
  
 Dalgalı çizgi tanımlayıcının sahipse ve kısa çizgi en sağdaki karakter altında görünür, sınıf, oluşturucu, yöntemi, özelliği, alan veya sabit listesi için bir saplama oluşturabilirsiniz. Daha fazla bilgi için [kullanımından Oluştur](/visualstudio/ide/visual-csharp-intellisense#generate-from-usage).
  
 Visual Basic Derleyicisi gelen uyarılar çözümleyerek, daha hızlı çalışır ve daha az hata olan kod yazmayı mümkün olabilir. Bu uyarılar uygulamayı çalıştırdığınızda, hatalara neden olabilecek kodunu tanımlayın. Örneğin, derleyici, atanmamış nesne değişkeninin bir üyeyi çağıran denerseniz bir işlevden dönüş değeri ayarlamadan döndürür veya yürütme uyarır bir `Try` hatalarla mantığında özel durumları yakalama bloğu. Açma ve kapatma, devre dışı bırakma dahil olmak üzere uyarılar hakkında daha fazla bilgi için bkz. [Visual Basic'teki uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).
