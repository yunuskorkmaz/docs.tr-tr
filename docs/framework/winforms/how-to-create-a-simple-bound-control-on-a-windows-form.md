---
title: 'Nasıl yapılır: Windows Forms’ta Basit Bağlantılı Denetim Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [Windows Forms], simple data binding
- Windows Forms controls, data binding
ms.assetid: 3bcaded8-0f1a-4cc0-8830-f59be253bf4e
ms.openlocfilehash: 79b31e61f4c7739a20765c9484db6a8cfd04b01b
ms.sourcegitcommit: 11deacc8ec9f229ab8ee3cd537515d4c2826515f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2019
ms.locfileid: "66003767"
---
# <a name="how-to-create-a-simple-bound-control-on-a-windows-form"></a>Nasıl yapılır: Windows Forms’ta Basit Bağlantılı Denetim Oluşturma
İle *basit bağlama*, tek bir veri öğesi, bir veri kümesi tablodaki bir sütun değeri gibi bir denetimi görüntüleme. Basit bir denetimin herhangi bir özelliği bir veri değerine bağlamak.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-simple-bind-a-control"></a>Basit-bağlama bir denetim için  
  
1. Bir veri kaynağına bağlanın. Daha fazla bilgi için [bir veri kaynağına bağlanma](../data/adonet/connecting-to-a-data-source.md).  
  
2. Form denetimi seçin ve görüntüleme **özellikleri** penceresi.  
  
3. Genişletin **(DataBindings)** özelliği.  
  
     Çoğunlukla ilişkili özellikleri altında görüntülenen **(DataBindings)** özelliği. Örneğin, çoğu denetim, **metin** özelliği sık bağlı.  
  
4.  İstediğiniz özelliğin bağlama yaygın olarak bağlı özelliklerden biri değil, tıklayın **üç nokta** düğmesine (![Visual Studio Özellikler penceresinde üç nokta düğmesini (…)](./media/how-to-create-a-simple-bound-control-on-a-windows-form/visual-studio-ellipsis-button.png)) içinde **( Gelişmiş)** görüntülemek için kutusu **biçimlendirme ve Gelişmiş bağlama** bu denetim için özelliklerin tam bir liste ile iletişim kutusu.  
  
5. Altındaki aşağı açılan oka tıklayın ve bağlamak istediğiniz özelliği seçin **bağlama**.  
  
     Kullanılabilir veri kaynaklarının bir listesi görüntülenir.  
  
6. İstediğiniz tek veri öğesi bulana kadar bağlamak istediğiniz veri kaynağını genişletin. Örneğin, bir veri kümesi tablodaki bir sütun değerine bağlanıyorsanız, veri kümesinin adını genişletin ve ardından sütun adlarını görüntülemek için tablo adını genişletin.  
  
7. Bağlanılacak bir öğe adına tıklayın.  
  
8. Üzerinde çalıştığınız varsa **biçimlendirme ve Gelişmiş bağlama** iletişim kutusu, tıklayın **Tamam** dönmek için **özellikleri** penceresi.  
  
9. Denetimin ek özellikleri bağlamak istiyorsanız, 3 ila 7. adımları tekrarlayın.  
  
    > [!NOTE]
    >  Basit veriye bağlı denetimler yalnızca bir tek veri öğesi göstermek için bir Windows formunda basit bağlantılı denetim ile gezinti mantığı içeren çok normaldir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Binding>
- [Windows Forms Veri Bağlama](windows-forms-data-binding.md)
- [Veri Bağlama ve Windows Forms](data-binding-and-windows-forms.md)
