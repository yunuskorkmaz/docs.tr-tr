---
title: "Nasıl yapılır: Windows Formları BindingSource Bileşeniyle Arama Tablosu Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- lookup tables
- tables [Windows Forms], creating lookup tables
- BindingSource component [Windows Forms], creating a lookup table
- BindingSource component [Windows Forms], examples
ms.assetid: 622fce80-879d-44be-abbf-8350ec22ca2b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 324e4ed290b98d2268dd82fa55b81deaeb849770
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-lookup-table-with-the-windows-forms-bindingsource-component"></a>Nasıl yapılır: Windows Formları BindingSource Bileşeniyle Arama Tablosu Oluşturma
Arama tablosu ilişkili bir tabloda kayıttan alınan verileri görüntüleyen bir sütun olan verilerin bir tablosu verilmiştir. Aşağıdaki yordamlarda bulunan bir <xref:System.Windows.Forms.ComboBox> denetimi üst alt tablosuna yabancı anahtar ilişkisi alanıyla görüntülemek için kullanılır.  
  
 Bu iki tablo ve bu ilişkiyi görselleştirmenize yardımcı olmak için üst ve alt tablo örneği aşağıdadır:  
  
 CustomersTable (üst tablo)  
  
|CustomerID|customerName|  
|----------------|------------------|  
|712|Paul Koch|  
|713|Tamara Johnston|  
  
 OrdersTable (alt tablo)  
  
|OrderID|OrderDate|CustomerID|  
|-------------|---------------|----------------|  
|903|12 Şubat 2004|712|  
|904|13 Şubat 2004|713|  
  
 Bu senaryoda, bir tablo, CustomersTable, görüntülemek ve kaydetmek istediğiniz gerçek bilgileri depolar. Ancak alanı kaydetmek için tablonun netlik ekleyen verileri bırakır. Diğer tablo, OrdersTable, hangi müşteri numarası hangi sipariş tarihi ve Sipariş Kimliği'eşdeğerdir yalnızca görünüm ilgili bilgiler de içerir Hiçbir Bahsetme müşterilerin adlarını yoktur.  
  
 Dört önemli özellikleri ayarlandığında [ComboBox denetimi](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md) arama tablosu oluşturma için denetimi.  
  
-   <xref:System.Windows.Forms.ComboBox.DataSource%2A> Özelliği tablo adını içerir.  
  
-   <xref:System.Windows.Forms.ListControl.DisplayMember%2A> Özelliği (Müşteri'nin adı) kontrol metni için görüntülemek istediğiniz bu tablonun veri sütunu içerir.  
  
-   <xref:System.Windows.Forms.ListControl.ValueMember%2A> Özelliği (kimlik numarası üst tablodan) depolanmış bilgilerle bu tablonun veri sütunu içerir.  
  
-   <xref:System.Windows.Forms.ListControl.SelectedValue%2A> Özelliği, bağlı alt tablo için arama değeri sağlar <xref:System.Windows.Forms.ListControl.ValueMember%2A>.  
  
 Aşağıdaki yordamlar bir arama tablosu formunuzu düzenleme ve denetimlere veri bağlama gösterilmektedir. Başarıyla yordamları tamamlamak için daha önce belirtildiği gibi bir yabancı anahtar ilişkisine sahip üst ve alt tablolar ile bir veri kaynağı olması gerekir.  
  
### <a name="to-create-the-user-interface"></a>Kullanıcı arabirimini oluşturmak için  
  
1.  Gelen **araç**, sürükleyin bir <xref:System.Windows.Forms.ComboBox> forma denetim.  
  
     Bu denetim, üst tablodan sütun görüntülenir.  
  
2.  Alt tablosundan ayrıntılarını görüntülemek için diğer denetimleri sürükleyin. Tablosunda veri biçimi, seçtiğiniz hangi denetimlerin belirlemeniz gerekir. Daha fazla bilgi için bkz: [işleve göre Windows Forms denetimleri](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md).  
  
3.  Sürükleme bir <xref:System.Windows.Forms.BindingNavigator> denetim forma; bu alt tablodaki verileri gezinmenize olanak tanır.  
  
### <a name="to-connect-to-the-data-and-bind-it-to-controls"></a>Veri bağlanmak ve denetimlere bağlama  
  
1.  Seçin <xref:System.Windows.Forms.ComboBox> akıllı görev iletişim kutusu görüntülemek için akıllı görev karakter'a tıklayın.  
  
2.  Seçin **kullanım verileri bağlı öğeleri**.  
  
3.  Yanındaki oka tıklayın **veri kaynağı** açılan kutusu. Bir veri kaynağı, daha önce proje veya form için yapılandırılmışsa, görünür; Aksi takdirde, (Bu örnekte Northwind örnek veritabanı müşteriler ve Siparişler tablolarını kullanır ve bunlara parantez içine başvuru yapan) aşağıdaki adımları tamamlayın.  
  
    1.  Tıklatın **proje veri kaynağı Ekle** veri bağlanmak ve bir veri kaynağı oluşturun.  
  
    2.  Üzerinde **veri kaynağı Yapılandırma Sihirbazı** Karşılama sayfasında, tıklatın **sonraki**.  
  
    3.  Seçin **veritabanı** üzerinde **bir veri kaynağı türü seç** sayfası.  
  
    4.  Kullanılabilir bağlantılar listesinden bir veri bağlantısı seçin **veri bağlantınızı** sayfası. İstenen veri bağlantınızı kullanılabilir durumda değilse, seçin **yeni bağlantı** yeni bir veri bağlantısı oluşturmak için.  
  
    5.  Tıklatın **Evet, bağlantı kaydetme** uygulama yapılandırma dosyasında bağlantı dizesini kaydetmek için.  
  
    6.  Uygulamanıza getirmek için veritabanı nesneleri seçin. Bu durumda, bir üst tablo ve yabancı anahtar ilişkisi alt tabloda (örneğin, müşteriler ve siparişler) seçin.  
  
    7.  İsterseniz varsayılan veri kümesi adını değiştirin.  
  
    8.  **Son**'a tıklayın.  
  
4.  İçinde **görüntü üye** açılan kutusunda görüntülenecek sütun adı (örneğin, ContactName) açılan kutusunda seçin.  
  
5.  İçinde **değer üyesi** açılan kutu, alt tabloda arama işlemi gerçekleştirmek için sütun (örneğin, CustomerID) seçin.  
  
6.  İçinde **seçili değer** açılır kutusunda, gitmek **proje veri kaynaklarını** ve üst ve alt tablolar içeren yeni oluşturduğunuz veri kümesi. Üst tablo (örneğin, siparişler.MüşteriNo) değeri üyesi olan alt tablo aynı özelliğini seçin. Uygun <xref:System.Windows.Forms.BindingSource> , veri kümesi ve tablo bağdaştırıcısı bileşenleri oluşturulur ve forma eklenir.  
  
7.  Bağlama <xref:System.Windows.Forms.BindingNavigator> denetimini <xref:System.Windows.Forms.BindingSource> alt tablonun (örneğin, `OrdersBindingSource`).  
  
8.  Denetimleri dışında bağlamak <xref:System.Windows.Forms.ComboBox> ve <xref:System.Windows.Forms.BindingNavigator> alt tablonun ayrıntıları alanlara denetiminden <xref:System.Windows.Forms.BindingSource> (örneğin, `OrdersBindingSource`) görüntülemek istediğiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.BindingSource>  
 [BindingSource Bileşeni](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [ComboBox Denetimi](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md)  
 [Visual Studio'da verilere denetimler bağlama](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
