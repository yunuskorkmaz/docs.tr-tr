---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Formları Denetimlerini BindingSource Bileşeni ile Bağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], binding
- BindingSource component [Windows Forms], binding controls
- data binding [Windows Forms], BindingSource component
ms.assetid: 391ae170-de5c-40f8-8233-91cb2ee4683a
ms.openlocfilehash: 95f375d8845c60441aa5eefdd37e32541ea2d5a7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43565687"
---
# <a name="how-to-bind-windows-forms-controls-with-the-bindingsource-component-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Formları Denetimlerini BindingSource Bileşeni ile Bağlama
Formunuza denetimler eklenir ve uygulamanız için kullanıcı arabirimi belirlenen sonra çalışma zamanında, kullanıcılar alter ve uygulamayla ilgili verileri kaydetme böylece bir veri kaynağına denetimlerin bağlayabilirsiniz.  
  
 Windows Forms'ta bir denetim veya denetimlerin bir dizisini bağlama en kolay gerçekleştirilir kullanarak <xref:System.Windows.Forms.BindingSource> denetimi form üzerinde denetimleri ve veri kaynağı arasında bir köprü olarak.  
  
 Formdaki denetimlerin bir veya daha fazla veriye bağlı olabilir; Aşağıdaki yordamda bir <xref:System.Windows.Forms.TextBox> denetim bir veri kaynağına bağlı.  
  
 Yordamı tamamlamak için bir veritabanından alınan veri kaynağına bağlayacaksınız varsayılır. Diğer veri depolarından veri kaynakları oluşturma hakkında daha fazla bilgi için bkz. [yeni veri kaynağı ekleme](/visualstudio/data-tools/add-new-data-sources).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-bind-a-control-at-design-time"></a>Tasarım zamanında bir denetimi bağlamak için  
  
1.  Sürükleme bir <xref:System.Windows.Forms.TextBox> denetim formu açın.  
  
2.  İçinde **özellikleri** penceresi:  
  
    1.  Genişletin **(DataBindings)** düğümü.  
  
    2.  Yanındaki oka tıklayın <xref:System.Windows.Forms.TextBox.Text%2A> özelliği.  
  
         **DataSource** UI türü Düzenleyici açar.  
  
         Bir veri kaynağı, daha önce proje veya form için yapılandırıldı, görünür.  
  
3.  Tıklayın **proje veri kaynağı Ekle** verilere bağlanmak ve bir veri kaynağı oluşturun.  
  
4.  Üzerinde **veri kaynağı Yapılandırma Sihirbazı** Karşılama sayfasında, tıklayın **sonraki**.  
  
5.  Üzerinde **bir veri kaynağı türü seçin** sayfasında **veritabanı**.  
  
6.  Üzerinde **veri bağlantınızı seçin** sayfasında, kullanılabilir bağlantılar listesinden bir veri bağlantısı seçin. İstenen veri bağlantınızı seçin kullanılabilir değilse **yeni bağlantı** yeni bir veri bağlantısı oluşturmak için.  
  
7.  Seçin **Evet, bağlantıyı Kaydet** bağlantı dizesini uygulama yapılandırma dosyasına kaydetmek için.  
  
8.  Uygulamanıza getirmek için veritabanı nesneleri seçin. Bu durumda, istediğiniz bir tabloda bir alan seçin <xref:System.Windows.Forms.TextBox> görüntülenecek.  
  
9. İsterseniz varsayılan veri kümesi adı değiştirin.  
  
10. **Son**'a tıklayın.  
  
11. İçinde **özellikleri** penceresinde yanındaki oka tıklayın <xref:System.Windows.Forms.TextBox.Text%2A> yeniden özelliği. İçinde **DataSource** UI türü Düzenleyici bağlamak için alan adı seçin <xref:System.Windows.Forms.TextBox> için.  
  
     **DataSource** UI türü Düzenleyici kapanır ve veri kümesi <xref:System.Windows.Forms.BindingSource> ve tablo bağdaştırıcısı belirli veri bağlantısı formunuza eklenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.BindingNavigator>  
 [Yeni veri kaynağı ekleme](/visualstudio/data-tools/add-new-data-sources)  
 [Veri kaynakları penceresi](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)
