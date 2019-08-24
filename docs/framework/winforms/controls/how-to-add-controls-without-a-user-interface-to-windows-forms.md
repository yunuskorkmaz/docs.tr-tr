---
title: 'Nasıl yapılır: Windows Forms’a Kullanıcı Arabirimi Olmadan Denetimler Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- NonVisualSelection
helpviewer_keywords:
- invisible controls [Windows Forms]
- Windows Forms controls, adding to form
- controls [Windows Forms], nonvisual
- Windows Forms controls, nonvisual
- nonvisual controls [Windows Forms]
ms.assetid: 52134d9c-cff6-4eed-8e2b-3d5eb3bd494e
ms.openlocfilehash: bc1f844e5a2cf4d4f3b64ebf20e935f36ff85e12
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987108"
---
# <a name="how-to-add-controls-without-a-user-interface-to-windows-forms"></a>Nasıl yapılır: Windows Forms’a Kullanıcı Arabirimi Olmadan Denetimler Ekleme

Görsel olmayan bir denetim (veya bileşen) uygulamanıza işlevsellik sağlar. Diğer denetimlerin aksine, bileşenler kullanıcıya Kullanıcı arabirimi sağlamamalıdır ve bu nedenle Windows Form Tasarımcısı yüzeyinde gösterilmemelidir. Forma bir bileşen eklendiğinde Windows Form Tasarımcısı, tüm bileşenlerin görüntülendiği formun alt kısmına yeniden boyutlandırılabilir bir tepsi görüntüler. Bileşen tepsisine bir denetim eklendikten sonra, bileşeni seçebilir ve form üzerindeki diğer denetimleri yaptığınız gibi özelliklerini ayarlayabilirsiniz.

## <a name="add-a-component-to-a-windows-form"></a>Windows formuna bir bileşen ekleme

1. Formu Visual Studio 'da açın. Ayrıntılar için bkz [. nasıl yapılır: Tasarımcıda](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100))Windows Forms görüntüleyin.

2. **Araç kutusunda**bir bileşene tıklayın ve onu formunuza sürükleyin.

     Bileşeniniz bileşen tepsisinde görünür.

Ayrıca, bileşenler çalışma zamanında bir forma eklenebilir. Bu yaygın bir senaryodur, özellikle de bileşenler görsel bir ifade olmadığından, Kullanıcı arabirimine sahip denetimlerin aksine. Aşağıdaki örnekte, çalışma zamanında bir <xref:System.Windows.Forms.Timer> bileşen eklenir. (Visual Studio 'nun bir dizi farklı Zamanlayıcı içerdiğini unutmayın; bu durumda bir Windows Forms <xref:System.Windows.Forms.Timer> bileşeni kullanın. Visual Studio 'daki farklı zamanlayıcılar hakkında daha fazla bilgi için bkz. [sunucu tabanlı zamanlayıcılara giriş](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).)

> [!CAUTION]
> Bileşenlere genellikle bileşenin etkin bir şekilde çalışması için ayarlanması gereken denetimine özgü özellikler vardır. Aşağıdaki <xref:System.Windows.Forms.Timer> bileşen durumunda `Interval` özelliğini ayarlarsınız. Projenize bileşen eklerken, bu bileşen için gerekli özellikleri ayarlamış olduğunuzdan emin olun.

## <a name="add-a-component-to-a-windows-form-programmatically"></a>Windows formuna programlı bir bileşen ekleme

1. Kodda <xref:System.Windows.Forms.Timer> sınıfının bir örneğini oluşturun.

2. Süreölçerin zaman işaretleri arasındaki süreyi öğrenmek için özelliğiniayarlayın.`Interval`

3. Bileşeniniz için diğer tüm gerekli özellikleri yapılandırın.

     Aşağıdaki kod, bir <xref:System.Windows.Forms.Timer> öğesinin `Interval` özellik kümesi ile oluşturulmasını gösterir.

    ```vb
    Public Sub CreateTimer()
       Dim timerKeepTrack As New System.Windows.Forms.Timer
       timerKeepTrack.Interval = 1000
    End Sub
    ```

    ```csharp
    public void createTimer()
    {
       System.Windows.Forms.Timer timerKeepTrack = new
           System.Windows.Forms.Timer();
       timerKeepTrack.Interval = 1000;
    }
    ```

    ```cpp
    public:
       void createTimer()
       {
          System::Windows::Forms::Timer^ timerKeepTrack = gcnew
             System::Windows::Forms::Timer();
          timerKeepTrack->Interval = 1000;
       }
    ```

    > [!IMPORTANT]
    > Kötü amaçlı bir UserControl 'e başvurarak yerel bilgisayarınızı ağ üzerinden bir güvenlik riskine maruz kalabilirsiniz. Bu durum yalnızca zararlı bir kişinin zararlı bir denetim oluşturan bir sorun olduğu ve bunu projenize yanlışlıkla ekleyerek bir sorun olacaktır.

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms Denetimleri](index.md)
- [Nasıl yapılır: Windows Forms denetim ekleme](how-to-add-controls-to-windows-forms.md)
- [Nasıl yapılır: Windows Forms için ActiveX denetimleri ekleme](how-to-add-activex-controls-to-windows-forms.md)
- [Windows Forms’a Denetimler Yerleştirme](putting-controls-on-windows-forms.md)
- [Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Windows Forms'da Kullanılacak Denetimler](controls-to-use-on-windows-forms.md)
- [İşleve Göre Windows Forms Denetimleri](windows-forms-controls-by-function.md)
