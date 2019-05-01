---
title: Öğe ve Öznitelikler İçeren Yeni Düğümler için Varlık Başvurusu Genişlemesine Ad Alanı Etkisi
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 64359aee-aab0-4042-9a32-d19789af6ca7
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4231516848cc50212a3a6a03d101907b2f6b3920
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62027114"
---
# <a name="namespace-affect-on-entity-reference-expansion-for-new-nodes-containing-elements-and-attributes"></a>Öğe ve Öznitelikler İçeren Yeni Düğümler için Varlık Başvurusu Genişlemesine Ad Alanı Etkisi
Bir varlık bildiriminin içeriği neredeyse her şeyi içerebileceğinden, içeriği gibi bir öğe içerebilecek bir olasılık yoktur `<!ENTITY aname "<elem>test</elem>">`.  
  
 XML ayrıştırıldığında `&aname;` değiştirme içeriğini ayrıştırma zamanında genişletilmemiştir. Genişletme XML belgesine düğüm yerleştirilir kadar öğe için ad çözümleme olamaz çünkü yapılmaz. O zamana kadar hangi ad alanı kapsamında olduğu bilgisi yoktur. Düğüm belgeye yerleştirdiğinizde, ardından ad çözümlemesi gerçekleşir ve sonuç varlık içeriği uygun düğümlerini ayrıştırılır.  
  
> [!NOTE]
>  Yeni oluşturulan varlık başvurusu düğümde genişletme gerçekleşir sonra hiçbir zaman yeniden. Bu nedenle, değiştirme metni öğe için kullanılan ad alanları üst düğüm kümesi zamanında bağlıdır. Ad alanı çıkarıp başka bir yere yerleştirin, mevcut varlık başvurusu düğümleri için veya ile kopyalanan varlık başvurusu düğümlerinde ancak değiştirilebilir **CloneNode** yöntemi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
