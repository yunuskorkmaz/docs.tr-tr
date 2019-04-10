---
title: 'Nasıl yapılır: Yazdırma Sistemi Nesnesi Özelliklerini Yansıma Olmadan Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PrintSystemObject [WPF], getting properties
ms.assetid: 43560f28-183d-41c1-b9d1-de7c2552273e
ms.openlocfilehash: b9ca7444b2c49f4563ff0d7baef8b2d250a7f331
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59215280"
---
# <a name="how-to-get-print-system-object-properties-without-reflection"></a>Nasıl yapılır: Yazdırma Sistemi Nesnesi Özelliklerini Yansıma Olmadan Alma
Bir nesne üzerinde özelliklerini (ve bu özelliklerin türleri) belirtmek için yansıma kullanarak uygulama performansını düşürebilir. <xref:System.Printing.IndexedProperties> Ad alanı, yansıma kullanarak bu bilgileri almak için bir yol sağlar.  
  
## <a name="example"></a>Örnek  
 Bunu yapmak için adımlar aşağıdaki gibidir.  
  
1.  Türün bir örneğini oluşturun. Aşağıdaki örnekte türüdür <xref:System.Printing.PrintQueue> iş öğesinden türetilen türler için Microsoft .NET Framework, ancak neredeyse aynı kod ile birlikte gelen türü <xref:System.Printing.PrintSystemObject>.  
  
2.  Oluşturma bir <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> türün gelen <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A>. <xref:System.Collections.DictionaryEntry.Value%2A> Türlerinden türetilmiş bir nesnenin Bu sözlük her giriş özelliğidir <xref:System.Printing.IndexedProperties.PrintProperty>.  
  
3.  Sözlük üyelerini sıralar. Bunların her biri için aşağıdakileri yapın.  
  
4.  Her giriş için değerini yukarı atama <xref:System.Printing.IndexedProperties.PrintProperty> ve oluşturmak için kullanmak bir <xref:System.Printing.IndexedProperties.PrintProperty> nesne.  
  
5.  Türü alma <xref:System.Printing.IndexedProperties.PrintProperty.Value%2A> her birinin <xref:System.Printing.IndexedProperties.PrintProperty> nesne.  
  
 [!code-csharp[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](~/samples/snippets/csharp/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/CSharp/Program.cs#showpropertytypeswithoutreflection)]
 [!code-vb[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/visualbasic/program.vb#showpropertytypeswithoutreflection)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Printing.IndexedProperties.PrintProperty>
- <xref:System.Printing.PrintSystemObject>
- <xref:System.Printing.IndexedProperties>
- <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>
- <xref:System.Printing.LocalPrintServer>
- <xref:System.Printing.PrintQueue>
- <xref:System.Collections.DictionaryEntry>
- [WPF'deki Belgeler](documents-in-wpf.md)
- [Yazdırmaya Genel Bakış](printing-overview.md)
