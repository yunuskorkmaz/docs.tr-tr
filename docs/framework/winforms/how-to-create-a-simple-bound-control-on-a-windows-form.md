---
title: 'Nasıl yapılır: Windows Forms’ta Basit Bağlantılı Denetim Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [Windows Forms], simple data binding
- Windows Forms controls, data binding
ms.assetid: 3bcaded8-0f1a-4cc0-8830-f59be253bf4e
ms.openlocfilehash: ed1d0e423a3cdf77a242ec3214720f1466f65897
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039502"
---
# <a name="how-to-create-a-simple-bound-control-on-a-windows-form"></a>Nasıl yapılır: Windows Forms’ta Basit Bağlantılı Denetim Oluşturma

*Basit bağlama*sayesinde, bir denetim içinde bir veri kümesi tablosundan sütun değeri gibi tek bir veri öğesi görüntüleyebilirsiniz. Bir denetimin herhangi bir özelliğini bir veri değerine basit bir şekilde bağlayabilirsiniz.

### <a name="to-simple-bind-a-control"></a>Bir denetimi basit bağlamak için

1. Bir veri kaynağına bağlanın. Daha fazla bilgi için bkz. [veri kaynağına bağlanma](../data/adonet/connecting-to-a-data-source.md).

2. Formunda, denetimi seçin ve **Özellikler** penceresini görüntüleyin.

3. **(DataBindings)** özelliğini genişletin.

     En sık ciltleyen Özellikler **(DataBindings)** özelliğinin altında görüntülenir. Örneğin, çoğu denetimin **metin** özelliği en sık bağlanır.

4. Bağlamak istediğiniz özellik, yaygın olarak bağlanan özelliklerden biri değilse, **(Gelişmiş)** kutusunda![](./media/how-to-create-a-simple-bound-control-on-a-windows-form/visual-studio-ellipsis-button.png) **bulunan üç nokta düğmesine (Visual Studio Özellikler penceresi) (...) tıklayın. Biçimlendirme ve Gelişmiş bağlama** iletişim kutusu, bu denetimin özelliklerinin tamamı listesi.

5. Bağlamak istediğiniz özelliği seçin ve **bağlama**bölümündeki aşağı açılan oka tıklayın.

     Kullanılabilir veri kaynaklarının bir listesi görüntülenir.

6. İstediğiniz tek veri öğesini buluncaya kadar bağlamak istediğiniz veri kaynağını genişletin. Örneğin, bir veri kümesinin tablosundaki bir sütun değerine bağlıyorsanız, veri kümesinin adını genişletin ve ardından sütun adlarını göstermek için tablo adını genişletin.

7. Bağlanacak öğenin adına tıklayın.

8. **Biçimlendirme ve Gelişmiş bağlama** iletişim kutusunda çalışıyorsanız, **Özellikler** penceresine dönmek için **Tamam** ' ı tıklatın.

9. Denetimin ek özelliklerini bağlamak istiyorsanız 3 ile 7 arasındaki adımları yineleyin.

    > [!NOTE]
    > Basit-bağlantılı denetimler yalnızca tek bir veri öğesi gösterebildiğinden, basit bağlantılı denetimlerle bir Windows formuna gezinme mantığını eklemek çok normaldir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Binding>
- [Windows Forms Veri Bağlama](windows-forms-data-binding.md)
- [Veri Bağlama ve Windows Forms](data-binding-and-windows-forms.md)
