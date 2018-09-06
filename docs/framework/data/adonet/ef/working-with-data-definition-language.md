---
title: Veri tanımlama dili ile çalışma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec50083d-44f4-4093-9b23-5eacd601f96e
ms.openlocfilehash: 25d7f49644996d87ddb5d191dc313916c0ca6fbb
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44037168"
---
# <a name="working-with-data-definition-language"></a>Veri tanımlama dili ile çalışma
İle başlayarak [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] sürüm 4, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] veri tanımlama dili (DDL) destekler. Bu, oluşturmak veya bağlantı dizesi ve depolama (SSDL) model meta verilerini temel alan bir veritabanı örneğini silmek sağlar.  
  
 Aşağıdaki yöntemlerden <xref:System.Data.Objects.ObjectContext> aşağıdakileri gerçekleştirmek için bağlantı dizesini ve SSDL içeriği kullanın: oluşturun veya veritabanını silin, veritabanı var ve oluşturulan DDL betiğini görüntüle olup olmadığını denetleyin:  
  
-   <xref:System.Data.Objects.ObjectContext.CreateDatabase%2A>  
  
-   <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A>  
  
-   <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A>  
  
-   <xref:System.Data.Objects.ObjectContext.CreateDatabaseScript%2A>  
  
> [!NOTE]
>  DDL komutları yürütmeden yeterli izinlere varsayar.  
  
 Daha önce listelenen yöntemlerden istediğinizi çoğunu alttaki ADO.NET veri sağlayıcı için temsilci. Veritabanı nesneleri oluşturmak için kullanılan adlandırma kuralı sorgulamak için kullanılan kuralları ile tutarlı olmasını sağlamak üzere sağlayıcısının sorumluluğundadır ve güncelleştirir.  
  
 Aşağıdaki örnek mevcut modelini temel alan bir veritabanı oluşturmayı gösterir. Ayrıca nesne bağlamı için yeni bir varlık nesnesi ekler ve sonra veritabanına kaydeder.  
  
## <a name="procedures"></a>Yordamlar  
  
#### <a name="to-define-a-database-based-on-the-existing-model"></a>Mevcut modelini temel alan bir veritabanı tanımlamak için  
  
1.  Bir konsol uygulaması oluşturun.  
  
2.  Mevcut bir model uygulamanıza ekleyin.  
  
    1.  Adlı boş bir model ekleme `SchoolModel`. Boş bir model oluşturmak için bkz [nasıl yapılır: yeni bir .edmx dosyası oluşturma](https://msdn.microsoft.com/library/beb8189e-e51c-4051-839c-9902c224abf2) konu.  
  
     SchoolModel.edmx dosyası projenize eklenir.  
  
    1.  Kavramsal, depolama kopyalayın ve eşleme içeriği Okul modeli [Okul modeli](https://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac) konu.  
  
    2.  SchoolModel.edmx dosyasını açın ve içeriği yapıştırın `edmx:Runtime` etiketler.  
  
3.  Aşağıdaki kodu ana işlevinize ekleyin. Kod, veritabanı sunucunuza DDL betik veritabanı oluşturur, yeni bir varlık için bir bağlam eklenmiştir ve değişiklikleri veritabanına kaydeder görünümleri bağlantı dizesini başlatır.  
  
     [!code-csharp[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/csharp/VS_Snippets_Data/DP ObjectServices Concepts/CS/Source.cs#ddl)]
     [!code-vb[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP ObjectServices Concepts/VB/Source.vb#ddl)]
