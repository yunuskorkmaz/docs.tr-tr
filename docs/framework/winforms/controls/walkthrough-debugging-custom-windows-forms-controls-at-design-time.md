---
title: Tasarım zamanında özel denetimlerin hatalarını ayıklama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- debugging [Visual Studio], walkthroughs
- custom controls [Windows Forms], walkthroughs
- visual editors
- debugging [Visual Studio], Windows Forms
- custom controls [Windows Forms], debugging
- designers
- controls [Windows Forms], debugging
- walkthroughs [Windows Forms], debugging
- design-time debugging
ms.assetid: 1fd83ccd-3798-42fc-85a3-6cba99467387
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d9e292a1219c24571bcb35db2fe357b0197c8812
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740189"
---
# <a name="walkthrough-debug-custom-windows-forms-controls-at-design-time"></a>İzlenecek yol: tasarım zamanında özel Windows Forms Denetimlerinde hata ayıklama

Özel bir denetim oluşturduğunuzda, genellikle tasarım zamanı davranışından hata ayıklamanın gerekli olduğunu fark edersiniz. Özel denetiminiz için özel tasarımcı yazıyorsanız bu özellikle doğrudur. Ayrıntılar için bkz. [Izlenecek yol: Visual Studio tasarım zamanı özelliklerinden faydalanan Windows Forms denetimi oluşturma](creating-a-wf-control-design-time-features.md).

Visual Studio 'Yu kullanarak özel denetimlerde hata ayıklaması yapabilirsiniz, tıpkı diğer .NET Framework sınıflarında hata ayıklaması yapabilirsiniz. Fark, Visual Studio 'nun özel denetiminizin kodunu çalıştıran ayrı bir örneğinde hata ayıklamanın farkından oluşur.

## <a name="create-the-project"></a>Projeyi oluşturma

İlk adım uygulama projesini oluşturmaktır. Bu projeyi, özel denetimi barındıran uygulamayı oluşturmak için kullanacaksınız.

Visual Studio 'da bir Windows uygulama projesi oluşturun ve **DebuggingExample**olarak adlandırın.

## <a name="create-the-control-library-project"></a>Denetim kitaplığı projesi oluşturma

1. Çözüme bir **Windows Denetim Kitaplığı** projesi ekleyin.

2. DebugControlLibrary projesine yeni bir **UserControl** öğesi ekleyin. **DebugControl**olarak adlandırın.

3. **Çözüm Gezgini**, kod dosyasını UserControl1 temel adıyla silerek projenin varsayılan denetimini silin.

4. Çözümü oluşturun.

## <a name="checkpoint"></a>Checkpoint

Bu noktada, **araç kutusunda**özel denetiminizi görebileceksiniz.

İlerleme durumunu denetlemek için **DebugControlLibrary bileşenleri** adlı yeni sekmeyi bulun ve seçmek için tıklayın. Açıldığında, denetimizin, simgenin yanında **DebugControl** olarak listelendiğini göreceksiniz.

## <a name="add-a-property-to-your-custom-control"></a>Özel denetimi bir özellik ekleyin

Özel denetimizin kodunun tasarım zamanında çalıştığını göstermek için, özelliği uygulayan kodda bir özellik ekleyeceksiniz ve bir kesme noktası ayarlayacaksınız.

1. **Kod düzenleyicisinde** **DebugControl** ' i açın. Aşağıdaki kodu sınıf tanımına ekleyin:

    ```vb
    Private demoStringValue As String = Nothing
    <BrowsableAttribute(true)>
    Public Property DemoString() As String

        Get
            Return Me.demoStringValue
        End Get

        Set(ByVal value As String)
            Me.demoStringValue = value
        End Set

    End Property
    ```

    ```csharp
    private string demoStringValue = null;
    [Browsable(true)]
    public string DemoString
    {
        get
        {
            return this.demoStringValue;
        }
        set
        {
            demoStringValue = value;
        }
    }
    ```

2. Çözümü oluşturun.

## <a name="add-your-custom-control-to-the-host-form"></a>Özel denetiminizi ana bilgisayar formuna ekleme

Özel denetiminizin tasarım zamanı davranışının hatalarını ayıklamak için, bir ana bilgisayar formuna özel denetim sınıfının bir örneğini yerleştirebilirsiniz.

1. "DebuggingExample" projesinde, **Windows Form Tasarımcısı**Form1 ' i açın.

2. **Araç kutusunda** **DebugControlLibrary bileşenleri** sekmesini açın ve bir **DebugControl** örneğini form üzerine sürükleyin.

3. **Özellikler** penceresinde `DemoString` özel özelliğini bulun. Değerini diğer tüm özellikler gibi değiştirebileceğinizi unutmayın. Ayrıca, `DemoString` özelliği seçildiğinde özelliğin açıklama dizesinin **Özellikler** penceresinin altında göründüğünü unutmayın.

## <a name="set-up-the-project-for-design-time-debugging"></a>Projeyi tasarım zamanı hata ayıklama için ayarlama

