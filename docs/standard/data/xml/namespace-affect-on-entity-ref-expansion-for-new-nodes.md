---
title: "Namespace güncelleştirmedikçe öğeleri ve öznitelikleri içeren yeni düğüm için varlık başvurusu genişletme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 64359aee-aab0-4042-9a32-d19789af6ca7
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 39110a9b44e6efbe7ad0331cfdb4fbe6078e7cfc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="namespace-affect-on-entity-reference-expansion-for-new-nodes-containing-elements-and-attributes"></a>Namespace güncelleştirmedikçe öğeleri ve öznitelikleri içeren yeni düğüm için varlık başvurusu genişletme
Bir varlık bildiriminin içeriği neredeyse her şeyi içerebileceğinden içeriği gibi bir öğe içerebilir olasılığı yok `<!ENTITY aname "<elem>test</elem>">`.  
  
 XML ayrıştırıldığında `&aname;` değiştirme içeriğini ayrıştırma zamanında genişletilmiş değil. Düğümün belgede yerleştirilen kadar öğe için bir ad çözümlemesini gerçekleşemez çünkü XML genişletme yapılmadı. O zamana kadar hangi ad alanı kapsamında olup hiçbir bilgisi yoktur. Düğüm belgeye geçirdiğinizde, ad çözümlemesi oluşur ve içerik sonuç varlık uygun düğümlerinden ayrıştırılır.  
  
> [!NOTE]
>  Yeni oluşturulan varlık başvurusu düğümde genişletme oluşur sonra hiçbir zaman oluşana. Bu nedenle, öğe için değiştirme metinde kullanılan ad alanları üst düğüm kümesi aynı anda bağlanır. Ad alanı kaldırdığınızda ve başka bir yere yerleştirin varolan varlık başvurusu düğümleri için veya ile kopyalanması varlık başvurusu düğümlerde ancak değiştirilebilir **CloneNode** yöntemi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML belge nesne modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
