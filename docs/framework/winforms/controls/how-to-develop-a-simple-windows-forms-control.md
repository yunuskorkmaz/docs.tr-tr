---
title: Basit denetim geliştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms]
- custom controls [Windows Forms], creating simple controls using code
- Control class [Windows Forms], Windows Forms
ms.assetid: 86cbe435-45b7-4cb4-9b5a-47418369758d
ms.openlocfilehash: 5383cee5358dbd260fc6c023d3db607da6b10ea4
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742261"
---
# <a name="how-to-develop-a-simple-windows-forms-control"></a>Nasıl yapılır: Basit Bir Windows Forms Denetimi Geliştirme

Bu bölümde, özel bir Windows Forms denetimi yazmak için temel adımlarda izlenecek yol gösterilmektedir. Bu izlenecek yolda geliştirilen basit denetim <xref:System.Windows.Forms.Control.Text%2A> özelliğinin hizalanmasına izin verir. Olayları oluşturmaz veya işlemez.

### <a name="to-create-a-simple-custom-control"></a>Basit bir özel denetim oluşturmak için

1. <xref:System.Windows.Forms.Control?displayProperty=nameWithType>türeten bir sınıf tanımlayın.

    ```vb
    Public Class FirstControl
       Inherits Control

    End Class
    ```

    ```csharp
    public class FirstControl:Control {}
    ```

