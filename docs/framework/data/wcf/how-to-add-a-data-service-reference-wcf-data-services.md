---
title: 'Nasıl yapılır: Veri hizmeti başvurusu ekleme (WCF Veri Hizmetleri)'
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 62c6f318-3ee1-433a-b7a3-efa234c3034c
ms.openlocfilehash: 42d89cf87b5fe9bbdb229f10cd6a0e340d4c08fd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790745"
---
# <a name="how-to-add-a-data-service-reference-wcf-data-services"></a>Nasıl yapılır: Veri hizmeti başvurusu ekleme (WCF Veri Hizmetleri)

WCF Veri Hizmetleri bir başvuru eklemek için Visual Studio 'daki **hizmet başvurusu Ekle** iletişim kutusunu kullanabilirsiniz. Bu, Visual Studio 'da geliştirdiğiniz bir istemci uygulamasındaki veri hizmetine daha kolay erişmenizi sağlar. Bu yordamı tamamladığınızda veri sınıfları, veri hizmetinden alınan meta veriler temel alınarak oluşturulur. Daha fazla bilgi için bkz. [veri hizmeti Istemci kitaplığı oluşturma](generating-the-data-service-client-library-wcf-data-services.md).

## <a name="add-a-data-service-reference"></a>Veri hizmeti başvurusu ekleme

1. Seçim Veri hizmeti çözümün bir parçası değilse ve çalışır durumda değilse, veri hizmetini başlatın ve veri hizmetinin URI 'sini not edin.

2. Visual Studio 'da, **Çözüm Gezgini**, istemci projesine sağ tıklayın ve ardından**hizmet başvurusu** **Ekle** > ' yi seçin.

3. Veri hizmeti geçerli çözümün parçasıysa **bul**' a tıklayın.

     -veya-

     **Adres** metin kutusuna veri hizmetinin temel URL 'sini yazın (gibi `http://localhost:1234/Northwind.svc`) ve ardından **Git**' e tıklayın.

4. **Tamam**’ı seçin.

     Veri hizmeti kaynaklarıyla erişebilen ve bunlarla etkileşime girebilen veri sınıflarını içeren yeni bir kod dosyası projeye eklenir.

## <a name="see-also"></a>Ayrıca bkz.

- [Hızlı başlangıç](quickstart-wcf-data-services.md)
