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
ms.openlocfilehash: 8f3a9c3b4d9f4bcbe3a6ffcff9868aa7b19b8f28
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544209"
---
# <a name="how-to-clone-a-printer"></a>Nasıl yapılır: Yazıcı Kopyalama
Çoğu işletme belirli bir noktada aynı modelin birden çok yazıcı satın alacaklardır. Genellikle, bunlar tüm neredeyse aynı yapılandırma ayarları ile yüklenir. Her yazıcı yükleme alabilir ve hataya. <xref:System.Printing.IndexedProperties?displayProperty=nameWithType> Ad alanı ve <xref:System.Printing.PrintServer.InstallPrintQueue%2A> Microsoft .NET Framework ile sunulan sınıfı anında kopyalandığı ek yazdırma sıralarını herhangi bir sayıda var olan bir yazdırma kuyruğundan yüklemek olanaklı kılar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, ikinci bir yazdırma sırası bir mevcut yazdırma sırasından kopyalanır. İkinci birinciden farklı yalnızca adını, konumunu, bağlantı noktası ve paylaşılan durum içinde. Bunu yapmak için önemli adımlar aşağıdaki gibidir.  
  
1.  Oluşturma bir <xref:System.Printing.PrintQueue> kopyalanma giderek varolan yazıcı nesnesi.  
  
2.  Oluşturma bir <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> gelen <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A> , <xref:System.Printing.PrintQueue>. <xref:System.Collections.DictionaryEntry.Value%2A> Bu sözlükteki her girdinin özelliği türetilen türlerden birinde bir nesnedir <xref:System.Printing.IndexedProperties.PrintProperty>. Bu sözlükteki bir giriş değerini ayarlamak için iki yolu vardır.  
  
    -   Sözlüğün kullanmak **kaldırmak** ve <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.Add%2A> yöntemlerle girdiyi kaldırmak ve istenilen değer ile yeniden ekleyin.  
  
    -   Sözlüğün kullanmak <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.SetProperty%2A> yöntemi.  
  
     Aşağıdaki örnekte, her iki yolu gösterir.  
  
3.  Oluşturma bir <xref:System.Printing.IndexedProperties.PrintBooleanProperty> nesne ve ayarlayın, <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> "IsShared" için ve kendi <xref:System.Printing.IndexedProperties.PrintBooleanProperty.Value%2A> için `true`.  
  
4.  Kullanım <xref:System.Printing.IndexedProperties.PrintBooleanProperty> değeri olması için nesne <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>'s "IsShared" girişi.  
  
5.  Oluşturma bir <xref:System.Printing.IndexedProperties.PrintStringProperty> nesne ve ayarlayın, <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> "ShareName" için ve kendi <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> için uygun bir <xref:System.String>.  
  
6.  Kullanım <xref:System.Printing.IndexedProperties.PrintStringProperty> değeri olması için nesne <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>'s "ShareName" girişi.  
  
7.  Başka birini oluşturmak <xref:System.Printing.IndexedProperties.PrintStringProperty> nesne ve ayarlayın, <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> "Konum" için ve kendi <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> için uygun bir <xref:System.String>.  
  
8.  İkinci <xref:System.Printing.IndexedProperties.PrintStringProperty> değeri olması için nesne <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>'s "Konum" girişi.  
  
9. Bir dizi oluşturmak <xref:System.String>s. Her öğe bir bağlantı noktası sunucusundaki adıdır.  
  
10. Kullanım <xref:System.Printing.PrintServer.InstallPrintQueue%2A> yeni değerlerle yeni bir yazıcı yüklemek için.  
  
 Aşağıda bir örnektir.  
  
 [!code-csharp[ClonePrinter#ClonePrinter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClonePrinter/CSharp/Program.cs#cloneprinter)]
 [!code-vb[ClonePrinter#ClonePrinter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClonePrinter/visualbasic/program.vb#cloneprinter)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Printing.IndexedProperties>  
 <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>  
 <xref:System.Printing.LocalPrintServer>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Collections.DictionaryEntry>  
 [WPF'deki Belgeler](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Yazdırmaya Genel Bakış](../../../../docs/framework/wpf/advanced/printing-overview.md)
