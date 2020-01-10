---
title: Okuyucudan Veri Yükleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 7e74918c-bc72-4977-a49b-e1520a6d8f60
ms.openlocfilehash: 90a66e04bda4fb2ee4216e8aabd631afb2f28dd0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710719"
---
# <a name="load-data-from-a-reader"></a>Okuyucudan Veri Yükleme
Bir XML belgesi <xref:System.Xml.XmlDocument.Load%2A> yöntemi ve bir <xref:System.Xml.XmlReader>parametresi kullanılarak yüklenirse, diğer biçimlerden verileri yükleme davranışına kıyasla oluşan davranışta farklılıklar vardır. Okuyucu ilk durumundaysa, <xref:System.Xml.XmlDocument.Load%2A> okuyucudaki tüm içeriği tüketir ve XML Belge Nesne Modeli (DOM) ' ı okuyucudaki tüm verilerden kullanır.  
  
 Okuyucu, belgenin herhangi bir yerinde zaten bir düğümde konumlandırılmışsa ve okuyucu daha sonra <xref:System.Xml.XmlDocument.Load%2A> yöntemine geçirilirse, <xref:System.Xml.XmlDocument.Load%2A> geçerli derinliği ve tüm eşdüzey öğelerinin geçerli derinliğini belleğe kapatan bitiş etiketine kadar okumaya çalışır. Denenen <xref:System.Xml.XmlDocument.Load%2A> başarısı, yük denendiğinde okuyucunun açık olduğu düğüme bağlıdır. <xref:System.Xml.XmlDocument.Load%2A>, okuyucudaki XML 'nin doğru biçimlendirildiğini doğrular. XML doğru biçimlendirilmediyse, <xref:System.Xml.XmlDocument.Load%2A> bir özel durum oluşturur. Örneğin, aşağıdaki düğüm kümesi iki kök düzeyi öğe içerir, XML doğru biçimlendirilmemiş ve <xref:System.Xml.XmlDocument.Load%2A> bir özel durum oluşturur.  
  
- Açıklama düğümü, ardından bir öğe düğümü, ardından bir öğesi düğümü, ve ardından bir EndElement düğümü.  
  
 Aşağıdaki düğüm kümesi, kök düzeyinde bir öğe olmadığından tamamlanmamış bir DOM oluşturuyor.  
  
- Açıklama düğümü ve ardından bir işlem yönergesi düğümü ve ardından bir EndElement düğümü gelen bir açıklama düğümü gelir.  
  
 Bu, bir özel durum oluşturmaz ve veri yüklenir. Bu düğümlerin üst kısmına bir kök öğesi ekleyebilir ve hatasız kaydedilebilecek, düzgün biçimlendirilmiş bir XML oluşturabilirsiniz.  
  
 Okuyucu, bir belgenin kök düzeyi (örneğin, bir boşluk veya öznitelik düğümü) için geçersiz olan bir yaprak düğümde konumlandırılmışsa, bu,, kök için kullanılabilecek bir düğüme yerleştirilene kadar okumaya devam eder. Belge bu noktada yüklenmeye başlıyor.  
  
 Varsayılan olarak, <xref:System.Xml.XmlDocument.Load%2A> XML 'nin belge türü tanımı (DTD) veya şema doğrulaması kullanarak geçerli olup olmadığını doğrulamaz. Yalnızca XML 'nin düzgün biçimlendirilmiş olup olmadığını doğrular. Doğrulamanın gerçekleşmesi için <xref:System.Xml.XmlReaderSettings> sınıfını kullanarak bir <xref:System.Xml.XmlReader> oluşturmanız gerekir. <xref:System.Xml.XmlReader> sınıfı, bir DTD veya şema tanım dili (XSD) şeması kullanarak doğrulamayı zorunlu kılabilir. <xref:System.Xml.XmlReaderSettings> sınıfındaki <xref:System.Xml.ValidationType> özelliği <xref:System.Xml.XmlReader> örneğinin doğrulamayı zorluyor olduğunu belirler. XML verilerini doğrulama hakkında daha fazla bilgi için <xref:System.Xml.XmlReader> başvuru sayfasının açıklamalar bölümüne bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
