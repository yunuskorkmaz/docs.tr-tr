---
title: BindingSource bileşeniyle arama tablosu oluşturma
ms.date: 03/30/2017
helpviewer_keywords:
- lookup tables
- tables [Windows Forms], creating lookup tables
- BindingSource component [Windows Forms], creating a lookup table
- BindingSource component [Windows Forms], examples
ms.assetid: 622fce80-879d-44be-abbf-8350ec22ca2b
ms.openlocfilehash: ccf2bfa6cf3f56a38b55f8c87004c42a46172891
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736807"
---
# <a name="how-to-create-a-lookup-table-with-the-windows-forms-bindingsource-component"></a>Nasıl yapılır: Windows Formları BindingSource Bileşeniyle Arama Tablosu Oluşturma
Arama tablosu, ilişkili tablodaki kayıtlardan verileri görüntüleyen bir sütunu olan bir veri tablosudur. Aşağıdaki yordamlarda, üst-anahtar ilişkisine sahip alanı alt tabloya göstermek için bir <xref:System.Windows.Forms.ComboBox> denetimi kullanılır.  
  
 Bu iki tabloyu ve bu ilişkiyi görselleştirmenize yardımcı olmak için bir üst ve alt tablo örneği aşağıda verilmiştir:  
  
 CustomersTable (üst tablo)  
  
|Ister|customerName|  
|----------------|------------------|  
|712|Paul Koch|  
|713|Tamara Johnston|  
  
 OrdersTable (alt tablo)  
  
|Sipariş|OrderDate|Ister|  
|-------------|---------------|----------------|  
|903|12 Şubat 2004|712|  
|904|13 Şubat 2004|713|  
  
 Bu senaryoda, bir tablo olan CustomersTable, göstermek ve kaydetmek istediğiniz gerçek bilgileri depolar. Ancak alanı kazanmak için tablo, açıklık ekleyen verileri bırakır. Diğer tablo, OrdersTable, hangi müşteri KIMLIĞI numarasının hangi sipariş tarihi ve sipariş KIMLIĞIYLE eşdeğer olduğu hakkında yalnızca görünümle ilgili bilgileri içerir. Müşterilerin adlarından bahsetme yoktur.  
  
 Arama tablosu oluşturmak için [ComboBox Denetim](combobox-control-windows-forms.md) denetiminde dört önemli özellik ayarlanır.  
  
- <xref:System.Windows.Forms.ComboBox.DataSource%2A> özelliği tablonun adını içerir.  
  
- <xref:System.Windows.Forms.ListControl.DisplayMember%2A> özelliği, denetim metni (müşterinin adı) için görüntülenmesini istediğiniz tablonun veri sütununu içerir.  
  
- <xref:System.Windows.Forms.ListControl.ValueMember%2A> özelliği, bu tablonun depolanan bilgiler (üst tablodaki KIMLIK numarası) ile veri sütununu içerir.  
  
- <xref:System.Windows.Forms.ListControl.SelectedValue%2A> özelliği, alt tablo için <xref:System.Windows.Forms.ListControl.ValueMember%2A>temelinde arama değeri sağlar.  
  
 Aşağıdaki yordamlarda, formunuzu bir arama tablosu olarak nasıl düzenleyeni ve verileri üzerinde denetimlere nasıl bağlayacağınız gösterilmektedir. Yordamları başarıyla tamamlayabilmeniz için, daha önce belirtildiği gibi, yabancı anahtar ilişkisine sahip üst ve alt tablolar içeren bir veri kaynağınız olması gerekir.  
  
### <a name="to-create-the-user-interface"></a>Kullanıcı arabirimini oluşturmak için  
  
1. **Araç kutusundan**bir <xref:System.Windows.Forms.ComboBox> denetimini form üzerine sürükleyin.  
  
     Bu denetim, üst tablodaki sütunu görüntüler.  
  
