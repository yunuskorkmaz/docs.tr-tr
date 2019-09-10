---
title: Veri Tanımlama Dili ile Çalışma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec50083d-44f4-4093-9b23-5eacd601f96e
ms.openlocfilehash: 83d6fc1294f6aa37389db9e517b02866ef000b50
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854231"
---
# <a name="working-with-data-definition-language"></a>Veri Tanımlama Dili ile Çalışma
.NET Framework sürüm 4 ' te başlayarak, Entity Framework veri tanımlama dili 'ni (DDL) destekler. Bu, bağlantı dizesini ve depolama (SSDL) modelinin meta verilerini temel alarak bir veritabanı örneği oluşturmanıza veya silmesine izin verir.  
  
 Aşağıdaki yöntemler, <xref:System.Data.Objects.ObjectContext> aşağıdakileri gerçekleştirmek için bağlantı dizesini ve SSDL içeriğini kullanır: veritabanını oluşturun veya silin, veritabanının mevcut olup olmadığını denetleyin ve oluşturulan DDL betiğini görüntüleyin:  
  
- <xref:System.Data.Objects.ObjectContext.CreateDatabase%2A>  
  
- <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A>  
  
- <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A>  
  
- <xref:System.Data.Objects.ObjectContext.CreateDatabaseScript%2A>  
  
> [!NOTE]
> DDL komutlarının yürütülmesi yeterli izinleri varsaymaktadır.  
  
 Daha önce, temel alınan ADO.NET veri sağlayıcısı üzerinde çalışmanın büyük bir kısmını temsil eden yöntemler. Veritabanı nesneleri oluşturmak için kullanılan adlandırma kuralının, sorgulama ve güncelleştirme için kullanılan kurallara uygun olduğundan emin olmak sağlayıcının sorumluluğundadır.  
  
 Aşağıdaki örnek, var olan modele göre veritabanının nasıl oluşturulacağını gösterir. Ayrıca, nesne bağlamına yeni bir varlık nesnesi ekler ve sonra veritabanına kaydeder.  
  
## <a name="procedures"></a>Yordamlar  
  
### <a name="to-define-a-database-based-on-the-existing-model"></a>Mevcut modele göre bir veritabanı tanımlamak için  
  
1. Konsol uygulaması oluşturun.  
  
2. Uygulamanıza var olan bir modeli ekleyin.  
  
    1. Adlı `SchoolModel`boş bir model ekleyin. Boş bir model oluşturmak için bkz [. nasıl yapılır: Yeni bir. edmx dosyası](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100)) oluşturma konusu.  
  
     SchoolModel. edmx dosyası projenize eklenir.  
  
    1. Okul modeline ait kavramsal, depolama ve eşleme içeriğini [okul modeli](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) konusundan kopyalayın.  
  
    2. SchoolModel. edmx dosyasını açın ve içeriği `edmx:Runtime` Etiketler içine yapıştırın.  
  
3. Ana işlevinizde aşağıdaki kodu ekleyin. Kod, bağlantı dizesini veritabanı sunucunuza başlatır, DDL betiğini görüntüler, veritabanını oluşturur, içeriğe yeni bir varlık ekler ve değişiklikleri veritabanına kaydeder.  
  
     [!code-csharp[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/csharp/VS_Snippets_Data/DP ObjectServices Concepts/CS/Source.cs#ddl)]
     [!code-vb[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP ObjectServices Concepts/VB/Source.vb#ddl)]