2. Özellikleri tanımlayın. (Bir denetim <xref:System.Windows.Forms.Control> sınıfından birçok özelliği devraldığından, ancak çoğu özel denetim genellikle ek özellikler tanımlayacağından, özellikleri tanımlamanız gerekmez.) Aşağıdaki kod parçası, <xref:System.Windows.Forms.Control>devralınmış <xref:System.Windows.Forms.Control.Text%2A> özelliğinin görüntülenmesini biçimlendirmek için `FirstControl` tarafından kullanılan `TextAlignment` adlı bir özelliği tanımlar. Özellikleri tanımlama hakkında daha fazla bilgi için bkz. [özelliklere genel bakış](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v%3dvs.120)).

     [!code-csharp[System.Windows.Forms.FirstControl#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#3)]
     [!code-vb[System.Windows.Forms.FirstControl#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#3)]

     Denetimin görsel görüntüsünü değiştiren bir özelliği ayarladığınızda, denetimi yeniden çizmek için <xref:System.Windows.Forms.Control.Invalidate%2A> yöntemini çağırmanız gerekir. <xref:System.Windows.Forms.Control.Invalidate%2A>, temel sınıfta <xref:System.Windows.Forms.Control>tanımlanır.

3. Denetiminizin işleme mantığını sağlamak için <xref:System.Windows.Forms.Control> devralınmış korunan <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemini geçersiz kılın. <xref:System.Windows.Forms.Control.OnPaint%2A>geçersiz kılamazsınız, denetiminiz kendisini çizmeyecektir. Aşağıdaki kod parçasında <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi, `alignmentValue` alanı tarafından belirtilen hizalamayla <xref:System.Windows.Forms.Control> devralınan <xref:System.Windows.Forms.Control.Text%2A> özelliğini görüntüler.

     [!code-csharp[System.Windows.Forms.FirstControl#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#4)]
     [!code-vb[System.Windows.Forms.FirstControl#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#4)]

4. Denetiminizin özniteliklerini sağlayın. Öznitelikler görsel tasarımcı 'nın, tasarım zamanında denetiminizi ve özelliklerini ve olaylarını uygun şekilde görüntülemesini sağlar. Aşağıdaki kod parçası, `TextAlignment` özelliğine öznitelikler uygular. Visual Studio gibi bir tasarımcıda <xref:System.ComponentModel.CategoryAttribute.Category%2A> özniteliği (kod parçasında gösterilmektedir) özelliğin bir mantıksal kategori altında görüntülenmesine neden olur. <xref:System.ComponentModel.DescriptionAttribute.Description%2A> özniteliği, `TextAlignment` özelliği seçildiğinde **Özellikler** penceresinin alt kısmında açıklayıcı bir dizenin görüntülenmesine neden olur. Öznitelikler hakkında daha fazla bilgi için bkz. [Bileşenler Için tasarım zamanı öznitelikleri](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120)).

     [!code-csharp[System.Windows.Forms.FirstControl#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#5)]
     [!code-vb[System.Windows.Forms.FirstControl#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#5)]

5. seçim Denetiminizin kaynaklarını sağlayın. Denetim için bir derleyici seçeneği (`/res` için C#) kullanarak denetim için bit eşlem gibi bir kaynak sağlayabilirsiniz. Çalışma zamanında, kaynak <xref:System.Resources.ResourceManager> sınıfının yöntemleri kullanılarak alınabilir. Kaynakları oluşturma ve kullanma hakkında daha fazla bilgi için, bkz. [Masaüstü uygulamalarındaki kaynaklar](../../resources/index.md).

6. Denetiminizi derleyin ve dağıtın. Derlemek ve dağıtmak için `FirstControl,` aşağıdaki adımları yürütün:

    1. Aşağıdaki örnekteki kodu bir kaynak dosyasına kaydedin (örneğin, FirstControl.cs veya FirstControl. vb).

    2. Kaynak kodu bir derlemede derleyin ve uygulamanızın dizinine kaydedin. Bunu gerçekleştirmek için, kaynak dosyayı içeren dizinden aşağıdaki komutu yürütün.

        ```console
        vbc -t:library -out:[path to your application's directory]/CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll FirstControl.vb
        ```

        ```console
        csc -t:library -out:[path to your application's directory]/CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll FirstControl.cs
        ```

         `/t:library` derleyici seçeneği derleyiciye oluşturmakta olduğunuz derlemenin bir kitaplık (yürütülebilir değil) olduğunu söyler. `/out` seçeneği, derlemenin yolunu ve adını belirtir. `/r` seçeneği, kodunuzun başvurduğu derlemelerin adını sağlar. Bu örnekte, yalnızca uygulamalarınızın kullanabileceği özel bir derleme oluşturursunuz. Bu nedenle, uygulamayı uygulamanızın dizinine kaydetmelisiniz. Dağıtım için bir denetim paketleme ve dağıtma hakkında daha fazla bilgi için bkz. [dağıtım](../../deployment/index.md).

Aşağıdaki örnekte `FirstControl`kodu gösterilmektedir. Denetim ad alanı `CustomWinControls`alınmıştır. Bir ad alanı ilgili türlerin mantıksal bir gruplandırmasını sağlar. Denetiminizi yeni veya mevcut bir ad alanında oluşturabilirsiniz. ' C#De `using` bildirimine (Visual Basic, `Imports`), türün tam adı kullanılmadan bir ad alanından erişilmesine izin verir. Aşağıdaki örnekte `using` bildirimi, kodun, <xref:System.Windows.Forms.Control?displayProperty=nameWithType>tam adı kullanmak yerine <xref:System.Windows.Forms.Control> <xref:System.Windows.Forms?displayProperty=nameWithType> <xref:System.Windows.Forms.Control> sınıfına erişmesini sağlar.

[!code-csharp[System.Windows.Forms.FirstControl#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#1)]
[!code-vb[System.Windows.Forms.FirstControl#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#1)]

## <a name="using-the-custom-control-on-a-form"></a>Bir form üzerinde özel denetimi kullanma

Aşağıdaki örnekte `FirstControl`kullanan basit bir form gösterilmektedir. Her biri `TextAlignment` özelliği için farklı bir değere sahip `FirstControl`üç örneğini oluşturur.

#### <a name="to-compile-and-run-this-sample"></a>Bu örneği derlemek ve çalıştırmak için

1. Aşağıdaki örnekteki kodu bir kaynak dosyasına (SimpleForm.cs veya SimpleForms. vb) kaydedin.

2. Kaynak dosyayı içeren dizinden aşağıdaki komutu yürüterek, kaynak kodu yürütülebilir bir derlemede derleyin.

    ```console
    vbc -r:CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll SimpleForm.vb
    ```

    ```console
    csc -r:CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll SimpleForm.cs
    ```

     CustomWinControls. dll, `FirstControl`sınıfını içeren derlemedir. Bu derleme, kendisine erişen form için kaynak dosyayla aynı dizinde olmalıdır (SimpleForm.cs veya SimpleForms. vb).

3. Aşağıdaki komutu kullanarak SimpleForm. exe ' yi yürütün.

    ```console
    SimpleForm
    ```

[!code-csharp[System.Windows.Forms.FirstControl#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/SimpleForm.cs#10)]
[!code-vb[System.Windows.Forms.FirstControl#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/SimpleForm.vb#10)]

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms Denetimlerindeki Özellikler](properties-in-windows-forms-controls.md)
- [Windows Forms Denetimlerindeki Olaylar](events-in-windows-forms-controls.md)
