---
title: 'Nasıl yapılır: varolan bir hizmet sözleşmesini tüketen bir iş akışı hizmeti oluşturma'
ms.date: 03/30/2017
ms.assetid: 11d11b59-acc4-48bf-8e4b-e97b516aa0a9
ms.openlocfilehash: 146b3bba3a880c780644eecd277827823793b5e8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515311"
---
# <a name="how-to-create-a-workflow-service-that-consumes-an-existing-service-contract"></a>Nasıl yapılır: varolan bir hizmet sözleşmesini tüketen bir iş akışı hizmeti oluşturma
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] özellikleri daha iyi web hizmetleri ve iş akışları sözleşme ilk iş akışı geliştirme biçiminde arasında tümleştirme. Sözleşme ilk iş akışı geliştirme aracı kod sözleşmede ilk tasarlamanızı sağlar. Araç ardından otomatik olarak bir etkinlik şablonu sözleşmesindeki işlemleri için araç kutusu oluşturur.  
  
> [!NOTE]
>  Bu konu, bir sözleşme ilk iş akışı hizmeti oluşturma ile ilgili adım adım yönergeler sağlar. Önce anlaşma iş akışı hizmeti geliştirme hakkında daha fazla bilgi için bkz: [sözleşme ilk iş akışı hizmeti geliştirme](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md).  
  
### <a name="creating-the-workflow-project"></a>İş akışı projesi oluşturma  
  
1.  Visual Studio'da seçin **dosya**, **yeni proje**. Seçin **WCF** düğümü altında **C#** düğümünde **şablonları** ağacı ve seçin **WCF iş akışı hizmeti uygulaması** şablonu.  
  
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
