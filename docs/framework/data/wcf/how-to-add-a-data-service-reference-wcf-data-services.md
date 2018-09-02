---
title: 'Nasıl yapılır: bir veri hizmeti başvurusu (WCF Veri Hizmetleri) ekleme'
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 62c6f318-3ee1-433a-b7a3-efa234c3034c
ms.openlocfilehash: fc1786e1c6102c702374989253cd3ce23e3f7b54
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43404429"
---
# <a name="how-to-add-a-data-service-reference-wcf-data-services"></a>Nasıl yapılır: bir veri hizmeti başvurusu (WCF Data Services) ekleme

Kullanabileceğiniz **hizmet Başvurusu Ekle** WCF Veri Hizmetleri için bir başvuru eklemek için Visual Studio'da iletişim kutusu. Bu, Visual Studio'da geliştirdiğiniz bir istemci uygulamasında veri hizmeti daha kolay erişmenizi sağlar. Bu yordamı tamamladıktan sonra veri sınıfları, veri hizmetinden alınan meta verileri oluşturulur. Daha fazla bilgi için [veri hizmeti istemci kitaplığı oluşturma](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md).

## <a name="add-a-data-service-reference"></a>Bir veri hizmeti başvurusu ekleme

1. (İsteğe bağlı) Veri Hizmeti çözümün bir parçası değil ve çalışır durumda değil, veri hizmeti başlatın ve veri hizmeti URI'sini not edin.

2. Visual Studio içinde **Çözüm Gezgini**, istemci projeye sağ tıklayın ve ardından **Ekle** > **hizmet başvurusu**.

3. Veri Hizmeti geçerli çözümün bir parçası ise, tıklayın **bulma**.

     veya

     İçinde **adresi** metin kutusuna, veri hizmetinin temel URL'sini yazın gibi `http://localhost:1234/Northwind.svc`ve ardından **Git**.

4. Seçin **Tamam**.

     Erişebilir ve veri hizmeti kaynaklarına ile etkileşimli veri sınıfları içeren yeni bir kod dosyası projeye eklenir.

## <a name="see-also"></a>Ayrıca bkz.

- [Hızlı başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)