---
title: "Nasıl yapılır: varolan bir hizmet sözleşmesini tüketen bir iş akışı hizmeti oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11d11b59-acc4-48bf-8e4b-e97b516aa0a9
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a811609f601e844d55d4173eb94df24701fcc7d8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-workflow-service-that-consumes-an-existing-service-contract"></a>Nasıl yapılır: varolan bir hizmet sözleşmesini tüketen bir iş akışı hizmeti oluşturma
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]özellikleri daha iyi web hizmetleri ve iş akışları sözleşme ilk iş akışı geliştirme biçiminde arasında tümleştirme. Sözleşme ilk iş akışı geliştirme aracı kod sözleşmede ilk tasarlamanızı sağlar. Araç ardından otomatik olarak bir etkinlik şablonu sözleşmesindeki işlemleri için araç kutusu oluşturur.  
  
> [!NOTE]
>  Bu konu, bir sözleşme ilk iş akışı hizmeti oluşturma ile ilgili adım adım yönergeler sağlar. [!INCLUDE[crabout](../../../includes/crabout-md.md)]önce anlaşma iş akışı hizmeti geliştirme bkz [sözleşme ilk iş akışı hizmeti geliştirme](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md).  
  
### <a name="creating-the-workflow-project"></a>İş akışı projesi oluşturma  
  
1.  İçinde [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)]seçin **dosya**, **yeni proje**. Seçin **WCF** düğümü altında **C#** düğümünde **şablonları** ağacı ve seçin **WCF iş akışı hizmeti uygulaması** şablonu.  
  
2.  Yeni proje adı `ContractFirst` tıklatıp **Tamam**.  
  
### <a name="creating-the-service-contract"></a>Hizmet sözleşmesi oluşturma  
  
1.  ' Nde projeye sağ **Çözüm Gezgini** seçip **Ekle**, **yeni öğe...** . Seçin **kod** sol düğümünde ve **sınıfı** sağdaki şablonu. Yeni sınıf `IBookService` tıklatıp **Tamam**.  
  
2.  Görüntülenen kodu penceresi üst kullanma deyimine `System.Servicemodel`.  
  
    ```  
    using System.ServiceModel;  
    ```  
  
3.  Örnek sınıf tanımını aşağıdaki arabirimi tanımını değiştirin.  
  
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
  
### <a name="importing-the-service-contract"></a>Hizmet sözleşmesi içeri aktarma  
  
1.  ' Nde projeye sağ **Çözüm Gezgini** seçip **alma hizmet sözleşmesini**. Altında  **\<geçerli Proje >**, tüm alt düğümleri açıp seçin **IBookService**. **Tamam**'ı tıklatın.  
  
2.  Bu işlemi başarıyla tamamlandı ve Projeyi derledikten sonra görünecek oluşturulan etkinlikler Araç Kutusu'nda uyarı bir iletişim kutusu açılır. **Tamam**'ı tıklatın.  
  
3.  Tuşuna basarak projeyi oluşturun **Ctrl + Shift + B**, böylece içeri aktarılan etkinlikler araç kutusu'nda görünür.  
  
4.  İçinde **Çözüm Gezgini**, Service1.xamlx açın. İş akışı hizmeti Tasarımcısı'nda görünür.  
  
5.  Seçin **dizisi** etkinlik. Özellikler penceresinde **...** düğmesini **ImplementedContract** özelliği. İçinde **türü Koleksiyonu Düzenleyicisi** görünen penceresini tıklatın **türü** açılan listesinde seçip **türleri için Gözat...** girişi. İçinde **göz atma ve seçme bir .net türü** iletişim altında  **\<geçerli Proje >**, tüm alt düğümleri açıp seçin **IBookService**. **Tamam**'ı tıklatın. İçinde **türü Koleksiyonu Düzenleyicisi** iletişim kutusunda, tıklatın **Tamam**.  
  
6.  Seçin ve delete **ReceiveRequest** ve **SendResponse** etkinlikler.  
  
7.  Araç Kutusu'ndan sürükleyin bir **Buy_ReceiveAndSendReply** ve **Checkout_Receive** etkinlik üzerine **sıralı hizmet** etkinlik.
