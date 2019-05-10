---
title: Okuyucudan Veri Yükleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 7e74918c-bc72-4977-a49b-e1520a6d8f60
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e4b789a23b790757ce2dfaa82b6eaec7fdaf3cb3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647876"
---
# <a name="load-data-from-a-reader"></a>Okuyucudan Veri Yükleme
Bir XML belgesi kullanarak yüklü ise <xref:System.Xml.XmlDocument.Load%2A> yöntemi ve parametre olarak bir <xref:System.Xml.XmlReader>, diğer biçimlerinden veri yükleme davranışını karşılaştırıldığında ortaya çıkan davranış farkları vardır. Okuyucu, başlangıç durumunda ise <xref:System.Xml.XmlDocument.Load%2A> okuyucudan tüm içeriğini tüketir ve XML belge nesne modeli (DOM) tüm verileri okuyucu oluşturur.  
  
 Okuyucu belgedeki bir düğümde konumlandırılır ve okuyucu geçirilerek <xref:System.Xml.XmlDocument.Load%2A> yöntemi <xref:System.Xml.XmlDocument.Load%2A> geçerli düğüm ve tüm geçerli derinlik belleğe kapatır bitiş etiketi adede kadar eş değerleri okumaya çalışır. Denenen başarısını <xref:System.Xml.XmlDocument.Load%2A> yük çalışırken, okuyucu açık olan düğüme bağlıdır olarak <xref:System.Xml.XmlDocument.Load%2A> okuyucudan XML doğru biçimlendirilmemiş olduğunu doğrular. Doğru biçimlendirilmiş XML değilse <xref:System.Xml.XmlDocument.Load%2A> bir özel durum oluşturur. Örneğin, aşağıdaki düğümleri kümesini içeren iki kök düzeyinde öğe, doğru biçimlendirilmiş XML değil ve <xref:System.Xml.XmlDocument.Load%2A> bir özel durum oluşturur.  
  
- Ardından bir EndElement düğümü tarafından izlenen bir öğe düğümü arkasından bir öğe düğümü, açıklama düğümü.  
  
 Herhangi bir kök düzeyinde öğe olduğundan aşağıdaki dizi düğümü eksik bir DOM oluşturur.  
  
- Açıklama düğümü bir EndElement düğümü tarafından izlenen bir açıklama düğümü ardından instruction bir düğüm tarafından izlenen.  
  
 Verileri yüklendi ve bir özel durum oluşturmaz. Bu düğümler üst bir kök öğe ekleyin ve hata kaydedilebilir iyi biçimlendirilmiş bir XML dosyası oluşturmak.  
  
 Okuyucu için (örneğin, bir beyaz boşluk veya öznitelik düğümü) belgenin kök düzeyinde geçersiz bir yaprak düğüm üzerinde konumlandırıldı, bunu konumlandırılmış kadar okumak okuyucu devam bir düğümdeki kök için kullanılabilir. Belge, bu noktada yüklemeye başlar.  
  
 Varsayılan olarak, <xref:System.Xml.XmlDocument.Load%2A> XML belge türü tanımı (DTD'nin) veya şema doğrulaması kullanarak geçerli olup olmadığını doğrulamaz. Yalnızca XML iyi biçimlendirilmiş olup olmadığını doğrular. Doğrulama gerçekleşmesi için sırada oluşturmanız gerekir. bir <xref:System.Xml.XmlReader> kullanarak <xref:System.Xml.XmlReaderSettings> sınıfı. <xref:System.Xml.XmlReader> Sınıfı bir DTD'nin veya şema tanım dili (XSD) şeması kullanarak doğrulama zorunlu. <xref:System.Xml.ValidationType> Özelliği <xref:System.Xml.XmlReaderSettings> sınıfı belirleyen olmadığını <xref:System.Xml.XmlReader> örnek doğrulama zorlar. XML veri doğrulama hakkında daha fazla bilgi için bkz. Açıklamalar bölümüne <xref:System.Xml.XmlReader> başvuru sayfası.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
