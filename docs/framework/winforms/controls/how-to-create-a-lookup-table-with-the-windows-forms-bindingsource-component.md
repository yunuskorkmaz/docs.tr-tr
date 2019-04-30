---
title: 'Nasıl yapılır: Windows Forms BindingSource Bileşeniyle Arama Tablosu Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- lookup tables
- tables [Windows Forms], creating lookup tables
- BindingSource component [Windows Forms], creating a lookup table
- BindingSource component [Windows Forms], examples
ms.assetid: 622fce80-879d-44be-abbf-8350ec22ca2b
ms.openlocfilehash: 481774e9127531bb38df0cc71ac8e7eab76da695
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61747063"
---
# <a name="how-to-create-a-lookup-table-with-the-windows-forms-bindingsource-component"></a>Nasıl yapılır: Windows Forms BindingSource Bileşeniyle Arama Tablosu Oluşturma
Arama tablosu kayıttan alınan ilişkili bir tabloda görüntüleyen bir sütun olan verilerin bir tablodur. Aşağıdaki yordamlarda, bir <xref:System.Windows.Forms.ComboBox> denetimi üst alt tablo için yabancı anahtar ilişkisi alanıyla görüntülemek için kullanılır.  
  
 Bu iki tablo ve bu ilişkiyi görselleştirmenize yardımcı olmak için üst ve alt tablo örneği aşağıdadır:  
  
 CustomersTable (üst tablo)  
  
|CustomerID|CustomerName|  
|----------------|------------------|  
|712|Paul Koch|  
|713|Tamara Johnston|  
  
 OrdersTable (alt tablo)  
  
|Sipariş Kimliği|orderDate|CustomerID|  
|-------------|---------------|----------------|  
|903|Şubat 12, 2004|712|  
|904|13 Şubat 2004|713|  
  
 Bu senaryoda, bir tablo, CustomersTable, görüntülemek ve kaydetmek istediğiniz gerçek bilgi depolar. Ancak alanı kaydetmek için tabloda açıklık veri çıkışı bırakır. Diğer tablo, OrdersTable, hangi müşterinin hakkında kimlik numarasını hangi sipariş tarihi ve sipariş kimliği için eşdeğer yalnızca görünüm ile ilgili bilgiler içerir Müşterilerin adlarını hiçbir Bahsetme yoktur.  
  
 Dört önemli özellikleri üzerinde ayarlanır [ComboBox denetimi](combobox-control-windows-forms.md) arama tablosu oluşturma için denetimi.  
  
- <xref:System.Windows.Forms.ComboBox.DataSource%2A> Özelliği tablo adını içerir.  
  
- <xref:System.Windows.Forms.ListControl.DisplayMember%2A> Özelliği, bu tablonun (müşterinin adı) kontrol metni için görüntülemek istediğiniz veri sütunu içerir.  
  
- <xref:System.Windows.Forms.ListControl.ValueMember%2A> Bilgilerini (kimlik numarası üst tablodan) söz konusu tablonun veri sütununun özellik içerir.  
  
- <xref:System.Windows.Forms.ListControl.SelectedValue%2A> Özelliği, temel alt tablo için arama değeri sağlar <xref:System.Windows.Forms.ListControl.ValueMember%2A>.  
  
 Aşağıdaki yordamlar, formunuzu arama tablosu olarak düzenleme ve denetimlere veri bağlama işlemini göstermektedir. Başarıyla yordamları tamamlamak için daha önce belirtildiği gibi bir yabancı anahtar ilişkisine sahip üst ve alt tablolar ile bir veri kaynağı olmalıdır.  
  
### <a name="to-create-the-user-interface"></a>Kullanıcı arabirimini oluşturmak için  
  
1. Gelen **araç kutusu**, sürükleyin bir <xref:System.Windows.Forms.ComboBox> forma denetim.  
  
     Bu denetim, üst tablo sütunu görüntülenir.  
  
