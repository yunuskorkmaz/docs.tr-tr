---
title: 'Nasıl yapılır: Basit Bir Windows Forms Denetimi Geliştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms]
- custom controls [Windows Forms], creating simple controls using code
- Control class [Windows Forms], Windows Forms
ms.assetid: 86cbe435-45b7-4cb4-9b5a-47418369758d
ms.openlocfilehash: a190d86f5ebe258427ac4a73c16c7f271462b69c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64753231"
---
# <a name="how-to-develop-a-simple-windows-forms-control"></a>Nasıl yapılır: Basit Bir Windows Forms Denetimi Geliştirme

Bu bölümde özel bir Windows Forms denetimi geliştirme için anahtar adımlarında size kılavuzluk eder. Bu izlenecek yolda geliştirilmiş basit denetimin hizalamasını izin kendi <xref:System.Windows.Forms.Control.Text%2A> özelliği değiştirilecek. Yükseltme değil veya olaylarını işleme.

### <a name="to-create-a-simple-custom-control"></a>Basit bir özel denetim oluşturmak için

1. Türetilen bir sınıf tanımlama <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.

    ```vb
    Public Class FirstControl
       Inherits Control

    End Class
    ```

    ```csharp
    public class FirstControl:Control {}
    ```

2. Özelliklerini tanımlayın. (Bir denetim birçok özellikleri devraldığından özelliklerini tanımlamak gerekmez <xref:System.Windows.Forms.Control> sınıfı, ancak çoğu özel denetimler genellikle ek özellikleri tanımlar.) Aşağıdaki kod parçası adlı bir özellik tanımlar `TextAlignment` , `FirstControl` görüntülenmesini biçimlendirmek için kullandığı <xref:System.Windows.Forms.Control.Text%2A> özelliği öğesinden devralınan <xref:System.Windows.Forms.Control>. Özellikleri tanımlama hakkında daha fazla bilgi için bkz. [özelliklerine genel bakış](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v%3dvs.120)).

     [!code-csharp[System.Windows.Forms.FirstControl#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#3)]
     [!code-vb[System.Windows.Forms.FirstControl#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#3)]

     Denetimin görsel görünümünü değiştirir bir özelliği ayarlamak, çağırmalıdır <xref:System.Windows.Forms.Control.Invalidate%2A> denetimi yeniden çizmek için yöntemi. <xref:System.Windows.Forms.Control.Invalidate%2A> temel sınıfta tanımlanan <xref:System.Windows.Forms.Control>.

3. Geçersiz kılma korumalı <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi öğesinden devralınan <xref:System.Windows.Forms.Control> denetiminiz için işleme mantığı sağlamak için. Geçersiz olursa <xref:System.Windows.Forms.Control.OnPaint%2A>, Denetim kendisini çizmek mümkün olmayacaktır. Aşağıdaki kod parçası, <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi görüntüler <xref:System.Windows.Forms.Control.Text%2A> özelliği öğesinden devralınan <xref:System.Windows.Forms.Control> tarafından belirtilen hizalama ile `alignmentValue` alan.

     [!code-csharp[System.Windows.Forms.FirstControl#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#4)]
     [!code-vb[System.Windows.Forms.FirstControl#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#4)]

4. Öznitelikler için denetim sağlar. Öznitelikler, tasarım zamanında denetiminizi ve özellikleri ve olayları uygun şekilde görüntülemek bir görsel tasarımcı sağlar. Aşağıdaki kod parçası özniteliklere uygulanır `TextAlignment` özelliği. Visual Studio gibi bir tasarımcıda <xref:System.ComponentModel.CategoryAttribute.Category%2A> özniteliği (kod parçasında gösterilen) bir mantıksal kategorisi altında görüntülenecek özelliği neden olur. <xref:System.ComponentModel.DescriptionAttribute.Description%2A> Öznitelik neden olur, alt kısmında görüntülenmesi açıklayıcı bir dize **özellikleri** penceresi zaman `TextAlignment` özellik seçildiğinde. Öznitelikler hakkında daha fazla bilgi için bkz. [bileşenler için tasarım zamanı öznitelikleri](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120)).

     [!code-csharp[System.Windows.Forms.FirstControl#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#5)]
     [!code-vb[System.Windows.Forms.FirstControl#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#5)]

5. (isteğe bağlı) Kaynaklar için denetim sağlar. Derleyici seçeneğini kullanarak denetlemek için bir bit eşlem gibi bir kaynak sağlayabilir (`/res` için C#) ile denetiminizi paket kaynaklarına. Çalışma zamanında, kaynak yöntemleri kullanılarak alınabilir <xref:System.Resources.ResourceManager> sınıfı. Oluşturma ve kaynakları kullanma hakkında daha fazla bilgi için bkz. [masaüstü uygulamalarında kaynakların](../../resources/index.md).

6. Derleme ve denetim dağıtın. Derlemek ve dağıtmak için `FirstControl,` aşağıdaki adımları uygulayın:

    1. Aşağıdaki örnek bir kaynak dosyasına (örneğin, FirstControl.cs veya FirstControl.vb) kod kaydedin.

    2. Kaynak kodu bir araya derlemek ve uygulamanızın dizine kaydedin. Bunu yapmak için kaynak dosyasını içeren dizinden aşağıdaki komutu yürütün.

        ```console
        vbc -t:library -out:[path to your application's directory]/CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll FirstControl.vb
        ```

        ```console
        csc -t:library -out:[path to your application's directory]/CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll FirstControl.cs
        ```

         `/t:library` Derleyici seçeneği derleyici oluşturduğunuz derleme bir kitaplık (ve çalıştırılabilir değil) olduğunu söyler. `/out` Seçeneği derlemenin adını ve yolunu belirtir. `/r` Seçeneği, kodunuz tarafından başvurulan bir derleme adı sağlar. Bu örnekte, yalnızca uygulamalarınızı kullanabileceğiniz özel bir derleme oluşturun. Bu nedenle, uygulamanızın dizininde kaydetmek sahip. Paketleme ve dağıtım için bir denetim dağıtma hakkında daha fazla bilgi için bkz. [dağıtım](../../deployment/index.md).

Aşağıdaki örnek kodu gösterilir `FirstControl`. Denetimin ad alanı içinde alınmış `CustomWinControls`. Bir ad alanı, ilişkili mantıksal bir gruplandırmasını sağlar. Yeni veya mevcut bir ad alanındaki denetim oluşturabilirsiniz. C# ' ta, `using` bildirimi (Visual Basic'te `Imports`) türünün tam adını kullanarak olmadan bir ad alanından erişilecek türlerine izin verir. Aşağıdaki örnekte, `using` bildirimi sağlar sınıfını erişmek için kod <xref:System.Windows.Forms.Control> gelen <xref:System.Windows.Forms?displayProperty=nameWithType> basit <xref:System.Windows.Forms.Control> tam adı kullanmak zorunda olmak yerine <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.

[!code-csharp[System.Windows.Forms.FirstControl#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#1)]
[!code-vb[System.Windows.Forms.FirstControl#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#1)]

## <a name="using-the-custom-control-on-a-form"></a>Formda özel denetim kullanarak

Aşağıdaki örnek, kullanan basit bir form gösterir `FirstControl`. Üç örneklerini oluşturur `FirstControl`, her biri için farklı bir değerle `TextAlignment` özelliği.

#### <a name="to-compile-and-run-this-sample"></a>Derlemek ve bu örneği çalıştırmak için

1. Kodu aşağıdaki örnekte bir kaynak dosyasına (SimpleForm.cs veya SimpleForms.vb) kaydedin.

2. Kaynak kodu, yürütülebilir bir derlemeye kaynak dosyasını içeren dizinden aşağıdaki komutu yürüterek derleyin.

    ```console
    vbc -r:CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll SimpleForm.vb
    ```

    ```console
    csc -r:CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll SimpleForm.cs
    ```

     CustomWinControls.dll olan sınıfı içeren derlemeyi `FirstControl`. Bu derleme (SimpleForm.cs veya SimpleForms.vb) eriştiği formu için kaynak dosyayla aynı dizinde olmalıdır.

3. Aşağıdaki komutu kullanarak SimpleForm.exe yürütün.

    ```console
    SimpleForm
    ```

[!code-csharp[System.Windows.Forms.FirstControl#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/SimpleForm.cs#10)]
[!code-vb[System.Windows.Forms.FirstControl#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/SimpleForm.vb#10)]

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms Denetimlerindeki Özellikler](properties-in-windows-forms-controls.md)
- [Windows Forms Denetimlerindeki Olaylar](events-in-windows-forms-controls.md)
