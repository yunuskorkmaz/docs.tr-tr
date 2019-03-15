---
title: 'Nasıl yapılır: Mevcut bir hizmet anlaşmasını kullanan iş akışı hizmeti oluşturma'
ms.date: 03/30/2017
ms.assetid: 11d11b59-acc4-48bf-8e4b-e97b516aa0a9
ms.openlocfilehash: 06d4d4f6687979f4fd54e919ca6f236a5b5402e8
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57843014"
---
# <a name="how-to-create-a-workflow-service-that-consumes-an-existing-service-contract"></a>Nasıl yapılır: Mevcut bir hizmet anlaşmasını kullanan iş akışı hizmeti oluşturma
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Özellikler, web hizmetleri ve iş akışları sözleşme öncelikli iş akışı geliştirme biçiminde arasındaki tümleştirme daha iyi. Sözleşme öncelikli iş akışı geliştirme aracı, kod sözleşmede ilk tasarlamak sağlar. Araç ardından otomatik olarak bir etkinlik şablonu sözleşme işlemleri için araç kutusunda oluşturur.  
  
> [!NOTE]
>  Bu konu, bir sözleşme öncelikli iş akışı hizmeti oluşturma ile ilgili adım adım yönergeler sağlar. Sözleşme öncelikli iş akışı hizmet geliştirme hakkında daha fazla bilgi için bkz: [sözleşme ilk iş akışı hizmet geliştirme](contract-first-workflow-service-development.md).  
  
### <a name="creating-the-workflow-project"></a>İş akışı projesi oluşturma  
  
1.  Visual Studio'da **dosya**, **yeni proje**. Seçin **WCF** düğümünde **C#** düğümünde **şablonları** ağaç ve seçin **WCF iş akışı hizmeti uygulaması** şablonu.  
  
2.  Yeni proje adını `ContractFirst` tıklatıp **Tamam**.  
  
### <a name="creating-the-service-contract"></a>Hizmet sözleşmesi oluşturma  
  
1.  Projeye sağ **Çözüm Gezgini** seçip **Ekle**, **yeni öğe...** . Seçin **kod** solda, düğüm ve **sınıfı** sağdaki şablonu. Yeni bir sınıf adı `IBookService` tıklatıp **Tamam**.  
  
2.  Görünen kod penceresinde üst bir Using deyimi ekleyin `System.Servicemodel`.  
  
    ```  
    using System.ServiceModel;  
    ```  
  
3.  Örnek sınıf tanımına aşağıdaki arabirim tanımı için değiştirin.  
  
    ```  
    [ServiceContract]  
        public interface IBookService  
        {  
            [OperationContract]  
            void Buy(string bookName);  
  
            [OperationContract(IsOneWay=true)]  
            void Checkout();  
        }  
    ```  
  
4.  Tuşuna basarak projeyi oluşturun **Ctrl + Shift + B**.  
  
### <a name="importing-the-service-contract"></a>Hizmet sözleşmesi içe aktarılıyor  
  
1.  Projeye sağ **Çözüm Gezgini** seçip **hizmet sözleşmesini içer aktar**. Altında  **\<geçerli Proje >**, tüm alt düğümleri açın ve seçin **IBookService**. **Tamam**'ı tıklatın.  
  
2.  Sizi, işlemi başarıyla tamamlandı ve Projeyi derledikten sonra görünecek oluşturulan etkinlikler araç kutusundan bir iletişim kutusu açılır. **Tamam**'ı tıklatın.  
  
3.  Tuşuna basarak projeyi oluşturun **Ctrl + Shift + B**, böylece içeri aktarılan etkinlikler araç kutusunda görünür.  
  
4.  İçinde **Çözüm Gezgini**, Service1.xamlx açın. İş akışı hizmetinin tasarımcıda görünür.  
  
5.  Seçin **dizisi** etkinlik. Özellikler penceresinde tıklayın **...** düğmesini **ImplementedContract** özelliği. İçinde **Editor Typu Kolekce** penceresine tıklayın **türü** açılır listesinde seçip **vyhledat Typy...** girişi. İçinde **göz atın ve bir .NET türü seçin** iletişim altında  **\<geçerli Proje >**, tüm alt düğümleri açın ve seçin **IBookService**. **Tamam**'ı tıklatın. İçinde **Editor Typu Kolekce** iletişim kutusunda, tıklayın **Tamam**.  
  
6.  Seçip silin **ReceiveRequest** ve **SendResponse** etkinlikler.  
  
7.  Araç kutusundan sürükleyin bir **Buy_ReceiveAndSendReply** ve **Checkout_Receive** üzerine etkinlik **sıralı hizmeti** etkinlik.
