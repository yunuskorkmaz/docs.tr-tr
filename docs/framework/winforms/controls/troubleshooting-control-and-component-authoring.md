---
title: Denetim ve Bileşen Yazmada Sorun Giderme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- troubleshooting components
- troubleshooting controls [Windows Forms]
- controls [Windows Forms], troubleshooting
- components [Windows Forms], troubleshooting
- Windows Forms controls, debugging
ms.assetid: e9c8c099-2271-4737-882f-50f336c7a55e
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9ee9df41e6f0a4e37164760a2e40740e31530121
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459066"
---
# <a name="troubleshoot-control-and-component-authoring"></a>Denetim ve Bileşen Yazmada Sorun Giderme

Bu konuda, bileşenleri ve denetimleri geliştirirken ortaya çıkan aşağıdaki yaygın sorunlar listelenmektedir:

- Araç kutusu 'na denetim eklenemiyor

- Windows Forms Kullanıcı denetiminde veya bileşende hata ayıklaması yapılamıyor

- Devralınan denetimde veya bileşende olay Iki kez getirilir

- Tasarım zamanı hatası: "' ' bileşen*adı*'" bileşeni oluşturulamadı

- STAThreadAttribute

- Bileşen simgesi araç kutusunda görünmüyor

## <a name="cannot-add-control-to-toolbox"></a>Araç kutusu 'na denetim eklenemiyor

**Araç kutusu**için başka bir projede veya üçüncü taraf denetiminde oluşturduğunuz özel bir denetim eklemek istiyorsanız, bunu el ile yapmanız gerekir. Geçerli proje denetim veya bileşeninizi içeriyorsa **araç kutusunda** otomatik olarak görünmelidir. Daha fazla bilgi için bkz. [Izlenecek yol: araç kutusunu özel bileşenlerle otomatik olarak doldurma](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).

### <a name="to-add-a-control-to-the-toolbox"></a>Araç kutusuna denetim eklemek için

1. **Araç kutusuna** sağ tıklayıp kısayol menüsünden **öğeleri seç**' i seçin.

2. **Araç kutusu öğelerini Seç** iletişim kutusunda, bileşeni ekleyin:

    - .NET Framework bir bileşen veya denetim eklemek istiyorsanız, **.NET Framework bileşenleri** sekmesine tıklayın.

         veya

    - COM bileşeni veya ActiveX denetimi eklemek istiyorsanız **com bileşenleri** sekmesine tıklayın.

3. Denetiminiz iletişim kutusunda listeleniyorsa, seçili olduğunu onaylayın ve ardından **Tamam**' a tıklayın.

     Denetim **araç kutusuna**eklenir.

4. Denetiminiz iletişim kutusunda listelenmiyorsa, şunları yapın:

    1. **Araştır** düğmesine tıklayın.

    2. Denetiminizi içeren. dll dosyasını içeren klasöre gidin.

    3. . Dll dosyasını seçin ve **Aç**' a tıklayın.

         Denetiminiz iletişim kutusunda görünür.

    4. Denetiminizin seçili olduğunu doğrulayın ve ardından **Tamam**' a tıklayın.

         Denetiminiz **araç kutusuna**eklenir.

## <a name="cannot-debug-the-windows-forms-user-control-or-component"></a>Windows Forms Kullanıcı denetiminde veya bileşende hata ayıklaması yapılamıyor

Denetiminiz <xref:System.Windows.Forms.UserControl> sınıfından türetildiğinden, çalışma zamanı davranışının test kapsayıcısı ile hata ayıklaması yapabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: bir UserControl 'un çalışma zamanı davranışını test etme](how-to-test-the-run-time-behavior-of-a-usercontrol.md).

Diğer özel denetimler ve bileşenler tek başına projeler değildir. Bunlar, Windows Forms projesi gibi bir uygulama tarafından barındırılmalıdır. Bir denetimin veya bileşenin hatalarını ayıklamak için bir Windows Forms projesine eklemeniz gerekir.

### <a name="to-debug-a-control-or-component"></a>Bir denetimin veya bileşenin hatalarını ayıklamak için

1. Çözümünüzü derlemek için **Build (derleme** ) menüsünde **çözüm oluştur** ' a tıklayın.