2. Alt tablo ayrıntılarını görüntülemek için diğer denetimler sürükleyin. Hangi denetimlerin seçtiğiniz tablodaki verileri biçimi belirlemeniz gerekir. Daha fazla bilgi için [işleve göre Windows Forms denetimleri](windows-forms-controls-by-function.md).  
  
3. Sürükleme bir <xref:System.Windows.Forms.BindingNavigator> forma denetim; bu alt tablodaki verileri gezinmenize olanak tanır.  
  
### <a name="to-connect-to-the-data-and-bind-it-to-controls"></a>Verilere bağlanmak ve denetimlere bağlama  
  
1. Seçin <xref:System.Windows.Forms.ComboBox> ve akıllı bir görev iletişim kutusunu görüntülemek için akıllı bir görev karakter'a tıklayın.  
  
2. Seçin **kullanım veri bağlama öğeleri**.  
  
3. Yanındaki oka tıklayın **veri kaynağı** açılan kutusu. Bir veri kaynağını daha önce proje veya form için yapılandırılmışsa, görüntülenir. Aksi takdirde, (Bu örnekte, Northwind örnek veritabanındaki müşteriler ve Siparişler tablolarını kullanır ve parantez içinde bunlara başvuran) aşağıdaki adımları tamamlayın.  
  
    1. Tıklayın **proje veri kaynağı Ekle** verilere bağlanmak ve bir veri kaynağı oluşturun.  
  
    2. Üzerinde **veri kaynağı Yapılandırma Sihirbazı** Karşılama sayfasında, tıklayın **sonraki**.  
  
    3. Seçin **veritabanı** üzerinde **bir veri kaynağı türü seçin** sayfası.  
  
    4. Kullanılabilir bağlantılar listesinden bir veri bağlantısı seçin **veri bağlantınızı seçin** sayfası. İstenen veri bağlantısı kullanılamıyorsa seçin **yeni bağlantı** yeni bir veri bağlantısı oluşturmak için.  
  
    5. Tıklayın **Evet, bağlantıyı Kaydet** bağlantı dizesini uygulama yapılandırma dosyasına kaydetmek için.  
  
    6. Uygulamanıza getirmek için veritabanı nesneleri seçin. Bu durumda, bir üst tablo ve yabancı anahtar ilişkisi olan alt tablo (örneğin, müşteriler ve siparişler) seçin.  
  
    7. İsterseniz varsayılan veri kümesi adı değiştirin.  
  
    8. **Son**'a tıklayın.  
  
4. İçinde **görünen üye** birleşik giriş kutusunda görüntülenecek sütun adı (örneğin, ContactName) açılan kutusunda seçin.  
  
5. İçinde **değer üyesi** açılan kutu, alt tablosunda arama işlemi gerçekleştirmek için (örneğin, CustomerID) sütununu seçin.  
  
6. İçinde **seçili değer** açılan kutusunda, gitmek **Zdroje dat Projektu** ve üst ve alt tablolar içeren yeni oluşturduğunuz veri kümesi. Aynı özellik üst tablo (örneğin, siparişler.MüşteriNo) değeri üyesi olan alt tablo seçin. Uygun <xref:System.Windows.Forms.BindingSource> , veri kümesi ve tablo bağdaştırıcısı bileşenleri oluşturulur ve forma eklenir.  
  
7. Bağlama <xref:System.Windows.Forms.BindingNavigator> denetimini <xref:System.Windows.Forms.BindingSource> alt tablonun (örneğin, `OrdersBindingSource`).  
  
8. Denetimleri dışında bağlama <xref:System.Windows.Forms.ComboBox> ve <xref:System.Windows.Forms.BindingNavigator> alt tablonun ayrıntıları alanlara denetiminden <xref:System.Windows.Forms.BindingSource> (örneğin, `OrdersBindingSource`), görüntülemek istediğiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.BindingSource>
- [BindingSource Bileşeni](bindingsource-component.md)
- [ComboBox Denetimi](combobox-control-windows-forms.md)
- [Visual Studio'da verilere denetimler bağlama](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
