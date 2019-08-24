---
title: 'Nasıl yapılır: Bağlantılı Denetim Oluşturma ve Görüntülenen Verileri Biçimlendirme'
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], formatting
- bound controls [Windows Forms], creating
- bound controls [Windows Forms], formatting data
ms.assetid: d5a56228-899d-41d9-8af8-87b3f4ec2f94
ms.openlocfilehash: 543775894994c518d6069f697b145cedaa7af5b0
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015658"
---
# <a name="how-to-create-a-bound-control-and-format-the-displayed-data"></a>Nasıl yapılır: Bağlantılı Denetim Oluşturma ve Görüntülenen Verileri Biçimlendirme

Windows Forms veri bağlama ile, **biçimlendirme ve Gelişmiş bağlama** iletişim kutusunu kullanarak veriye dayalı bir denetimde görünen verileri biçimlendirebilirsiniz.

## <a name="to-bind-a-control-and-format-the-displayed-data"></a>Bir denetimi bağlamak ve görüntülenecek verileri biçimlendirmek için

1. Bir veri kaynağına bağlanın. Daha fazla bilgi için bkz. [veri kaynağına bağlanma](../data/adonet/connecting-to-a-data-source.md).

2. Visual Studio 'da formdaki denetimi seçin ve ardından **Özellikler** penceresini açın.

3. **(DataBindings)** özelliğini genişletin ve **(Gelişmiş)** kutusunda,![biçimlendirmeyi ve Gelişmiş ' i göstermek için üç nokta düğmesini (Visual Studio](./media/how-to-create-a-bound-control-and-format-the-displayed-data/visual-studio-ellipsis-button.png)'nun Özellikler penceresi üç nokta düğmesini (...) tıklatın.Bu denetim için özelliklerin tamamen bir listesini içeren bağlama iletişim kutusu.

4. Bağlamak istediğiniz özelliği seçin ve sonra **bağlama** okunu seçin.

     Kullanılabilir veri kaynaklarının bir listesi görüntülenir.

5. İstediğiniz tek veri öğesini buluncaya kadar bağlamak istediğiniz veri kaynağını genişletin.

     Örneğin, bir veri kümesinin tablosundaki bir sütun değerine bağlıyorsanız, veri kümesinin adını genişletin ve ardından sütun adlarını göstermek için tablo adını genişletin.

6. Bağlanacak öğenin adını seçin.

7. **Biçim türü** kutusunda, denetimde görüntülenecek verilere uygulamak istediğiniz biçimi seçin.

     Her durumda, veri kaynağı içeriyorsa <xref:System.DBNull>denetimde gösterilecek değeri belirtebilirsiniz. Aksi takdirde, Seçenekler, seçtiğiniz biçim türüne bağlı olarak biraz farklılık gösterir. Aşağıdaki tabloda biçim türleri ve seçenekleri gösterilmektedir.

    |Biçim türü|Biçimlendirme seçeneği|
    |-----------------|-----------------------|
    |Biçimlendirme yok|Seçenek yok.|
    |Numeric|Ondalık basamak sayısını artırma-azaltma denetimini kullanarak belirtin.|
    |Para Birimi|Ondalık basamak sayısını artırma-azaltma denetimini kullanarak belirtin.|
    |Tarih saat|**Tür** seçim kutusundaki öğelerden birini seçerek tarih ve saatin nasıl görüntüleneceğini seçin.|
    |Bilimsel|Ondalık basamak sayısını artırma-azaltma denetimini kullanarak belirtin.|
    |Özel|Kullanarak bir özel biçim dizesi belirtin.<br /><br /> Daha fazla bilgi için bkz. [biçimlendirme türleri](../../standard/base-types/formatting-types.md). **Not:**  Özel biçim dizelerinin, veri kaynağı ve bağlantılı denetim arasında başarılı bir şekilde gidiş dönüş garantisi yoktur. Bunun yerine bağlama <xref:System.Windows.Forms.Binding.Parse> için <xref:System.Windows.Forms.Binding.Format> veya olayını işleyin ve olay işleme kodunda özel biçimlendirme uygulayın.|

8. **Biçimlendirme ve Gelişmiş bağlama** iletişim kutusunu kapatmak ve Özellikler penceresi geri dönmek için **Tamam** ' ı seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Bir Windows formunda basit bağlantılı denetim oluşturma](how-to-create-a-simple-bound-control-on-a-windows-form.md)
- [Windows Forms'ta Kullanıcı Girdisi Doğrulama](user-input-validation-in-windows-forms.md)
- [Windows Forms Veri Bağlama](windows-forms-data-binding.md)