2. Uygulamanıza bir test projesi eklemek için **Dosya** menüsünden **Ekle**' yi ve ardından **Yeni proje** ' yi seçin.

3. **Yeni Proje Ekle** iletişim kutusunda proje türü Için **Windows uygulaması** ' nı seçin.

4. **Çözüm Gezgini**, yeni proje için **Başvurular** düğümüne sağ tıklayın. Denetim veya bileşen içeren projeye başvuru eklemek için kısayol menüsünde **Başvuru Ekle** ' ye tıklayın.

5. Test projesinde denetiminizin veya bileşeninizin bir örneğini oluşturun. Bileşeniniz **araç kutusunda**ise tasarımcı yüzeyine sürükleyebilirsiniz veya aşağıdaki kod örneğinde gösterildiği gibi örneği programlı bir şekilde oluşturabilirsiniz.

    ```vb
    Dim Component1 As New MyNeatComponent()
    ```

    ```csharp
    MyNeatComponent Component1 = new MyNeatComponent();
    ```

   Artık, denetim veya bileşeninizdeki hataları her zamanki gibi ayıklayabilirsiniz.

Hata ayıklama hakkında daha fazla bilgi için bkz. [Visual Studio 'Da hata ayıklama](/visualstudio/debugger/debugger-feature-tour) ve [Izlenecek yol: tasarım zamanında özel Windows Forms Denetimlerinde hata ayıklama](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).

## <a name="event-is-raised-twice-in-inherited-control-or-component"></a>Devralınan denetimde veya bileşende olay Iki kez getirilir

Bunun nedeni muhtemelen yinelenen bir `Handles` yan tümcesi olabilir. Daha fazla bilgi için bkz. [Visual Basic devralınan olay Işleyicilerinin sorunlarını giderme](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).

## <a name="design-time-error-failed-to-create-component-component-name"></a>Tasarım zamanı hatası: "' ' bileşen adı '" bileşeni oluşturulamadı

Bileşeninizin veya denetiminizin parametresiz bir Oluşturucu sağlaması gerekir. Tasarım ortamı, bileşeninizin veya denetiminizin bir örneğini oluşturduğunda, parametreleri alan Oluşturucu aşırı yüklerini parametre sağlamaya çalışmaz.

## <a name="stathreadattribute"></a>STAThreadAttribute

<xref:System.STAThreadAttribute>, Windows Forms tek iş parçacıklı grup modelini kullanan ortak dil çalışma zamanına (CLR) bildirir. Bu özniteliği Windows Forms uygulamanızın `Main` yöntemine uygulamadıysanız istenmeden bir davranış fark edebilirsiniz. Örneğin, arka plan görüntüleri <xref:System.Windows.Forms.ListView>gibi denetimler için görünmeyebilir. Bazı denetimler, doğru otomatik tamamlama ve sürükle ve bırak davranışı için de bu özniteliği gerektirebilir.

## <a name="component-icon-does-not-appear-in-toolbox"></a>Bileşen simgesi araç kutusunda görünmüyor

Özel bileşeninizdeki bir simgeyi ilişkilendirmek için <xref:System.Drawing.ToolboxBitmapAttribute> kullandığınızda, otomatik olarak oluşturulmuş bileşenler için araç kutusunda bit eşlem görünmez. Bit eşlemi görmek için **araç kutusu öğelerini Seç** iletişim kutusunu kullanarak denetimi yeniden yükleyin. Daha fazla bilgi için bkz. [nasıl yapılır: bir denetim Için araç kutusu bit eşlemi sağlama](how-to-provide-a-toolbox-bitmap-for-a-control.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Tasarım Zamanında Windows Forms Denetimleri Geliştirme](developing-windows-forms-controls-at-design-time.md)
- [İzlenecek yol: Araç Kutusunu Otomatik Olarak Özel Bileşenlerle Doldurma](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
- [Nasıl yapılır: Bir UserControl Denetiminin Çalışma Zamanı Davranışını Sınama](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
- [İzlenecek yol: Tasarım Zamanında Özel Windows Forms Denetimleri Hatalarını Ayıklama](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)
