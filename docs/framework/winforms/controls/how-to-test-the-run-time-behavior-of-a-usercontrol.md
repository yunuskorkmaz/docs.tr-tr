---
title: 'Nasıl yapılır: Bir UserControl Denetiminin Çalışma Zamanı Davranışını Sınama'
ms.date: 03/30/2017
helpviewer_keywords:
- UserControl class [Windows Forms], testing
- user controls [Windows Forms], testing
- composite controls [Windows Forms], testing
- UserControl Test Container
- UserControl class [Windows Forms], run-time behavior
ms.assetid: 4e4d5c49-1346-40ac-9d96-40211b573583
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1be79d52be3b5b84938d8548a8f101e965fa9dbb
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015773"
---
# <a name="how-to-test-the-run-time-behavior-of-a-usercontrol"></a>Nasıl yapılır: UserControl 'un çalışma zamanı davranışını test etme

Bir <xref:System.Windows.Forms.UserControl>geliştirirken, çalışma zamanı davranışını test etmeniz gerekir. Ayrı bir Windows tabanlı uygulama projesi oluşturabilir ve denetiminizi bir test formuna yerleştirebilirsiniz, ancak bu yordam uygun değildir. Visual Studio tarafından sunulan **UserControl Test kapsayıcısını** daha hızlı ve kolay bir şekilde kullanmaktır. Bu test kapsayıcısı doğrudan Windows Denetim Kitaplığı projenizden başlatılır.

> [!IMPORTANT]
> Test kapsayıcısının <xref:System.Windows.Forms.UserControl>' yi yüklemesi için, denetimin en az bir ortak Oluşturucusu olmalıdır.

> [!NOTE]
> Görsel C++ denetim, **UserControl Test kapsayıcısı**kullanılarak test edilemez.

## <a name="test-the-run-time-behavior-of-a-usercontrol"></a>UserControl 'un çalışma zamanı davranışını test etme

1. Visual Studio 'da bir Windows Denetim Kitaplığı projesi oluşturun ve **TestContainerExample**olarak adlandırın.

2. **Windows Form Tasarımcısı**, bir <xref:System.Windows.Forms.Label> denetimi **araç kutusundan** denetimin tasarım yüzeyine sürükleyin.

3. Projeyi derlemek ve **UserControl Test kapsayıcısını**çalıştırmak için **F5** tuşuna basın. Test kapsayıcısı, **Önizleme** bölmesinde ile <xref:System.Windows.Forms.UserControl> görüntülenir.

4. **Önizleme bölmesinin** sağındaki <xref:System.Windows.Forms.PropertyGrid> denetimde görüntülenecek özelliğiseçin.<xref:System.Windows.Forms.Control.BackColor%2A> Değerini **Controlkoyu**olarak değiştirin. Denetimin daha koyu bir renge değiştiğini gözlemleyin. Diğer özellik değerlerini değiştirmeyi deneyin ve denetiminizin etkisini gözlemleyin.

5. **Önizleme** bölmesinin altındaki **Kullanıcı denetimine dolguyu yerleştir** onay kutusunu tıklatın. Bölmeyi dolduracak şekilde denetimin yeniden boyutlandırıldığını gözlemleyin. Test kapsayıcısını yeniden boyutlandırın ve denetimin bölme ile yeniden boyutlandırıldığını gözlemleyin.

6. Test kapsayıcısını kapatın.

7. **TestContainerExample** projesine başka bir kullanıcı denetimi ekleyin.

8. **Windows Form Tasarımcısı**, bir <xref:System.Windows.Forms.Button> denetimi **araç kutusundan** denetimin tasarım yüzeyine sürükleyin.

9. Projeyi derlemek ve test kapsayıcısını çalıştırmak için **F5** tuşuna basın.

10. İki kullanıcı denetimi arasında geçiş yapmak için **Kullanıcı denetimini** <xref:System.Windows.Forms.ComboBox> Seç ' e tıklayın.

## <a name="test-user-controls-from-another-project"></a>Başka bir projeden kullanıcı denetimlerini test etme

Kullanıcı denetimlerini, geçerli projenizin test kapsayıcısındaki diğer projelerden test edebilirsiniz.

1. Visual Studio 'da bir Windows Denetim Kitaplığı projesi oluşturun ve **TestContainerExample2**olarak adlandırın.

2. **Windows Form Tasarımcısı**, bir <xref:System.Windows.Forms.RadioButton> denetimi **araç kutusundan** denetimin tasarım yüzeyine sürükleyin.

3. Projeyi derlemek ve test kapsayıcısını çalıştırmak için **F5** tuşuna basın. Test kapsayıcısı, **Önizleme** bölmesinde ile <xref:System.Windows.Forms.UserControl> görüntülenir.

4. **Yükle** düğmesine tıklayın.

5. **Aç** iletişim kutusunda, önceki yordamda oluşturduğunuz **TestContainerExample**. dll ' ye gidin. **TestContainerExample**. dll ' yi seçin ve **Aç** düğmesine tıklayarak Kullanıcı denetimlerini yükleyin

6. **TestContainerExample** projesinden iki kullanıcı denetimi arasında geçiş yapmak için **Kullanıcı Seç denetimini** <xref:System.Windows.Forms.ComboBox> kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.UserControl>
- [Nasıl yapılır: Bileşik denetimleri yaz](how-to-author-composite-controls.md)
- [İzlenecek yol: Bileşik denetim yazma](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
- [Kullanıcı denetimi Tasarımcısı](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))
