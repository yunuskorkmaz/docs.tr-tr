---
title: Okuyucudan Veri Yükleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 7e74918c-bc72-4977-a49b-e1520a6d8f60
ms.openlocfilehash: 1c048b08380bebce3a627670d88ff6ae48084535
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289167"
---
# <a name="load-data-from-a-reader"></a>Okuyucudan Veri Yükleme
Bir XML belgesi <xref:System.Xml.XmlDocument.Load%2A> yöntemi ve bir parametresi kullanılarak yüklenirse <xref:System.Xml.XmlReader> , diğer biçimlerden verileri yükleme davranışına kıyasla oluşan davranışta farklılıklar vardır. Okuyucu ilk durumundaysa, <xref:System.Xml.XmlDocument.Load%2A> tüm içeriği okuyucudan kullanır ve okuyucudaki tüm VERILERDEN XML belge nesne modeli (DOM) oluşturur.  
  
 Okuyucu, belgenin herhangi bir yerinde zaten bir düğüm üzerinde konumlandırılmışsa ve ardından dönüştürme <xref:System.Xml.XmlDocument.Load%2A> yöntemine geçtiğinde, geçerli <xref:System.Xml.XmlDocument.Load%2A> bir üst etikete kadar, geçerli derinliği belleğe kapatan bitiş etiketine kadar geçerli düğümü ve tüm eşdüzey düzeylerini okumaya çalışır. Denenen işlemin başarısı, <xref:System.Xml.XmlDocument.Load%2A> Yük denendiğinde okuyucunun üzerinde bulunduğu düğüme bağlıdır, <xref:System.Xml.XmlDocument.Load%2A> OKUYUCUDAN XML 'nin doğru biçimlendirildiğini doğrular. XML doğru biçimlendirilmemiş ise <xref:System.Xml.XmlDocument.Load%2A> bir özel durum oluşturur. Örneğin, aşağıdaki düğüm kümesi iki kök düzeyi öğe içerir, XML doğru biçimlendirilmemiş ve <xref:System.Xml.XmlDocument.Load%2A> bir özel durum oluşturur.  
  
- Açıklama düğümü, ardından bir öğe düğümü, ardından bir öğesi düğümü, ve ardından bir EndElement düğümü.  
  
 Aşağıdaki düğüm kümesi, kök düzeyinde bir öğe olmadığından tamamlanmamış bir DOM oluşturuyor.  
  
- Açıklama düğümü ve ardından bir işlem yönergesi düğümü ve ardından bir EndElement düğümü gelen bir açıklama düğümü gelir.  
  
 Bu, bir özel durum oluşturmaz ve veri yüklenir. Bu düğümlerin üst kısmına bir kök öğesi ekleyebilir ve hatasız kaydedilebilecek, düzgün biçimlendirilmiş bir XML oluşturabilirsiniz.  
  
 Okuyucu, bir belgenin kök düzeyi (örneğin, bir boşluk veya öznitelik düğümü) için geçersiz olan bir yaprak düğümde konumlandırılmışsa, bu,, kök için kullanılabilecek bir düğüme yerleştirilene kadar okumaya devam eder. Belge bu noktada yüklenmeye başlıyor.  
  
 Varsayılan olarak, <xref:System.Xml.XmlDocument.Load%2A> XML 'nin belge türü tanımı (DTD) veya şema doğrulaması kullanarak geçerli olup olmadığını doğrulamaz. Yalnızca XML 'nin düzgün biçimlendirilmiş olup olmadığını doğrular. Doğrulamanın gerçekleşmesi için, <xref:System.Xml.XmlReader> sınıfını kullanarak oluşturmanız gerekir <xref:System.Xml.XmlReaderSettings> . <xref:System.Xml.XmlReader>Sınıfı, BIR DTD veya şema tanım dili (xsd) şeması kullanarak doğrulamayı zorlayabilir. <xref:System.Xml.ValidationType>Sınıftaki özelliği, <xref:System.Xml.XmlReaderSettings> <xref:System.Xml.XmlReader> Örneğin doğrulamayı zorluyor olduğunu belirler. XML verilerini doğrulama hakkında daha fazla bilgi için başvuru sayfasının açıklamalar bölümüne bakın <xref:System.Xml.XmlReader> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](xml-document-object-model-dom.md)
