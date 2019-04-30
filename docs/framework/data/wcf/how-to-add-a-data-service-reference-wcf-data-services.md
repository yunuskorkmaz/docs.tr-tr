---
title: 'Nasıl yapılır: Bir veri hizmeti başvurusu (WCF Veri Hizmetleri) ekleme'
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 62c6f318-3ee1-433a-b7a3-efa234c3034c
ms.openlocfilehash: fc1786e1c6102c702374989253cd3ce23e3f7b54
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765537"
---
# <a name="how-to-add-a-data-service-reference-wcf-data-services"></a>Nasıl yapılır: Bir veri hizmeti başvurusu (WCF Data Services) ekleme

Kullanabileceğiniz **hizmet Başvurusu Ekle** WCF Veri Hizmetleri için bir başvuru eklemek için Visual Studio'da iletişim kutusu. Bu, Visual Studio'da geliştirdiğiniz bir istemci uygulamasında veri hizmeti daha kolay erişmenizi sağlar. Bu yordamı tamamladıktan sonra veri sınıfları, veri hizmetinden alınan meta verileri oluşturulur. Daha fazla bilgi için [veri hizmeti istemci kitaplığı oluşturma](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md).

## <a name="add-a-data-service-reference"></a>Bir veri hizmeti başvurusu ekleme

1. (İsteğe bağlı) Veri Hizmeti çözümün bir parçası değil ve çalışır durumda değil, veri hizmeti başlatın ve veri hizmeti URI'sini not edin.

2. Visual Studio içinde **Çözüm Gezgini**, istemci projeye sağ tıklayın ve ardından **Ekle** > **hizmet başvurusu**.

3. Veri Hizmeti geçerli çözümün bir parçası ise, tıklayın **bulma**.

     -veya-

     İçinde **adresi** metin kutusuna, veri hizmetinin temel URL'sini yazın gibi `http://localhost:1234/Northwind.svc`ve ardından **Git**.

4. **Tamam**’ı seçin.

     Erişebilir ve veri hizmeti kaynaklarına ile etkileşimli veri sınıfları içeren yeni bir kod dosyası projeye eklenir.

## <a name="see-also"></a>Ayrıca bkz.

- [Hızlı başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)