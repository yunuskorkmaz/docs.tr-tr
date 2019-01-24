---
title: 'Nasıl yapılır: Yazıcı Kopyalama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- print queues [WPF]
- cloning printers [WPF]
- printers [WPF], cloning
- print queues [WPF], cloning
- cloning print queues [WPF]
ms.assetid: dd6997c9-fe04-40f8-88a6-92e3ac0889eb
ms.openlocfilehash: d7a73c6590ca2df00c77a3a7255f2064a8676c42
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54677231"
---
# <a name="how-to-clone-a-printer"></a>Nasıl yapılır: Yazıcı Kopyalama
Çoğu işletmenin belirli bir noktada aynı modelin birden çok yazıcılar satın alacak. Genellikle, bunların tümü neredeyse aynı yapılandırma ayarlarıyla yüklenir. Her yazıcı yükleme alabilir ve hataya açık alanlardır. <xref:System.Printing.IndexedProperties?displayProperty=nameWithType> Ad alanı ve <xref:System.Printing.PrintServer.InstallPrintQueue%2A> Microsoft .NET Framework ile sunulan sınıfı mevcut bir yazdırma kuyruğundan klonlanır ek yazdırma sıralarını herhangi bir sayıda anında yükleneceği mümkün kılar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, ikinci bir yazdırma sırasının, mevcut bir yazdırma kuyruğundan kopyalanmış olan. İkinci ilkinden adını, konumunu, bağlantı noktası ve paylaşılan durum içinde. Bunu yapmak için önemli adımlar aşağıdaki gibidir.  
  
1.  Oluşturma bir <xref:System.Printing.PrintQueue> kopyalanma gidip mevcut yazıcı nesnesi.  
  
2.  Oluşturma bir <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> gelen <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A> , <xref:System.Printing.PrintQueue>. <xref:System.Collections.DictionaryEntry.Value%2A> Türlerinden türetilmiş bir nesnenin Bu sözlük her giriş özelliğidir <xref:System.Printing.IndexedProperties.PrintProperty>. Bu sözlükte bir giriş değeri ayarlamak için iki yolu vardır.  
  
    -   Sözlüğün kullanın **Kaldır** ve <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.Add%2A> yöntemleri girişi kaldırın ve istenen değeriyle yeniden ekleyin.  
  
    -   Sözlüğün kullanın <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.SetProperty%2A> yöntemi.  
  
     Aşağıdaki örnekte, her iki yolu gösterir.  
  
3.  Oluşturma bir <xref:System.Printing.IndexedProperties.PrintBooleanProperty> nesne ve ayarlayın, <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> "IsShared" için ve kendi <xref:System.Printing.IndexedProperties.PrintBooleanProperty.Value%2A> için `true`.  
  
4.  Kullanım <xref:System.Printing.IndexedProperties.PrintBooleanProperty> değeri olması için nesne <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>'s "IsShared" girişi.  
  
5.  Oluşturma bir <xref:System.Printing.IndexedProperties.PrintStringProperty> nesne ve ayarlayın, <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> "ShareName" için ve kendi <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> uygun bir <xref:System.String>.  
  
6.  Kullanım <xref:System.Printing.IndexedProperties.PrintStringProperty> değeri olması için nesne <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>'s "ShareName" girişi.  
  
7.  Hesaplanmış sütun oluşturabiliriz <xref:System.Printing.IndexedProperties.PrintStringProperty> nesne ve ayarlayın, <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> "Konum" için ve kendi <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> uygun bir <xref:System.String>.  
  
8.  İkinci kullanın <xref:System.Printing.IndexedProperties.PrintStringProperty> değeri olması için nesne <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>'s "Konum" girişi.  
  
9. Bir dizi oluşturma <xref:System.String>s. Her öğe bir bağlantı noktası sunucusunda adıdır.  
  
10. Kullanım <xref:System.Printing.PrintServer.InstallPrintQueue%2A> yeni değerlerle yeni bir yazıcı yüklenecek.  
  
 Bir örnek aşağıda verilmiştir.  
  
 [!code-csharp[ClonePrinter#ClonePrinter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClonePrinter/CSharp/Program.cs#cloneprinter)]
 [!code-vb[ClonePrinter#ClonePrinter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClonePrinter/visualbasic/program.vb#cloneprinter)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Printing.IndexedProperties>
- <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>
- <xref:System.Printing.LocalPrintServer>
- <xref:System.Printing.PrintQueue>
- <xref:System.Collections.DictionaryEntry>
- [WPF'deki Belgeler](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)
- [Yazdırmaya Genel Bakış](../../../../docs/framework/wpf/advanced/printing-overview.md)
