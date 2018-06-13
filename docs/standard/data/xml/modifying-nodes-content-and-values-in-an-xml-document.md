---
title: Düğümler, içerik ve bir XML belgesi değerlerini değiştirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 761773e0-db72-4986-b9f5-a522213d8397
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 716270450a5f0ede545ffcbd906b0a42f547c20f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571442"
---
# <a name="modifying-nodes-content-and-values-in-an-xml-document"></a>Düğümler, içerik ve bir XML belgesi değerlerini değiştirme
Düğümler ve belgedeki içeriği değiştirebilirsiniz birçok yolu vardır. Şunları yapabilirsiniz:  
  
-   Kullanarak düğümler değerini değiştirme <xref:System.Xml.XmlNode.Value%2A> özelliği.  
  
-   Düğümleri kümesinin tamamını düğümleri yeni düğümler ile değiştirerek değiştirin. Bu yapılır kullanarak <xref:System.Xml.XmlNode.InnerXml%2A> özelliği.  
  
-   Varolan düğümleri kullanarak yeni düğümler ile Değiştir <xref:System.Xml.XmlNode.RemoveChild%2A> yöntemi.  
  
-   Devralınan düğümleri ek karakterler eklemek <xref:System.Xml.XmlCharacterData> kullanarak sınıfı <xref:System.Xml.XmlCharacterData.AppendData%2A>, <xref:System.Xml.XmlCharacterData.InsertData%2A>, veya <xref:System.Xml.XmlCharacterData.ReplaceData%2A> yöntemleri.  
  
-   Bir aralıktaki karakterleri kullanarak kaldırarak içeriğini değiştirme <xref:System.Xml.XmlCharacterData.DeleteData%2A> devralınmalıdır düğüm türleri üzerinde yöntemi <xref:System.Xml.XmlCharacterData>.  
  
 Bir düğüm değerini değiştirmek için basit bir teknik kullanmaktır `node.Value = "new value";`. Aşağıdaki tabloda, bu tek satırlık bir kod çalışır düğüm türleri ve bu düğüm türü için hangi verilerin tam olarak değiştirilir listeler.  
  
|Düğüm türü|Değiştirilen veri|  
|---------------|------------------|  
|Öznitelik|Öznitelik değeri.|  
|CDATASection|CDATASection içeriği.|  
|Yorum|Açıklama içeriği.|  
|İnstruction|Hedef hariç içeriği.|  
|Metin|Metnin içeriği.|  
|XmlDeclaration|Bildirim içeriğini hariç `<?xml` ve `?>` biçimlendirme.|  
|Boşluk|Beyaz alan değeri. Dört tanınan XML boşluk karakterleri biri için değer ayarlayabilirsiniz: boşluk, sekme, CR ya da LF.|  
|SignificantWhitespace|Önemli boşluk değeri. Dört tanınan XML boşluk karakterleri biri için değer ayarlayabilirsiniz: boşluk, sekme, CR ya da LF.|  
  
 Tabloda listelenmeyen herhangi bir düğüm türü bir değer ayarlamak için geçerli düğüm türü değil. Başka bir düğüm türü herhangi bir değer ayarlanması oluşturur bir <xref:System.InvalidOperationException>.  
  
 <xref:System.Xml.XmlNode.InnerXml%2A> Geçerli düğüm için alt düğümleri işaretleme özelliğini değiştirir. Bu özelliği ayarlamak alt düğümler verilen dize ayrıştırılmış içeriğiyle değiştirir. Ayrıştırma geçerli ad alanı bağlamında gerçekleştirilir. Ayrıca, <xref:System.Xml.XmlNode.InnerXml%2A> yedek ad alanı bildirimleri kaldırır. Sonuç, çok sayıda kesme ve yapıştırma işlemlerini belgenizin yedek ad alanı bildirimleri ile boyutunu artırmaz gibi. Ad alanları etkisini gösteren kod örneği için <xref:System.Xml.XmlNode.InnerXml%2A> işlemi, bkz: <xref:System.Xml.XmlDocument.InnerXml%2A> özelliği.  
  
 Kullanırken <xref:System.Xml.XmlCharacterData.ReplaceData%2A> ve <xref:System.Xml.XmlNode.RemoveChild%2A> yöntemleri, yöntemleri, değiştirilen veya kaldırılan düğüm döndürür. Bu düğüm sonra herhangi bir yerde başka XML belge nesne modeli (DOM) yeniden. <xref:System.Xml.XmlCharacterData.ReplaceData%2A> Yöntemi belgeye eklenen düğüm üzerinde iki doğrulama denetimlerini yapar. Alt düğümler türüne sahip bir düğümün bir alt düğüm büyüyor ilk denetimi sağlar. İkinci onay eklenen düğüm alt olma düğümünün üst emin olunmasını sağlar. Koşulları atar bunlardan ihlal eden bir <xref:System.InvalidOperationException>.  
  
 Eklemek veya bir salt okunur alt düzenlenebilir bir düğümden kaldırmak için geçerli değil. Ancak, salt okunur düğüm değiştirmeye çalıştığında oluşturur bir <xref:System.InvalidOperationException>. Bunun bir örneğini alt değiştirerek bir <xref:System.Xml.XmlEntityReference> düğümü. Alt salt okunurdur ve değiştirilemez. Yapmaya atar değiştirmek bir <xref:System.InvalidOperationException>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