2. Alt tablodaki ayrıntıları göstermek için diğer denetimleri sürükleyin. Tablodaki verilerin biçimi hangi denetimleri istediğinizi belirlemelidir. Daha fazla bilgi için bkz. [Windows Forms denetimleri işleve göre](windows-forms-controls-by-function.md).  
  
3. Bir <xref:System.Windows.Forms.BindingNavigator> denetimini form üzerine sürükleyin; Bu, alt tablodaki verilerde gezinmeniz için izin verir.  
  
### <a name="to-connect-to-the-data-and-bind-it-to-controls"></a>Verilere bağlanmak ve denetimlere bağlamak için  
  
1. <xref:System.Windows.Forms.ComboBox> seçin ve Akıllı Görev iletişim kutusunu göstermek için Akıllı Görev glifi ' ne tıklayın.  
  
2. **Veri bağlantılı öğeleri kullan**' ı seçin.  
  
3. **Veri kaynağı** açılır kutusunun yanındaki oka tıklayın. Bir veri kaynağı daha önce proje veya form için yapılandırıldıysa, görünür; Aksi takdirde, aşağıdaki adımları uygulayın (Bu örnek, Northwind örnek veritabanının Customers ve Orders tablolarını kullanır ve bunları parantez içinde ifade eder).  
  
    1. Verilere bağlanmak ve bir veri kaynağı oluşturmak için **proje veri kaynağı Ekle** ' ye tıklayın.  
  
    2. **Veri kaynağı Yapılandırma Sihirbazı** 'na hoş geldiniz sayfasında **İleri**' ye tıklayın.  
  
    3. **Veri kaynağı türü seçin** sayfasında **veritabanı** ' nı seçin.  
  
    4. **Veri bağlantınızı seçin** sayfasında kullanılabilir bağlantılar listesinden bir veri bağlantısı seçin. İstediğiniz veri bağlantınız yoksa yeni **bağlantı** ' yı seçerek yeni bir veri bağlantısı oluşturun.  
  
    5. Bağlantı dizesini uygulama yapılandırma dosyasına kaydetmek için **Evet, bağlantıyı kaydet** ' e tıklayın.  
  
    6. Uygulamanıza getirmek istediğiniz veritabanı nesnelerini seçin. Bu durumda, bir ana tablo ve alt tablo (örneğin, müşteriler ve siparişler) yabancı anahtar ilişkisiyle seçin.  
  
    7. İsterseniz varsayılan veri kümesi adını değiştirin.  
  
    8. **Son**'a tıklayın.  
  
4. **Üye görüntüle** açılan kutusunda, açılan kutuda görüntülenecek sütun adını (örneğin, ContactName) seçin.  
  
5. **Değer üyesi** açılan kutusunda, alt tabloda arama işlemini gerçekleştirmek için sütunu (örneğin, CustomerID) seçin.  
  
6. **Seçili değer** açılır kutusunda, **proje veri kaynakları** ' na ve üst ve alt tabloları içeren yeni oluşturduğunuz veri kümesine gidin. Üst tablonun değer üyesi olan alt tablonun aynı özelliğini seçin (örneğin, Orders. CustomerID). Uygun <xref:System.Windows.Forms.BindingSource>, veri kümesi ve tablo bağdaştırıcısı bileşenleri oluşturulacak ve forma eklenecek.  
  
7. <xref:System.Windows.Forms.BindingNavigator> denetimini alt tablonun <xref:System.Windows.Forms.BindingSource> bağlayın (örneğin, `OrdersBindingSource`).  
  
8. <xref:System.Windows.Forms.ComboBox> ve <xref:System.Windows.Forms.BindingNavigator> denetimi dışındaki denetimleri, alt tablonun <xref:System.Windows.Forms.BindingSource> (örneğin, `OrdersBindingSource`) Ayrıntılar alanlarına bağlayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.BindingSource>
- [BindingSource Bileşeni](bindingsource-component.md)
- [ComboBox Denetimi](combobox-control-windows-forms.md)
- [Visual Studio'da verilere denetimler bağlama](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
