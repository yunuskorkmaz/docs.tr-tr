---
title: 'Nasıl yapılır: Değiştiricileri ve GenerateMember Özelliklerini Kullanma'
ms.date: 03/30/2017
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
ms.openlocfilehash: 6194ef288bd43267c2b00fa6d7c6250e90b37c75
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778865"
---
# <a name="how-to-use-the-modifiers-and-generatemember-properties"></a>Nasıl yapılır: Değiştiricileri ve GenerateMember Özelliklerini Kullanma
Bir Windows formunda bir bileşen yerleştirdiğinizde, iki özellik tasarım ortamı tarafından sağlanan: `GenerateMember` ve `Modifiers`. `GenerateMember` Özellik belirtir, Windows Form Tasarımcısı ' bileşeni için bir üye değişkeni oluşturur. `Modifiers` Özelliğidir, bu üye değişkenine atanan erişim değiştiricisi. Varsa değerini `GenerateMember` özelliği `false`, değerini `Modifiers` özelliğinin hiçbir etkisi.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-specify-whether-a-component-is-a-member-of-the-form"></a>Bir bileşen form üyesi olup olmadığını belirlemek için  
  
1. Windows Form Tasarımcısı'nda formunuza açın.  
  
2. Açık **araç kutusu**ve üç form üzerinde yerleştirmek <xref:System.Windows.Forms.Button> kontrol eder.  
  
3. Ayarlama `GenerateMember` ve `Modifiers` özellikleri her <xref:System.Windows.Forms.Button> aşağıdaki tabloya göre denetimi.  
  
    |Düğme adı|GenerateMember değeri|Değiştiriciler değeri|  
    |-----------------|--------------------------|---------------------|  
    |`button1`|`true`|`private`|  
    |`button2`|`true`|`protected`|  
    |`button3`|`false`|Değişiklik yok|  
  
4. Çözümü oluşturun.  
  
5. İçinde **Çözüm Gezgini**, tıklayın **tüm dosyaları göster** düğmesi.  
  
6. Açık **Form1** düğümünü ve **Kod Düzenleyicisi**açın **Form1.Designer.vb** veya **Form1.Designer.cs** dosya. Bu dosya Windows Forms Tasarımcısı tarafından yayılan kod içerir.  
  
7. Üç düğme için bildirimler bulun. Aşağıdaki kod örneği tarafından belirtilen farklar gösterilmektedir `GenerateMember` ve `Modifiers` özellikleri.  
  
     [!code-csharp[System.Windows.Forms.GenerateMember#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.GenerateMember#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/VB/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.GenerateMember#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.GenerateMember#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/VB/Form1.vb#2)]  
  
> [!NOTE]
>  Varsayılan olarak, Windows Form Tasarımcısı atar `private` (`Friend` Visual Basic) değiştirici gibi kapsayıcı denetimlere <xref:System.Windows.Forms.Panel>. Varsa tabanınızı <xref:System.Windows.Forms.UserControl> veya <xref:System.Windows.Forms.Form> bir kapsayıcı denetimi sahip devralınan denetimler ve formları yeni alt öğe kabul etmez. Temel bir kapsayıcı denetimin değiştiricisini çözümüdür `protected` veya `public`.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Button>
- [Windows Forms Görsel Devralma](windows-forms-visual-inheritance.md)
- [İzlenecek yol: Görsel devralmayı gösterme](walkthrough-demonstrating-visual-inheritance.md)
- [Nasıl yapılır: Windows Form devralma](how-to-inherit-windows-forms.md)