Özel denetiminizin tasarım zamanı davranışınızda hata ayıklamak için, özel denetiminizin kodunu çalıştıran ayrı bir Visual Studio örneğinden hata ayıklayacaksınız.

1. **Çözüm Gezgini** **DebugControlLibrary** projesine sağ tıklayın ve **Özellikler**' i seçin.

2. **DebugControlLibrary** Özellik sayfasında, **Hata Ayıkla** sekmesini seçin.

     **Başlangıç eylemi** bölümünde **dış program Başlat**' ı seçin. Visual Studio 'nun ayrı bir örneğinde hata ayıkladığınızda, Visual Studio IDE 'ye gözatabilmek için üç nokta (Visual](./media/visual-studio-ellipsis-button.png)Studio 'nun Özellikler penceresi![) düğmesini tıklatın. Yürütülebilir dosyanın adı **devenv. exe**' dir ve varsayılan konuma yüklediyseniz, yolu *% ProgramFiles (x86)% \ Microsoft Visual studio\2019\\\<Edition > \Common7\IDE*olur.

3. İletişim kutusunu kapatmak için **Tamam ' ı** seçin.

4. **DebugControlLibrary** projesine sağ tıklayın ve bu hata ayıklama yapılandırmasını etkinleştirmek Için **Başlangıç projesi olarak ayarla** ' yı seçin.

## <a name="debug-your-custom-control-at-design-time"></a>Tasarım zamanında özel denetimi hata ayıklaması yapın

Artık tasarım modunda çalışırken özel denetimi hata ayıklamaya hazırsınız. Hata ayıklama oturumunu başlattığınızda, Visual Studio 'nun yeni bir örneği oluşturulur ve bunu "DebuggingExample" çözümünü yüklemek için kullanacaksınız. **Form tasarımcısında**Form1 ' i açtığınızda, özel denetiminizin bir örneği oluşturulur ve çalışmaya başlayacaktır.

1. **Kod düzenleyicisinde** **DebugControl** kaynak dosyasını açın ve `DemoString` özelliğinin `Set` erişimcisine bir kesme noktası yerleştirin.

2. Hata ayıklama oturumu başlatmak için **F5** tuşuna basın. Visual Studio 'nun yeni bir örneği oluşturulur. Örnekler arasında iki şekilde ayrım yapabilirsiniz:

    - Hata ayıklama örneği, başlık çubuğunda **çalışan** sözcüğe sahiptir

    - Hata ayıklama örneğinde **hata ayıklama** araç çubuğundaki **Başlat** düğmesi devre dışıdır

   Kesme noktası hata ayıklama örneğinde ayarlanır.

3. Visual Studio 'nun yeni örneğinde, "DebuggingExample" çözümünü açın. **Dosya** menüsünden **son projeler** ' i seçerek çözümü kolayca bulabilirsiniz. "DebuggingExample. sln" çözüm dosyası en son kullanılan dosya olarak listelenecektir.

4. **Form tasarımcısında** Form1 ' i açın ve **DebugControl** denetimini seçin.

5. `DemoString` özelliğinin değerini değiştirin. Değişikliği kaydettiğinizde, Visual Studio 'daki hata ayıklama örneği odak ve yürütme, kesme noktasında duraklar. Özellik erişimcisinde, tıpkı diğer kodlar gibi tek adım izleyebilirsiniz.

6. Hata ayıklamayı durdurmak için, Visual Studio 'nun barındırılan örneğinden çıkın veya hata ayıklama örneğindeki **hata ayıklamayı Durdur** düğmesini seçin.

## <a name="next-steps"></a>Sonraki adımlar

Tasarım zamanında özel denetimlerde hata ayıklayabildiğinize göre, Visual Studio IDE ile denetiminizin etkileşimini genişletmeye yönelik birçok olasılık vardır.

- Yalnızca tasarım zamanında yürütülecek kodu yazmak için <xref:System.ComponentModel.Component> sınıfının <xref:System.ComponentModel.Component.DesignMode%2A> özelliğini kullanabilirsiniz. Ayrıntılar için bkz. <xref:System.ComponentModel.Component.DesignMode%2A>.

- Özel denetiminizin, tasarımcı ile etkileşimini işlemek için denetiminizin özelliklerine uygulayabileceğiniz birkaç öznitelik vardır. Bu öznitelikleri <xref:System.ComponentModel?displayProperty=nameWithType> ad alanında bulabilirsiniz.

- Özel denetiminiz için özel tasarımcı yazabilirsiniz. Bu sayede, Visual Studio tarafından sunulan Genişletilebilir tasarımcı altyapısını kullanarak tasarım deneyimi üzerinde tüm denetim elde edersiniz. Ayrıntılar için bkz. [Izlenecek yol: Visual Studio tasarım zamanı özelliklerinden faydalanan Windows Forms denetimi oluşturma](creating-a-wf-control-design-time-features.md).

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: Visual Studio Tasarım-Zamanı Özellikleri'nden Faydalanan Windows Forms Denetimi Oluşturma](creating-a-wf-control-design-time-features.md)
