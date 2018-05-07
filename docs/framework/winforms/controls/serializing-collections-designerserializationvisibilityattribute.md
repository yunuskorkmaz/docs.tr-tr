---
title: 'İzlenecek yol: DesignerSerializationVisibilityAttribute ile Standart Türler Koleksiyonlarının Seri Hale Getirilmesi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- serialization [Windows Forms], collections
- standard types [Windows Forms], collections
- collections [Windows Forms], serializing
- collections [Windows Forms], standard types
ms.assetid: 020c9df4-fdc5-4dae-815a-963ecae5668c
ms.openlocfilehash: a502ecc30911f2296bf48eaa195f5b6452b7588a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-serializing-collections-of-standard-types-with-the-designerserializationvisibilityattribute"></a>İzlenecek yol: DesignerSerializationVisibilityAttribute ile Standart Türler Koleksiyonlarının Seri Hale Getirilmesi
Özel denetimler, bazen bir koleksiyon özelliği olarak açığa çıkarır. Bu kılavuzda nasıl kullanılacağı ortaya <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> koleksiyonu tasarım zamanında nasıl serileştirilmiş denetlemek için sınıf. Uygulama <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> koleksiyon özelliği için değer sağlar özelliği seri hale getirilir.  
  
 Bu konuda tek bir liste olarak kodu kopyalamak için bkz: [nasıl yapılır: seri hale koleksiyonları standart türleri DesignerSerializationVisibilityAttribute ile](http://msdn.microsoft.com/library/7829fcdd-8205-405f-8231-a1282a9835c9).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu kılavuzu tamamlamak için gerekir:  
  
-   Oluşturma ve Windows Forms uygulaması projeleri, Visual Studio yüklü olduğu bilgisayarda çalıştırmak için yeterli izinleri yok.  
  
## <a name="creating-a-control-that-has-a-serializable-collection"></a>Seri hale getirilebilir bir koleksiyonu olan bir denetimi oluşturma  
 İlk adım, bir özellik olarak serileştirilebilir bir koleksiyonu olan bir denetim oluşturmaktır. Bu koleksiyonu kullanarak içindekiler düzenleyebilirsiniz **Koleksiyonu Düzenleyicisi**, gelen erişebileceğiniz **özellikleri** penceresi.  
  
#### <a name="to-create-a-control-with-a-serializable-collection"></a>Bir denetim ile seri hale getirilebilir bir koleksiyon oluşturmak için  
  
1.  Adlı bir Windows Denetim Kitaplığı projesi oluşturun `SerializationDemoControlLib`. Daha fazla bilgi için bkz: [Windows Denetim Kitaplığı şablonu](http://msdn.microsoft.com/library/722f4e2d-1310-4ed5-8f33-593337ab66b4).  
  
2.  Yeniden Adlandır `UserControl1` için `SerializationDemoControl`. Daha fazla bilgi için bkz: [nasıl yapılır: yeniden adlandırma tanımlayıcıları](http://msdn.microsoft.com/library/2430f732-2b70-4516-8cf6-a7bb71cc9724).  
  
3.  İçinde **özellikleri** penceresindeki değerini ayarlayın <xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType> özelliğine `10`.  
  
4.  Yerine bir <xref:System.Windows.Forms.TextBox> denetim `SerializationDemoControl`.  
  
5.  Seçin <xref:System.Windows.Forms.TextBox> denetim. İçinde **özellikleri** penceresinde, aşağıdaki özellikleri ayarlayın.  
  
    |Özellik|Değiştirin|  
    |--------------|---------------|  
    |**Çok satırlı**|`true`|  
    |**Yerleştirme**|<xref:System.Windows.Forms.DockStyle.Fill>|  
    |**Kaydırma çubukları**|<xref:System.Windows.Forms.ScrollBars.Vertical>|  
    |**ReadOnly**|`true`|  
  
6.  İçinde **Kod düzenleyicisinde**, adında bir dize dizisi alan bildirin `stringsValue` içinde `SerializationDemoControl`.  
  
     [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#4)]
     [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#4)]
     [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#4)]  
  
7.  Tanımlamak `Strings` özelliği `SerializationDemoControl`.  
  
> [!NOTE]
>  <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> Koleksiyonunu serileştirmek etkinleştirmek için kullanılır.  
  
 [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#5)]
 [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#5)]
 [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#5)]  
  
1.  Projeyi derlemek ve denetiminizin çalıştırmak için F5 tuşuna basın **UserControl Test kapsayıcısı**.  
  
2.  Bul `Strings` özelliğinde <xref:System.Windows.Forms.PropertyGrid> , **UserControl Test kapsayıcısı**. Tıklatın `Strings` özelliği, üç nokta düğmesine (![VisualStudioEllipsesButton ekran](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) açmak için düğmeye **Dize Koleksiyonu Düzenleyicisi**.  
  
3.  Birkaç dizelerde girin **Dize Koleksiyonu Düzenleyicisi**. Bunları, her bir dizenin sonunda ENTER tuşuna basarak ayırın. Tıklatın **Tamam** dizeleri girmeyi tamamladığınızda.  
  
> [!NOTE]
>  Yazdığınız dizeleri görünür <xref:System.Windows.Forms.TextBox> , `SerializationDemoControl`.  
  
## <a name="serializing-a-collection-property"></a>Bir koleksiyon özelliği seri hale getirme  
 Seri hale getirme davranışını sınamak için bir form üzerinde yerleştirin ve koleksiyonuyla içeriğini değiştirme **Koleksiyonu Düzenleyicisi**. Seri hale getirilmiş toplama durumu bir özel Tasarımcı dosyasına, içine bakarak gördüğünüz **Windows Form Tasarımcısı** kod yayar.  
  
#### <a name="to-serialize-a-collection"></a>Bir koleksiyon seri hale getirmek için  
  
1.  Bir Windows uygulaması proje çözüme ekleyin. Proje adı `SerializationDemoControlTest`.  
  
2.  İçinde **araç**, adlı sekmesini bulmak **SerializationDemoControlLib bileşenleri**. Bu sekmede, bulacaksınız `SerializationDemoControl`. Daha fazla bilgi için bkz: [izlenecek yol: araç kutusunu özel bileşenlerle'otomatik olarak doldurma](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).  
  
3.  Yerine bir `SerializationDemoControl` formunuzda.  
  
4.  Bul `Strings` özelliğinde **özellikleri** penceresi. Tıklatın `Strings` özelliği, üç nokta düğmesine (![VisualStudioEllipsesButton ekran](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) açmak için düğmeye **Dize Koleksiyonu Düzenleyicisi**.  
  
5.  Birkaç dizelerde yazın **Dize Koleksiyonu Düzenleyicisi**. Bunları, her bir dizenin sonunda ENTER tuşuna basarak ayırın. Tıklatın **Tamam** dizeleri girmeyi tamamladığınızda.  
  
> [!NOTE]
>  Yazdığınız dizeleri görünür <xref:System.Windows.Forms.TextBox> , `SerializationDemoControl`.  
  
1.  İçinde **Çözüm Gezgini**, tıklatın **tüm dosyaları göster** düğmesi.  
  
2.  Açık **Form1** düğümü. Beneath adlı bir dosya olan **Form1.Designer.cs** veya **Form1.Designer.vb**. Bu dosyaya olan **Windows Form Tasarımcısı** formunuz ve onun alt denetimleri tasarım zamanı durumunu temsil eden kod yayar. Bu dosyayı açmak **Kod düzenleyicisinde**.  
  
3.  Adlı bölgesini açmak **Windows Form Tasarımcısı oluşturulan kod** ve etiketli bölüm Bul **serializationDemoControl1**. Bu etiket denetiminizin serileştirilmiş durumu temsil eden kodudur. 5. adımda yazılan dizelerde atama görünür `Strings` özelliği. Aşağıdaki kod C# ve Visual Basic örnekler kod dizeleri "red", "turuncu" ve "Sarı" yazılan yazısını görürsünüz benzer.  
  
    ```csharp  
    this.serializationDemoControl1.Strings = new string[] {  
            "red",  
            "orange",  
            "yellow"};  
    ```  
    
    ```vb  
    Me.serializationDemoControl1.Strings = New String() {"red", "orange", "yellow"}  
    ```
  
4.  İçinde **Kod düzenleyicisinde**, değerini değiştirme <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> üzerinde `Strings` özelliğine <xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>.  
  
    ```csharp  
    [DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)]  
    ```  
    ```vb  
    <DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)> _  
    ```  
  
5. 3. ve 4 adımları yineleyin ve çözümü yeniden derleyin.  
  
> [!NOTE]
>  Bu durumda, **Windows Form Tasarımcısı** hiçbir atamaya yayar `Strings` özelliği.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Standart Türler koleksiyonunu serileştirmek nasıl öğrendikten sonra özel denetimler daha derine tasarım zamanı ortamına tümleştirme göz önünde bulundurun. Aşağıdaki konular, özel denetimler tasarım zamanı tümleştirilmesi geliştirmek açıklanmaktadır:  
  
-   [Tasarım zamanı mimarisi](http://msdn.microsoft.com/library/4881917b-628f-4689-b872-472e4f8a4e3a)  
  
-   [Windows Forms Denetimlerindeki Öznitelikler](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
  
-   [Tasarımcı serileştirme genel bakış](http://msdn.microsoft.com/library/c342635a-aa5f-4281-915b-b013738af15a)  
  
-   [İzlenecek yol: Visual Studio Tasarım-Zamanı Özellikleri'nden Faydalanan Windows Forms Denetimi Oluşturma](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>  
 [Tasarımcı serileştirme genel bakış](http://msdn.microsoft.com/library/c342635a-aa5f-4281-915b-b013738af15a)  
 [Nasıl yapılır: DesignerSerializationVisibilityAttribute ile standart türler koleksiyonlarının seri hale](http://msdn.microsoft.com/library/7829fcdd-8205-405f-8231-a1282a9835c9)  
 [İzlenecek yol: Araç Kutusunu Otomatik Olarak Özel Bileşenlerle Doldurma](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
