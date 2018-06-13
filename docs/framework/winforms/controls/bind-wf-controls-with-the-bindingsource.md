---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Formları Denetimlerini BindingSource Bileşeni ile Bağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], binding
- BindingSource component [Windows Forms], binding controls
- data binding [Windows Forms], BindingSource component
ms.assetid: 391ae170-de5c-40f8-8233-91cb2ee4683a
ms.openlocfilehash: 3acbd17e8e969bb448e6deaf17dec23e44fa3bd4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527569"
---
# <a name="how-to-bind-windows-forms-controls-with-the-bindingsource-component-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Formları Denetimlerini BindingSource Bileşeni ile Bağlama
Formunuza denetimler eklenir ve uygulamanız için kullanıcı arabirimi belirlenen sonra çalışma zamanında, kullanıcılar alter ve uygulamayla ilgili verileri kaydetmek böylece bir veri kaynağına denetimlerini bağlayabilirsiniz.  
  
 Windows Forms'ta denetim veya denetimlerin bir dizi bağlama en kolay gerçekleştirilir kullanarak <xref:System.Windows.Forms.BindingSource> denetim form üzerinde denetimleri ve veri kaynağı arasında bir köprü olarak.  
  
 Bir form üzerinde bir veya daha fazla denetimler veriye bağlı olabilir; Aşağıdaki yordamda bir <xref:System.Windows.Forms.TextBox> denetim bir veri kaynağına bağlı.  
  
 Yordamı tamamlamak için bir veritabanından türetilmiş bir veri kaynağına bağlı olacağı varsayılır. Diğer veri depoları veri kaynakları oluşturma hakkında daha fazla bilgi için bkz: [yeni veri kaynakları ekleyin](/visualstudio/data-tools/add-new-data-sources).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-bind-a-control-at-design-time"></a>Tasarım zamanında denetim bağlamak için  
  
1.  Sürükleme bir <xref:System.Windows.Forms.TextBox> denetim form açın.  
  
2.  İçinde **özellikleri** penceresi:  
  
    1.  Genişletme **(veri bağlamaları)** düğümü.  
  
    2.  Yanındaki oka tıklayın <xref:System.Windows.Forms.TextBox.Text%2A> özelliği.  
  
         **DataSource** UI türü Düzenleyici açar.  
  
         Bir veri kaynağı, daha önce proje veya form için yapılandırılmışsa, görünür.  
  
3.  Tıklatın **proje veri kaynağı Ekle** veri bağlanmak ve bir veri kaynağı oluşturun.  
  
4.  Üzerinde **veri kaynağı Yapılandırma Sihirbazı** Karşılama sayfasında, tıklatın **sonraki**.  
  
5.  Üzerinde **bir veri kaynağı türü seç** sayfasında, **veritabanı**.  
  
6.  Üzerinde **veri bağlantınızı** sayfasında, kullanılabilir bağlantılar listesinden bir veri bağlantısı seçin. İstenen veri bağlantınızı kullanılabilir seçin değilse **yeni bağlantı** yeni bir veri bağlantısı oluşturmak için.  
  
7.  Seçin **Evet, bağlantı kaydetme** uygulama yapılandırma dosyasında bağlantı dizesini kaydetmek için.  
  
8.  Uygulamanıza getirmek için veritabanı nesneleri seçin. Bu durumda, istediğiniz bir tablodaki bir alan seçin <xref:System.Windows.Forms.TextBox> görüntülemek için.  
  
9. İsterseniz varsayılan veri kümesi adını değiştirin.  
  
10. **Son**'a tıklayın.  
  
11. İçinde **özellikleri** penceresinde yanındaki oka tıklayın <xref:System.Windows.Forms.TextBox.Text%2A> yeniden özelliği. İçinde **DataSource** UI türü Düzenleyici bağlamak için alanın adını seçin <xref:System.Windows.Forms.TextBox> için.  
  
     **DataSource** UI türü Düzenleyici kapanır ve veri kümesinin <xref:System.Windows.Forms.BindingSource> ve tablo bağdaştırıcısı belirli veri bağlantısı formunuza eklenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.BindingNavigator>  
 [Yeni veri kaynakları ekleyin](/visualstudio/data-tools/add-new-data-sources)  
 [Veri kaynakları penceresi](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)
