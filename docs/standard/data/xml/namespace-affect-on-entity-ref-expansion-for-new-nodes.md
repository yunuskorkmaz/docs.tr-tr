---
title: Öğeler ve öznitelikler içeren yeni düğümler için varlık başvurusu genişlemesine Namespace etkiler
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 64359aee-aab0-4042-9a32-d19789af6ca7
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4231516848cc50212a3a6a03d101907b2f6b3920
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44511269"
---
# <a name="namespace-affect-on-entity-reference-expansion-for-new-nodes-containing-elements-and-attributes"></a>Öğeler ve öznitelikler içeren yeni düğümler için varlık başvurusu genişlemesine Namespace etkiler
Bir varlık bildiriminin içeriği neredeyse her şeyi içerebileceğinden, içeriği gibi bir öğe içerebilecek bir olasılık yoktur `<!ENTITY aname "<elem>test</elem>">`.  
  
 XML ayrıştırıldığında `&aname;` değiştirme içeriğini ayrıştırma zamanında genişletilmemiştir. Genişletme XML belgesine düğüm yerleştirilir kadar öğe için ad çözümleme olamaz çünkü yapılmaz. O zamana kadar hangi ad alanı kapsamında olduğu bilgisi yoktur. Düğüm belgeye yerleştirdiğinizde, ardından ad çözümlemesi gerçekleşir ve sonuç varlık içeriği uygun düğümlerini ayrıştırılır.  
  
> [!NOTE]
>  Yeni oluşturulan varlık başvurusu düğümde genişletme gerçekleşir sonra hiçbir zaman yeniden. Bu nedenle, değiştirme metni öğe için kullanılan ad alanları üst düğüm kümesi zamanında bağlıdır. Ad alanı çıkarıp başka bir yere yerleştirin, mevcut varlık başvurusu düğümleri için veya ile kopyalanan varlık başvurusu düğümlerinde ancak değiştirilebilir **CloneNode** yöntemi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
