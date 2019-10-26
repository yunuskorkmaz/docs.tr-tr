---
title: LINQ to XML veri bağlama örneği
ms.date: 10/22/2019
ms.topic: sample
helpviewer_keywords:
- linq to xml data binding sample
ms.openlocfilehash: aac814e4768a863a93e69e34cd18c941a9b35c89
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920939"
---
# <a name="linq-to-xml-data-binding-sample"></a>LINQ to XML veri bağlama örneği

Bu makalede, Kullanıcı Arabirimi bileşenlerini gömülü bir XML veri kaynağına bağlayan bir Windows Presentation Foundation (WPF) uygulaması olan LinqToXmlDataBinding örneği açıklanmaktadır.

## <a name="overview"></a>Genel bakış

LinqToXmlDataBinding örneği, ve XAML kaynak dosyalarını içeren C# bir WINDOWS PRESENTATION FOUNDATION (WPF) uygulamasıdır. Gömülü bir XML belgesi, kitapların listesini tanımlar. Uygulama, kullanıcının kitap girişlerini görüntülemesini, eklemesini, silmesini ve düzenlemesini sağlar.

İki birincil kaynak dosyası vardır:

- [L2DBForm. xaml](l2dbform-xaml-source-code.md) , ana pencerenin kullanıcı ARABIRIMI (UI) için XAML bildirim kodunu içerir. Ayrıca, kitap listeleri için bir veri sağlayıcısını ve katıştırılmış XML belgesini tanımlayan bir pencere kaynağı bölümü içerir.

- [L2DBForm.xaml.cs](l2dbform-xaml-cs-source-code.md) , Kullanıcı arabirimiyle ilişkili başlatma ve olay işleme yöntemlerini içerir.

Ana pencere aşağıdaki dört dikey UI bölümüne bölünmüştür:

- **XML** katıştırılmış kitap LISTESININ ham XML kaynağını görüntüler.

- **Kitap listesi** , kitap girişlerini standart metin olarak görüntüler ve kullanıcının tek tek girdileri seçmesini ve silmesini sağlar.

- **Seçili kitabı Düzenle** , kullanıcının şu anda seçili olan kitap girişiyle ilişkili değerleri düzenlemesini sağlar.

- **Yeni kitap ekle** , Kullanıcı tarafından girilen değerlere göre yeni bir kitap girişi oluşturulmasına izin vermez.

## <a name="run-the-sample"></a>Örneği çalıştırın

Bu bölümde, Visual Studio 'da LinqToXmlDataBinding projesi oluşturma ve derleme ve elde edilen LinqToXmlDataBinding Windows Presentation Foundation (WPF) uygulamasının nasıl çalıştırılacağı gösterilmektedir.

### <a name="create-the-project"></a>Projeyi oluşturma

1. Visual Studio 'yu açın ve **LinqToXmlDataBinding**adlı bir C# **WPF uygulaması** oluşturun.

   Projenin .NET Framework 3,5 ' i (veya üzeri) hedeflemesi gerekir.

1. Henüz yoksa, aşağıdaki .NET derlemeleri için proje başvuruları ekleyin:

    - System.Data
    - System. Data. Datase, sions
    - System.Xml
    - System.Xml

1. **Ctrl** +**SHIFT** +**B**tuşlarına basarak çözümü derleyin, sonra **F5**tuşuna basarak çalıştırın.

   Projenin hata olmadan derlenmesi ve genel bir WPF uygulaması olarak çalışması gerekir.

### <a name="add-code"></a>Kod Ekle

1. **Çözüm Gezgini**, **Window1. xaml** kaynak dosyasını **L2XDBForm. xaml**olarak yeniden adlandırın.

   Window1.xaml.cs bağımlı kaynak dosyası otomatik olarak L2XDBForm.xaml.cs olarak yeniden adlandırılır.

1. **L2XDBForm. xaml** dosyasında bulunan kaynak kodu [L2DBForm. xaml kaynak kodu](l2dbform-xaml-source-code.md)ile değiştirin. Bu dosyayla çalışmak için XAML kaynak görünümünü kullanın.

1. Benzer şekilde, **L2XDBForm.xaml.cs** içindeki kaynağı [L2DBForm.xaml.cs kaynak kodu](l2dbform-xaml-cs-source-code.md)ile değiştirin.

1. **App. xaml**dosyasında, **Window1. xaml** dizesinin tüm oluşumlarını **L2XDBForm. xaml**ile değiştirin.

1. **Ctrl** +**SHIFT** +**B**'ye basarak çözümü oluşturun.

### <a name="run-the-app"></a>Uygulamayı çalıştırma

LinqToXmlDataBinding uygulaması, kullanıcının gömülü bir XML öğesi olarak depolanan bir kitap listesini görüntülemesini ve işlemesini sağlar. **F5** tuşuna basarak uygulamayı çalıştırın (hata ayıklamayı Başlat) veya **CTRL**+**F5** (hata ayıklama olmadan Başlat).

**LINQ to XML kullanarak WPF veri bağlama** başlıklı bir program penceresi görüntülenir.

Kullanıcı arabiriminin üst bölümü, kitap listesini temsil eden ham **XML** 'i görüntüler. Bir WPF <xref:System.Windows.Controls.TextBlock> denetimi kullanılarak görüntülenir ve bu, fare veya klavye aracılığıyla etkileşimi etkinleştirmez.

**Kitap listesi**etiketli ikinci dikey bölüm, kitapları düz metin sıralı bir liste olarak görüntüler. Fareyle veya klavyeden seçimi sağlayan <xref:System.Windows.Controls.ListBox> denetimini kullanır.

### <a name="add-and-delete-books"></a>Kitap ekleme ve silme

Listeye yeni bir kitap eklemek için son bölümdeki denetim <xref:System.Windows.Controls.TextBox>, **Yeni kitap ekle**' **ye ve ardından** **kitap ekle**' ye bir **değer** girin. Kitap, hem kitap hem de XML listelerinde listeye eklenir. Bu program giriş değerlerini doğrulamaz.

Listeden mevcut bir kitabı silmek için **kitap listesi** bölümünde seçin ve ardından **Seçili kitabı kaldır**' ı seçin. Kitap girişi hem defterden hem de ham XML kaynak listelerinden kaldırılır.

### <a name="edit-a-book-entry"></a>Kitap girişini düzenleme

1. İkinci **kitap listesi** bölümünde kitap girişini seçin.

   Geçerli değerleri **Seçili kitabı Düzenle** bölümünde görüntülenir.

1. Klavyeyi kullanarak değerleri düzenleyin. <xref:System.Windows.Controls.TextBox> denetim odağı kaybettiğinde, değişiklikler otomatik olarak XML kaynağına ve kitap listelerine yayılır.
