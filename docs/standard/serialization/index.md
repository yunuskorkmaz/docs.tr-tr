---
title: ".NET içinde seri hale getirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML serialization, defined
- binary serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ab8f86b66e92ea250fbe20e8bcb27e6706302db4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="serialization-in-net"></a>.NET içinde seri hale getirme
Seri hale getirme kalıcı veya taşınan bir forma bir nesnenin durumu dönüştürme işlemidir. Seri hale getirme tamamlama bir akış bir nesnesine dönüştürür seri kaldırma ' dir. Birlikte, bu işlemlerin kolayca depolanan ve aktarılan veri izin verin.  
  
.NET iki serileştirme teknolojileri özellikleri:  
  
-   Bir uygulamanın farklı çağrılarını arasında bir nesne durumunu korumak için kullanışlıdır türü uygunluk, ikili serileştirme korur. Örneğin, bir nesne panoya serileştirmek tarafından farklı uygulamalar arasında paylaşabilirsiniz. Nesneyi bir akışa, diske, belleğe, ağ üzerinden seri hale getirmek ve benzeri. Uzaktan iletişim serileştirme "değeri tarafından" nesnelerini geçirmek için bir bilgisayar veya uygulama etki alanından diğerine kullanır.  
  
-   XML serileştirme yalnızca ortak özellikler ve alanları serileştirir ve türü kalitesini korumak değil. Sağlayın veya veriyi kullanan uygulamayı kısıtlamadan veri tüketmek istediğinizde kullanışlıdır. XML açık bir standart olduğundan, Web üzerinden veri paylaşımı için çekici bir seçimdir. SOAP benzer şekilde yayınlayabilirsiniz kolaylaştırır açık bir standart olan.  
  
## <a name="in-this-section"></a>Bu Bölümde  
[Serileştirme Nasıl Yapılır Konuları](../../../docs/standard/serialization/serialization-how-to-topics.md)  
Bu bölümde bulunan nasıl yapılır konulara bağlantılar listeler.
  
[İkili seri hale getirme](../../../docs/standard/serialization/binary-serialization.md)  
Ortak dil çalışma zamanı ile içerdiği ikili serileştirme mekanizması açıklanmaktadır.

[XML ve SOAP seri hale getirme](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
Ortak dil çalışma zamanı ile içerdiği XML ve SOAP serileştirme mekanizması açıklanmaktadır.

[Seri hale getirme araçları](../../../docs/standard/serialization/serialization-tools.md)  
Bu araçlar serileştirme kod geliştirmelerine yardımcı olur.

[Seri hale getirme örnekleri](../../../docs/standard/serialization/serialization-samples.md)  
Örnekler serileştirme nasıl ekleyebileceğiniz gösterilmektedir.

## <a name="reference"></a>Başvuru
<xref:System.Runtime.Serialization>Seri hale getirme ve nesneleri seri durumdan çıkarmak için kullanılan sınıfları içerir.
  
<xref:System.Xml.Serialization>  
XML biçimli belgeler veya akışları nesneleri serileştirmek için kullanılan sınıfları içerir.