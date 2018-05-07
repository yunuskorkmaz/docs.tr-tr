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
ms.openlocfilehash: 04cedc0df60ef95acb79b651ddcbcbb34ae5e920
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-develop-a-simple-windows-forms-control"></a>Nasıl yapılır: Basit Bir Windows Forms Denetimi Geliştirme
Bu bölüm, özel bir Windows Forms denetimi geliştirme için önemli adımlar anlatılmaktadır. Bu kılavuzda geliştirilmiş basit denetim hizalamasını sağlar, <xref:System.Windows.Forms.Control.Text%2A> değiştirilecek özelliği. Yükseltme değil veya olayları işlemek.  
  
### <a name="to-create-a-simple-custom-control"></a>Basit bir özel denetim oluşturmak için  
  
1.  Türeyen bir sınıf tanımlama <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.  
  
    ```vb  
    Public Class FirstControl  
       Inherits Control  
  
    End Class  
    ```  
  
    ```csharp  
    public class FirstControl:Control{}  
    ```  
  
2.  Özellikleri tanımlayın. (Bir denetim birçok özelliklerinden devralındığından özelliklerini tanımlamak gerekmez <xref:System.Windows.Forms.Control> sınıfı, ancak çoğu özel denetimler genellikle ek özellikleri tanımlar.) Aşağıdaki kod parçası adlı bir özelliğini tanımlar `TextAlignment` , `FirstControl` görüntüsünü biçimlendirmek için kullandığı <xref:System.Windows.Forms.Control.Text%2A> özelliği devralınan <xref:System.Windows.Forms.Control>. Özellikleri tanımlama hakkında daha fazla bilgi için bkz: [özelliklerine genel bakış](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52).  
  
     [!code-csharp[System.Windows.Forms.FirstControl#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#3)]
     [!code-vb[System.Windows.Forms.FirstControl#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#3)]  
  
     Denetim görsel görünümünü değiştirir bir özellik ayarladığınızda, çağırmanız gerekir <xref:System.Windows.Forms.Control.Invalidate%2A> denetimi yeniden boyutlandırmaya yöntemi. <xref:System.Windows.Forms.Control.Invalidate%2A> taban sınıf içinde tanımlanan <xref:System.Windows.Forms.Control>.  
  
3.  Korumalı geçersiz kılma <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi devralınan <xref:System.Windows.Forms.Control> denetim işleme mantığı sağlamak için. Değil geçersiz kılarsanız <xref:System.Windows.Forms.Control.OnPaint%2A>, denetiminizi kendisini çizmek mümkün olmaz. Aşağıdaki kod parçası olarak <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi görüntüler <xref:System.Windows.Forms.Control.Text%2A> özelliği devralınan <xref:System.Windows.Forms.Control> tarafından belirtilen hizalama ile `alignmentValue` alan.  
  
     [!code-csharp[System.Windows.Forms.FirstControl#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#4)]
     [!code-vb[System.Windows.Forms.FirstControl#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#4)]  
  
4.  Öznitelikler için denetim sağlar. Öznitelikleri tasarım zamanında denetiminizi ve özellikleri ve olayları uygun şekilde görüntülemek bir görsel tasarımcı etkinleştirin. Aşağıdaki kod parçası özniteliklere uygulanır `TextAlignment` özelliği. Visual Studio gibi bir Tasarımcısı'nda <xref:System.ComponentModel.CategoryAttribute.Category%2A> (kod parçasında gösterilen) öznitelik mantıksal kategorisi altında görüntülenecek özelliği neden olur. <xref:System.ComponentModel.DescriptionAttribute.Description%2A> Özniteliği neden olur. alt kısmındaki görüntülenecek tanımlayıcı bir dize **özellikleri** penceresi zaman `TextAlignment` özelliği seçilidir. Öznitelikler hakkında daha fazla bilgi için bkz: [bileşenleri için tasarım zamanı öznitelikleri](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3).  
  
     [!code-csharp[System.Windows.Forms.FirstControl#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#5)]
     [!code-vb[System.Windows.Forms.FirstControl#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#5)]  
  
5.  (isteğe bağlı) Kaynaklar için denetim sağlar. Derleyici seçeneği kullanarak denetlemek için bir bit eşlem gibi bir kaynak sağlayın (`/res` için C#), Denetim ile paket kaynaklarına. Çalışma zamanında kaynak yöntemleri kullanılarak alınabilir <xref:System.Resources.ResourceManager> sınıfı. Oluşturma ve kaynakları kullanma hakkında daha fazla bilgi için bkz: [masaüstü uygulamalarında kaynakları](../../../../docs/framework/resources/index.md).  
  
6.  Derleme ve denetiminizin dağıtın. Derleme ve dağıtmak için `FirstControl,` aşağıdaki adımları yürütün:  
  
    1.  Bir kaynak dosyaya (örneğin, FirstControl.cs veya FirstControl.vb) aşağıdaki örnekteki kod kaydedin.  
  
    2.  Bir derlemeye kaynak kodu derleme ve uygulamanızın dizinine kaydedin. Bunu başarmak için kaynak dosyasını içeren dizininden aşağıdaki komutu yürütün.  
  
        ```console  
        vbc -t:library -out:[path to your application's directory]/CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll FirstControl.vb  
        ```  
  
        ```console 
        csc -t:library -out:[path to your application's directory]/CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll FirstControl.cs  
        ```  
  
         `/t:library` Derleyici seçeneği derleyici oluşturmakta derleme kitaplık (ve bir yürütülebilir) olduğunu bildirir. `/out` Seçeneği derlemenin adını ve yolunu belirtir. `/r` Seçeneği kodunuz tarafından başvurulan bir derleme adı sağlar. Bu örnekte, yalnızca uygulamalarınızı kullanabileceğiniz özel bir derlemesi oluşturun. Bu nedenle, uygulamanızın dizininde kaydetmeniz gerekir. Paketleme ve dağıtım için bir denetim dağıtma hakkında daha fazla bilgi için bkz: [dağıtım](../../../../docs/framework/deployment/index.md).  
  
 Aşağıdaki örnek kodunu gösterir `FirstControl`. Ad alanında denetimi içine `CustomWinControls`. Bir ad alanı, ilgili türleri mantıksal bir gruplandırmasını sağlar. Yeni veya var olan bir ad alanında denetiminizi oluşturabilirsiniz. C# ' ta, `using` bildirimi (Visual Basic'te `Imports`) türünün tam adını kullanmadan bir ad alanından erişilecek türlerine izin verir. Aşağıdaki örnekte, `using` bildirimi sınıfa erişmek kod sağlar <xref:System.Windows.Forms.Control> gelen <xref:System.Windows.Forms?displayProperty=nameWithType> basit <xref:System.Windows.Forms.Control> tam adı kullanmak zorunda olmak yerine <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.  
  
 [!code-csharp[System.Windows.Forms.FirstControl#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#1)]
 [!code-vb[System.Windows.Forms.FirstControl#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#1)]  
  
## <a name="using-the-custom-control-on-a-form"></a>Bir Form üzerinde özel denetimi kullanma  
 Aşağıdaki örnekte kullanan basit bir form gösterilmektedir `FirstControl`. Üç örneklerini oluşturur `FirstControl`, her biri için farklı bir değer `TextAlignment` özelliği.  
  
#### <a name="to-compile-and-run-this-sample"></a>Derlemek ve bu örneği çalıştırmak için  
  
1.  Aşağıdaki örnekte bir kaynak dosyasının (SimpleForm.cs veya SimpleForms.vb) kodunu kaydedin.  
  
2.  Kaynak kodu kaynak dosyasını içeren dizininden aşağıdaki komutu çalıştırarak yürütülebilir bir derlemeye derleyin.  
  
    ```console  
    vbc -r:CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll SimpleForm.vb  
    ```  
  
    ```console 
    csc -r:CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll SimpleForm.cs  
    ```  
  
     CustomWinControls.dll olan sınıfı içeren bütünleştirilmiş kodun `FirstControl`. Bu derleme (SimpleForm.cs veya SimpleForms.vb) eriştiği form için kaynak dosyası ile aynı dizinde olmalıdır.  
  
3.  Aşağıdaki komutu kullanarak SimpleForm.exe yürütün.  
  
    ```console
    SimpleForm  
    ```  
  
 [!code-csharp[System.Windows.Forms.FirstControl#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/SimpleForm.cs#10)]
 [!code-vb[System.Windows.Forms.FirstControl#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/SimpleForm.vb#10)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Forms Denetimlerindeki Özellikler](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 [Windows Forms Denetimlerindeki Olaylar](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)
