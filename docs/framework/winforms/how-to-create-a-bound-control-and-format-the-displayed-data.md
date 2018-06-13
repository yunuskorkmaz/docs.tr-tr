---
title: 'Nasıl yapılır: Bağlantılı Denetim Oluşturma ve Görüntülenen Verileri Biçimlendirme'
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], formatting
- bound controls [Windows Forms], creating
- bound controls [Windows Forms], formatting data
ms.assetid: d5a56228-899d-41d9-8af8-87b3f4ec2f94
ms.openlocfilehash: 9055ec9c4b646e0c86819e4e72db8ce20086bace
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33542216"
---
# <a name="how-to-create-a-bound-control-and-format-the-displayed-data"></a>Nasıl yapılır: Bağlantılı Denetim Oluşturma ve Görüntülenen Verileri Biçimlendirme
Windows Forms veri bağlama ile kullanarak bir veri bağlama denetiminde gösterilen veriler biçimlendirebilirsiniz **biçimlendirme ve Gelişmiş bağlama** iletişim kutusu.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-bind-a-control-and-format-the-displayed-data"></a>Bir denetimi bağlamak ve görüntülenen verileri biçimlendirme  
  
1.  Bir veri kaynağına bağlanın.  
  
     Daha fazla bilgi için bkz: [bir veri kaynağına bağlanma](../../../docs/framework/data/adonet/connecting-to-a-data-source.md).  
  
2.  Form denetimi seçin ve Özellikler penceresini açın.  
  
3.  Genişletin **(veri bağlamaları)** özelliği ve ardından **(Gelişmiş)** kutusunda, üç nokta düğmesini (![VisualStudioEllipsesButton ekran] (../../../docs/framework/winforms/media/vbellipsesbutton.png " vbEllipsesButton")) görüntülemek için **biçimlendirme ve Gelişmiş bağlama** iletişim kutusunda, bu denetim için özelliklerin tam bir listesi vardır.  
  
4.  Bağlamak ve ardından istediğiniz özelliği seçin **bağlama** oku.  
  
     Kullanılabilir veri kaynaklarının listesi görüntülenir.  
  
5.  İstediğiniz tek bir veri öğesi bulana kadar bağlamak istediğiniz veri kaynağı'nı genişletin.  
  
     Örneğin, bir veri kümesi'nin tablodaki bir sütun değerine bağlanıyorsanız, veri kümesinin adını genişletin ve ardından sütun adlarını görüntülemek için tablo adını genişletin.  
  
6.  Bağlanacak bir öğenin adına tıklayın.  
  
7.  İçinde **türünü biçimlendirme** kutusunda, denetimde görüntülenen verilere uygulamak istediğiniz biçimi tıklatın.  
  
     Her durumda, veri kaynağı içeriyorsa, denetimi görüntülenen değer belirtebilirsiniz <xref:System.DBNull>. Aksi takdirde, Seçenekler, seçtiğiniz biçimi türüne bağlı olarak biraz değişir. Aşağıdaki tabloda, biçimlendirme türleri ve seçenekler gösterilmektedir.  
  
    |Biçim türü|Biçimlendirme seçeneği|  
    |-----------------|-----------------------|  
    |Hiç biçimlendirme|Seçenek yok.|  
    |sayısal|Ondalık basamak sayısını kullanarak belirtin **ondalık** yukarı-aşağı denetim.|  
    |Para Birimi|Ondalık basamak sayısını kullanarak belirtin **ondalık** yukarı-aşağı denetim.|  
    |Tarih saat|Nasıl tarih ve saat içindeki öğelerden birini seçerek görüntüleneceğini seçin **türü** seçim kutusunu.|  
    |Bilimsel|Ondalık basamak sayısını kullanarak belirtin **ondalık** yukarı-aşağı denetim.|  
    |Özel|Kullanarak bir özel biçim dizesi belirtin.<br /><br /> Daha fazla bilgi için bkz: [biçimlendirme türleri](../../../docs/standard/base-types/formatting-types.md). **Not:** özel biçim dizeleri başarıyla veri kaynağı ile ilişkili denetim arasındaki gidiş dönüş için garanti edilmez. Bunun yerine işlemek <xref:System.Windows.Forms.Binding.Parse> veya <xref:System.Windows.Forms.Binding.Format> bağlama için olay ve olay işleme kodda özel biçimlendirme uygulayın.|  
  
8.  Tıklatın **Tamam** kapatmak için **biçimlendirme ve Gelişmiş bağlama** iletişim kutusu ve Özellikler penceresini dönün.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Bir Windows Formunda Basit Bağlantılı Denetim Oluşturma](../../../docs/framework/winforms/how-to-create-a-simple-bound-control-on-a-windows-form.md)  
 [Windows Forms'ta Kullanıcı Girdisi Doğrulama](../../../docs/framework/winforms/user-input-validation-in-windows-forms.md)  
 [Windows Forms Veri Bağlama](../../../docs/framework/winforms/windows-forms-data-binding.md)
