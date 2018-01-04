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
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 9b59f85eb0ef6646345eaef2a409f622c6fe4651
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="namespace-affect-on-entity-reference-expansion-for-new-nodes-containing-elements-and-attributes"></a>Namespace güncelleştirmedikçe öğeleri ve öznitelikleri içeren yeni düğüm için varlık başvurusu genişletme
Bir varlık bildiriminin içeriği neredeyse her şeyi içerebileceğinden içeriği gibi bir öğe içerebilir olasılığı yok `<!ENTITY aname "<elem>test</elem>">`.  
  
 XML ayrıştırıldığında `&aname;` değiştirme içeriğini ayrıştırma zamanında genişletilmiş değil. Düğümün belgede yerleştirilen kadar öğe için bir ad çözümlemesini gerçekleşemez çünkü XML genişletme yapılmadı. O zamana kadar hangi ad alanı kapsamında olup hiçbir bilgisi yoktur. Düğüm belgeye geçirdiğinizde, ad çözümlemesi oluşur ve içerik sonuç varlık uygun düğümlerinden ayrıştırılır.  
  
> [!NOTE]
>  Yeni oluşturulan varlık başvurusu düğümde genişletme oluşur sonra hiçbir zaman oluşana. Bu nedenle, öğe için değiştirme metinde kullanılan ad alanları üst düğüm kümesi aynı anda bağlanır. Ad alanı kaldırdığınızda ve başka bir yere yerleştirin varolan varlık başvurusu düğümleri için veya ile kopyalanması varlık başvurusu düğümlerde ancak değiştirilebilir **CloneNode** yöntemi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
