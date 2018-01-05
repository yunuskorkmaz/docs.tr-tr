---
title: "Nasıl yapılır: Değiştiricileri ve GenerateMember Özelliklerini Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
f1_keywords:
- Designer_GenerateMember
- Designer_Modifiers
helpviewer_keywords:
- base forms
- inheritance [Windows Forms], forms
- inherited forms [Windows Forms], Windows Forms
- inherited forms
- form inheritance
- Windows Forms, inheritance
ms.assetid: 3381a5e4-e1a3-44e2-a765-a0b758937b85
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f524bab55527bf9d3c744cb6f50d1df1fc9a2302
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-modifiers-and-generatemember-properties"></a>Nasıl yapılır: Değiştiricileri ve GenerateMember Özelliklerini Kullanma
Bir Windows formunda bir bileşen yerleştirdiğinizde, iki özellik tasarım ortamı tarafından sağlanan: `GenerateMember` ve `Modifiers`. `GenerateMember` Özelliği, Windows Form Tasarımcısı bileşeni için bir üye değişkenine oluşturduğunda belirtir. `Modifiers` Bu üye değişkenine atanan erişim değiştiricisi bir özelliktir. Varsa değerini `GenerateMember` özelliği `false`, değeri `Modifiers` özelliğinin hiçbir etkisi.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-specify-whether-a-component-is-a-member-of-the-form"></a>Bir bileşenin formun üyesi olup olmadığını belirtmek için  
  
1.  Windows Forms Tasarımcısı'nda formunuz açın.  
  
2.  Açık **araç**ve form üzerinde üç yerleştirin <xref:System.Windows.Forms.Button> kontrol eder.  
  
3.  Ayarlama `GenerateMember` ve `Modifiers` özellikleri her <xref:System.Windows.Forms.Button> denetimi aşağıdaki tabloya göre.  
  
    |Düğme adı|GenerateMember değeri|Değiştiriciler değeri|  
    |-----------------|--------------------------|---------------------|  
    |`button1`|`true`|`private`|  
    |`button2`|`true`|`protected`|  
    |`button3`|`false`|Değişiklik yok|  
  
4.  Çözümü oluşturun.  
  
5.  İçinde **Çözüm Gezgini**, tıklatın **tüm dosyaları göster** düğmesi.  
  
6.  Açık **Form1** düğümünü ve **Kod Düzenleyicisi**açın **Form1.Designer.vb** veya **Form1.Designer.cs** dosya. Bu dosyayı Windows Form Tasarımcısı tarafından gösterilen kodunu içerir.  
  
7.  Üç düğme için bildirimleri bulun. Aşağıdaki kod örneği tarafından belirtilen farklar gösterilmektedir `GenerateMember` ve `Modifiers` özellikleri.  
  
     [!code-csharp[System.Windows.Forms.GenerateMember#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.GenerateMember#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/VB/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.GenerateMember#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.GenerateMember#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/VB/Form1.vb#2)]  
  
> [!NOTE]
>  Varsayılan olarak, Windows Form Tasarımcısı atar `private` (`Friend` Visual Basic'te) kapsayıcı denetimleri gibi değiştiriciyi <xref:System.Windows.Forms.Panel>. Varsa tabanınızı <xref:System.Windows.Forms.UserControl> veya <xref:System.Windows.Forms.Form> bir kapsayıcı denetiminin devralınan denetimleri ve formlar yeni alt kabul etmez. Çözüm için temel kapsayıcı denetiminin değiştiricisi değiştirmektir `protected` veya `public`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Button>  
 [Windows Forms Görsel Devralma](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)  
 [İzlenecek Yol: Görsel Devralmayı Gösterme](../../../../docs/framework/winforms/advanced/walkthrough-demonstrating-visual-inheritance.md)  
 [Nasıl yapılır: Windows Forms’u Devralma](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)
