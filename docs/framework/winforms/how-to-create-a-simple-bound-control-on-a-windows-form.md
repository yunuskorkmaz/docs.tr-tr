---
title: 'Nasıl yapılır: Bir Windows Formunda Basit Bağlantılı Denetim Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [Windows Forms], simple data binding
- Windows Forms controls, data binding
ms.assetid: 3bcaded8-0f1a-4cc0-8830-f59be253bf4e
ms.openlocfilehash: 26bc136ea2b7e5bda4a57c5dad65ec3522efcd3d
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43258727"
---
# <a name="how-to-create-a-simple-bound-control-on-a-windows-form"></a>Nasıl yapılır: Bir Windows Formunda Basit Bağlantılı Denetim Oluşturma
İle *basit bağlama*, tek bir veri öğesi, bir veri kümesi tablodaki bir sütun değeri gibi bir denetimi görüntüleme. Basit bir denetimin herhangi bir özelliği bir veri değerine bağlamak.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-simple-bind-a-control"></a>Basit-bağlama bir denetim için  
  
1.  Bir veri kaynağına bağlanın. Daha fazla bilgi için [bir veri kaynağına bağlanma](../../../docs/framework/data/adonet/connecting-to-a-data-source.md).  
  
2.  Form denetimi seçin ve görüntüleme **özellikleri** penceresi.  
  
3.  Genişletin **(DataBindings)** özelliği.  
  
     Çoğunlukla ilişkili özellikleri altında görüntülenen **(DataBindings)** özelliği. Örneğin, çoğu denetim, **metin** özelliği sık bağlı.  
  
4.  İstediğiniz özelliğin bağlama yaygın olarak bağlı özelliklerden biri değil, tıklayın **üç nokta** düğmesine (![VisualStudioEllipsesButton ekran](../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton") ) içinde **(Gelişmiş)** görüntülemek için kutusu **biçimlendirme ve Gelişmiş bağlama** bu denetim için özelliklerin tam bir liste ile iletişim kutusu.  
  
5.  Altındaki aşağı açılan oka tıklayın ve bağlamak istediğiniz özelliği seçin **bağlama**.  
  
     Kullanılabilir veri kaynaklarının bir listesi görüntülenir.  
  
6.  İstediğiniz tek veri öğesi bulana kadar bağlamak istediğiniz veri kaynağını genişletin. Örneğin, bir veri kümesi tablodaki bir sütun değerine bağlanıyorsanız, veri kümesinin adını genişletin ve ardından sütun adlarını görüntülemek için tablo adını genişletin.  
  
7.  Bağlanılacak bir öğe adına tıklayın.  
  
8.  Üzerinde çalıştığınız varsa **biçimlendirme ve Gelişmiş bağlama** iletişim kutusu, tıklayın **Tamam** dönmek için **özellikleri** penceresi.  
  
9. Denetimin ek özellikleri bağlamak istiyorsanız, 3 ila 7. adımları tekrarlayın.  
  
    > [!NOTE]
    >  Basit veriye bağlı denetimler yalnızca bir tek veri öğesi göstermek için bir Windows formunda basit bağlantılı denetim ile gezinti mantığı içeren çok normaldir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Binding>  
 [Windows Forms Veri Bağlama](../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Veri Bağlama ve Windows Forms](../../../docs/framework/winforms/data-binding-and-windows-forms.md)
