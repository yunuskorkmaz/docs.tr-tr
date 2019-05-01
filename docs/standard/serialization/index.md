---
title: .NET içinde serileştirme
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, defined
- binary serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
ms.openlocfilehash: e05d358452a247b0d071f78d19c0bf721502899a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62018040"
---
# <a name="serialization-in-net"></a>.NET içinde serileştirme
Serileştirme kalıcı veya taşınan bir forma bir nesne durumunu dönüştürme işlemidir. Serileştirme tamamlayıcı bir akış bir nesneye dönüştürür seri kaldırma ' dir. Birlikte, bu işlemleri kolayca depolanan ve aktarılan veriler izin vermiyor.  
  
İki serileştirme teknoloji .NET özellikleri:  
  
- Bir uygulamanın farklı çağrılarını arasında bir nesne durumunu korumak için kullanışlıdır türü uygunluk, ikili serileştirme korur. Örneğin, bir nesne panoya serileştirmek tarafından farklı uygulamalar arasında paylaşabilirsiniz. Bir nesneyi bir akışa, diske, bellek, ağ üzerinden seri hale getirmek ve VS. Uzaktan iletişim serileştirme "değeri tarafından" nesnelerini geçirmek için bir bilgisayar veya uygulama etki alanından diğerine kullanır.  
  
- XML serileştirme yalnızca ortak özellikler ve alanları serileştirir ve türü kalitesini korumak değil. Sağlayın ya da söz konusu verileri kullanan uygulamayı kısıtlamadan veri tüketmek istediğinizde bu kullanışlıdır. XML açık bir standart olduğu için veri Web'de paylaşma çekici bir seçimdir. SOAP benzer şekilde, çekici bir seçim kolaylaştıracak açık bir standart olan.  
  
## <a name="in-this-section"></a>Bu Bölümde  
[Serileştirme ile İlgili Nasıl Yapılır Konuları](../../../docs/standard/serialization/serialization-how-to-topics.md)  
Bu bölümde bulunan nasıl yapılır konulara bağlantılar listeler.
  
[İkili Serileştirme](../../../docs/standard/serialization/binary-serialization.md)  
Ortak dil çalışma zamanı ile içerdiği ikili serileştirme mekanizması açıklanmaktadır.

[XML ve SOAP Serileştirme](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
Ortak dil çalışma zamanı ile içerdiği XML ve SOAP serileştirme mekanizması açıklanmaktadır.

[Serileştirme Araçları](../../../docs/standard/serialization/serialization-tools.md)  
Bu araçlar serileştirme kod geliştirmelerine yardımcı olur.

[Serileştirme Örnekleri](../../../docs/standard/serialization/serialization-samples.md)  
Örnekler serileştirme yapmak nasıl gösterir.

## <a name="reference"></a>Başvuru
<xref:System.Runtime.Serialization> Seri hale getirme ve seri kaldırma nesneler için kullanılan sınıfları içerir.
  
<xref:System.Xml.Serialization>  
XML biçimi belgeleri ya da akış nesneleri serileştirmek için kullanılan sınıfları içerir.