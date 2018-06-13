---
title: Projedeki XML şemaları derlenirken hataları oluştu
ms.date: 07/20/2015
f1_keywords:
- bc36810
- vbc36810
helpviewer_keywords:
- BC36810
ms.assetid: 9323b5d2-ba14-4e49-91f1-9ad647162144
ms.openlocfilehash: 0cc565809792c619ca9903f9ef9b029b51a8aa17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588268"
---
# <a name="errors-occurred-while-compiling-the-xml-schemas-in-the-project"></a>Projedeki XML şemaları derlenirken hataları oluştu
Projedeki XML şemaları derlenirken hataları oluştu. Bu nedenle, XML IntelliSense'i kullanılabilir değil.  
  
 Projeye dahil bir XML şema tanımı (XSD) şemasında bir hata var. Varolan XSD şema çakışmalarını proje için ayarlanmış bir XSD şema (.xsd) dosyası eklediğinizde, bu hata oluşur.  
  
 **Hata Kimliği:** BC36810  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Uyarı çift **hata listesine** penceresi. Visual Basic Uyarı kaynağı XSD dosyası konumu için yönlendirir. XSD şemasında hatayı düzeltin.  
  
-   Tüm gerekli XSD şema (.xsd) dosyaları projeye dahil emin olun. ' İ tıklatmanız gerekir **tüm dosyaları göster** üzerinde **proje** , .xsd görmek için menü dosyaları **Çözüm Gezgini**. Bir .xsd dosyasını sağ tıklatın ve ardından **projeye dahil et** dosyayı projenize eklemek için.  
  
-   XML ve şema Sihirbazı kullanıyorsanız, aynı kaynaktan birden fazla kez şemaları Infer bu hata oluşabilir. Bu durumda, varolan XSD şema dosyaları projeden kaldırmak eklemek yeni bir XML Şeması öğe şablonu için ve XML şema Sihirbazı'na tüm geçerli XML kaynaklarıyla projeniz için belirtin.  
  
-   XSD şemasında yok hatası belirlenirse, XML derleyici ayrıntılı hata iletisi sağlamak için yeterli bilgiye sahip olmayabilir. XML ad alanları .xsd dosyaları için Visual Studio'da ayarlayın XML şeması için tanımlanan XML ad alanları, proje eşlemesinde dahil olmak değilse daha ayrıntılı hata bilgileri almak mümkün olabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Listesi Penceresi](/visualstudio/ide/reference/error-list-window)  
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)
