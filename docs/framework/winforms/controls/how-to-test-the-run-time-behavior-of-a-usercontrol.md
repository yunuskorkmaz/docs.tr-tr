---
title: "Nasıl yapılır: bir UserControl 'un çalışma zamanı davranışını test etme"
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
ms.openlocfilehash: 110036e5031a2956375b1edf0689237661522d39
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72180200"
---
# <a name="how-to-test-the-run-time-behavior-of-a-usercontrol"></a>Nasıl yapılır: bir UserControl 'un çalışma zamanı davranışını test etme

@No__t-0 geliştirdiğinizde, çalışma zamanı davranışını test etmeniz gerekir. Ayrı bir Windows tabanlı uygulama projesi oluşturabilir ve denetiminizi bir test formuna yerleştirebilirsiniz, ancak bu yordam uygun değildir. Visual Studio tarafından sunulan **UserControl Test kapsayıcısını** daha hızlı ve kolay bir şekilde kullanmaktır. Bu test kapsayıcısı doğrudan Windows Denetim Kitaplığı projenizden başlatılır.

> [!IMPORTANT]
> @No__t-0 ' ı yüklemek için test kapsayıcısı için, denetimin en az bir ortak Oluşturucusu olmalıdır.

> [!NOTE]
> Görsel C++ denetim, **UserControl Test kapsayıcısı**kullanılarak test edilemez.

## <a name="test-the-run-time-behavior-of-a-usercontrol"></a>UserControl 'un çalışma zamanı davranışını test etme

1. Visual Studio 'da bir Windows Denetim Kitaplığı projesi oluşturun ve **TestContainerExample**olarak adlandırın.

2. **Windows Form Tasarımcısı**, bir <xref:System.Windows.Forms.Label> denetimini **araç kutusundan** denetimin tasarım yüzeyine sürükleyin.

3. Projeyi derlemek ve **UserControl Test kapsayıcısını**çalıştırmak için <kbd>F5</kbd> tuşuna basın. Test kapsayıcısı, **Önizleme** bölmesinde <xref:System.Windows.Forms.UserControl> ile görünür.

4. **Önizleme** bölmesinin sağında <xref:System.Windows.Forms.PropertyGrid> denetiminde görüntülenecek <xref:System.Windows.Forms.Control.BackColor%2A> özelliğini seçin. Değerini **Controlkoyu**olarak değiştirin. Denetimin daha koyu bir renge değiştiğini gözlemleyin. Diğer özellik değerlerini değiştirmeyi deneyin ve denetiminizin etkisini gözlemleyin.

5. **Önizleme** bölmesinin altındaki **Kullanıcı denetimine dolguyu yerleştir** onay kutusunu tıklatın. Bölmeyi dolduracak şekilde denetimin yeniden boyutlandırıldığını gözlemleyin. Test kapsayıcısını yeniden boyutlandırın ve denetimin bölme ile yeniden boyutlandırıldığını gözlemleyin.

6. Test kapsayıcısını kapatın.

7. **TestContainerExample** projesine başka bir kullanıcı denetimi ekleyin.

8. **Windows Form Tasarımcısı**, bir <xref:System.Windows.Forms.Button> denetimini **araç kutusundan** denetimin tasarım yüzeyine sürükleyin.

9. Projeyi derlemek ve test kapsayıcısını çalıştırmak için <kbd>F5</kbd> tuşuna basın.

10. İki kullanıcı denetimi arasında geçiş yapmak için @no__t **Kullanıcı denetimini Seç** -1 ' e tıklayın.

## <a name="test-user-controls-from-another-project"></a>Başka bir projeden kullanıcı denetimlerini test etme

Kullanıcı denetimlerini, geçerli projenizin test kapsayıcısındaki diğer projelerden test edebilirsiniz.

1. Visual Studio 'da bir Windows Denetim Kitaplığı projesi oluşturun ve **TestContainerExample2**olarak adlandırın.

2. **Windows Form Tasarımcısı**, bir <xref:System.Windows.Forms.RadioButton> denetimini **araç kutusundan** denetimin tasarım yüzeyine sürükleyin.

3. Projeyi derlemek ve test kapsayıcısını çalıştırmak için <kbd>F5</kbd> tuşuna basın. Test kapsayıcısı, **Önizleme** bölmesinde <xref:System.Windows.Forms.UserControl> ile görünür.

4. **Yükle** düğmesine tıklayın.

5. **Aç** iletişim kutusunda, önceki yordamda oluşturduğunuz *TestContainerExample. dll*' ye gidin. *TestContainerExample. dll* ' yi seçin ve **Aç** düğmesine tıklayarak Kullanıcı denetimlerini yükleyin.

6. **TestContainerExample** projesinden Iki kullanıcı denetimi arasında geçiş yapmak Için **kullanıcı denetimini Seç** <xref:System.Windows.Forms.ComboBox> ' i kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.UserControl>
- [Nasıl yapılır: bileşik denetimler yazma](how-to-author-composite-controls.md)
- [İzlenecek yol: bileşik denetim yazma](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
- [Kullanıcı denetimi Tasarımcısı](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))
