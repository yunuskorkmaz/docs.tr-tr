---
title: F# kullanarak Azure Tablo depolama kullanmaya başlama
description: Yapılandırılmış verileri Azure Tablo depolama veya Azure Cosmos DB kullanarak bulutta depolayın.
author: sylvanc
ms.date: 03/26/2018
ms.openlocfilehash: eb25fda0bb3c658eed2f675d6ba79c689a9080a9
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548357"
---
# <a name="get-started-with-azure-table-storage-and-the-azure-cosmos-db-table-api-using-f"></a>F kullanarak Azure Tablo depolama ve Azure Cosmos DB Tablo API'si kullanmaya başlama\#

Azure Table Storage, bulutta yapılandırılmış NoSQL verileri depolayan bir hizmettir. Table Storage, şemasız tasarım ile bir anahtar/öznitelik deposudur. Table Storage şemasız olduğu için uygulamanızın ihtiyaçları geliştikçe verilerinizi kolayca uyarlayabilirsiniz. Her türlü uygulama için verilere erişim hızlı ve uygun maliyetlidir. Table Storage, benzer hacimdeki veriler için geleneksel SQL’e oranla çok daha düşük maliyetlidir.

Web uygulamaları için kullanıcı verileri, adres defterleri, cihaz bilgileri ve hizmetiniz için gerekli olan tüm diğer meta veri türleri gibi esnek veri kümelerini depolamak üzere Table Storage’ı kullanabilirsiniz. Bir tabloda istediğiniz kadar varlık depolayabilirsiniz ve bir depolama hesabı kapasite limitini dolduracak kadar tablo içerebilir.

Azure Cosmos DB, Azure Tablo depolaması için yazılmış ve şu gibi Premium yetenekler gerektiren uygulamalar için Tablo API'si sağlar:

- Anahtar teslimi genel dağıtım.
- Dünya genelinde adanmış aktarım hızı.
- 99 yüzdebirlikte tek basamaklı milisaniyelik gecikme süresi.
- Garantili yüksek kullanılabilirlik.
- Otomatik ikincil dizin oluşturma.

Azure Tablo depolama için yazılmış uygulamalar herhangi bir kod değişikliği olmadan Tablo API'sini kullanarak Azure Cosmos DB'ye geçirilebilir ve üst düzey özelliklerden yararlanabilir. Tablo API’si, .NET, Java, Python ve Node.js ile kullanılabilecek istemci SDK’larına sahiptir.

Daha fazla bilgi için bkz. [Azure Cosmos DB tablo API'si giriş](/azure/cosmos-db/table-introduction).

## <a name="about-this-tutorial"></a>Bu öğretici hakkında

Bu öğreticide, bir tablo oluşturma ve silme ve tablo verileri ekleme, güncelleştirme, silme ve sorgulama dahil olmak üzere Azure Tablo depolama alanı veya Azure Cosmos DB Tablo API'si kullanarak bazı yaygın görevleri yapmak için F # kodu yazma işlemi gösterilmektedir.

## <a name="prerequisites"></a>Önkoşullar

Bu kılavuzu kullanmak için, önce [bir Azure depolama hesabı](/azure/storage/storage-create-storage-account) veya [Azure Cosmos DB hesabı](https://azure.microsoft.com/try/cosmosdb/)oluşturmanız gerekir.

## <a name="create-an-f-script-and-start-f-interactive"></a>F # betiği oluşturun ve F# Etkileşimli başlatın

Bu makaledeki örnekler bir F # uygulamasında veya F # betiğinde kullanılabilir. F # betiği oluşturmak için, `.fsx` Örneğin `tables.fsx` f # geliştirme ortamınızda uzantılı bir dosya oluşturun.

Daha sonra, [NuGet](https://www.nuget.org/) [Paket](https://fsprojects.github.io/Paket/) paketi [package manager](package-management.md) `WindowsAzure.Storage` ve `WindowsAzure.Storage.dll` bir yönerge kullanarak betiğe paket ve başvuru yüklemek için, paket veya NuGet gibi bir paket Yöneticisi kullanın `#r` . `Microsoft.WindowsAzure.ConfigurationManager`Microsoft. Azure ad alanını almak için bunu yeniden yapın.

### <a name="add-namespace-declarations"></a>Ad alanı bildirimleri ekleme

Aşağıdaki `open` bildirimlerini `tables.fsx` dosyasının üstüne ekleyin:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-azure-storage-connection-string"></a>Azure depolama Bağlantı dizenizi alın

Azure Storage Table Service 'e bağlanıyorsanız, bu öğretici için bağlantı dizeniz olması gerekir. Bağlantı dizenizi Azure portal kopyalayabilirsiniz. Bağlantı dizeleri hakkında daha fazla bilgi için bkz. [depolama bağlantı dizelerini yapılandırma](/azure/storage/storage-configure-connection-string).

### <a name="get-your-azure-cosmos-db-connection-string"></a>Azure Cosmos DB Bağlantı dizenizi alın

Azure Cosmos DB 'e bağlanıyorsanız, bu öğretici için bağlantı dizeniz olması gerekir. Bağlantı dizenizi Azure portal kopyalayabilirsiniz. Azure Portal, Cosmos DB hesabınızda **Ayarlar**  >  **bağlantı dizesi**' ne gidin ve **Kopyala** düğmesine tıklayarak birincil Bağlantı dizenizi kopyalayın.

Öğreticide, aşağıdaki örnekte olduğu gibi betiğe Bağlantı dizenizi girin:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

Ancak, bu gerçek projeler için **önerilmez** . Depolama hesabı anahtarınız depolama hesabınızın kök parolasına benzer. Depolama hesabı anahtarınızı korumak için her zaman özen gösterin. Diğer kullanıcılara dağıtmaktan, sabit kodlamaktan ve başkalarının erişebileceği düz metin dosyasına kaydetmekten kaçının. Güvenliğinin tehlikede olduğunu düşünüyorsanız, Azure portalını kullanarak anahtarınızı yeniden oluşturabilirsiniz.

Gerçek uygulamalar için, depolama Bağlantı dizenizi korumak için en iyi yol bir yapılandırma dosyasıdır. Bağlantı dizesini bir yapılandırma dosyasından getirmek için şunu yapabilirsiniz:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

Azure Yapılandırma Yöneticisi'ni kullanmak isteğe bağlıdır. .NET Framework türü gibi bir API de kullanabilirsiniz `ConfigurationManager` .

### <a name="parse-the-connection-string"></a>Bağlantı dizesini ayrıştırma

Bağlantı dizesini ayrıştırmak için şunu kullanın:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

Bu, bir döndürür `CloudStorageAccount` .

### <a name="create-the-table-service-client"></a>Tablo hizmeti istemcisi oluşturma

`CloudTableClient`Sınıfı tablo depolamadaki tabloları ve varlıkları almanızı sağlar. Hizmet istemcisini oluşturma yöntemlerinden biri aşağıda verilmiştir:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

Artık Table Storage’dan veri okuyan ve bu depolamaya veri yazan kodu yazmaya hazırsınız.

### <a name="create-a-table"></a>Bir tablo oluşturma

Bu örnek, zaten yoksa, nasıl bir tablo oluşturulacağını gösterir:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

### <a name="add-an-entity-to-a-table"></a>Tabloya bir varlık ekleme

Bir varlık, öğesinden devralan bir türe sahip olmalıdır `TableEntity` . `TableEntity`Dilediğiniz şekilde genişletebilirsiniz, ancak bu tür bir parametreye eşit bir oluşturucuya sahip *olmalıdır* . Yalnızca hem hem de içeren `get` Özellikler `set` Azure tablonuzda depolanır.

Bir varlığın bölüm ve satır anahtarı, varlığı tabloda benzersiz şekilde tanımlar. Aynı bölüm anahtarına sahip varlıklar farklı bölüm anahtarlı varlıklara göre daha hızlı sorgulanabilir ancak farklı bölüm anahtarlarının kullanılması paralel işlemler için daha büyük ölçeklendirme sağlar.

Aşağıda, `Customer` `lastName` bölüm anahtarı olarak ve satır anahtarı olarak öğesini kullanan bir örneği verilmiştir `firstName` .

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

Şimdi `Customer` tabloya ekleyin. Bunu yapmak için `TableOperation` tabloda yürütülen bir oluşturun. Bu durumda, bir `Insert` işlem oluşturursunuz.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

### <a name="insert-a-batch-of-entities"></a>Toplu işlem varlık yerleştirme

Tek bir yazma işlemi kullanarak bir tabloya bir varlık toplu işi ekleyebilirsiniz. Batch işlemleri, işlemleri tek bir yürütmeye birleştirmenizi sağlar, ancak bazı kısıtlamalar vardır:

- Aynı toplu işlemde güncelleştirme, silme ve ekleme işlemleri gerçekleştirebilirsiniz.
- Toplu işlem, en fazla 100 varlık içerebilir.
- Bir toplu işlemdeki tüm varlıkların aynı bölüm anahtarı olmalıdır.
- Toplu işlemde bir sorgu gerçekleştirmek mümkün olsa da, toplu işlemdeki tek işlem olmalıdır.

İşte bir toplu işlemin iki ekleme işlemini birleştiren kod:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

### <a name="retrieve-all-entities-in-a-partition"></a>Tüm varlıkları bir bölüme alma

Bir bölümdeki tüm varlıklar için bir tabloyu sorgulamak üzere bir `TableQuery` nesnesi kullanın. Burada, "Smith" bölümünün bölüm anahtarı olduğu varlıklar için filtre uygulayın.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L77-L82)]

Şimdi sonuçları yazdırmıyorsunuz:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]

### <a name="retrieve-a-range-of-entities-in-a-partition"></a>Bir bölüme bir grup varlık alma

Bir bölümdeki tüm varlıkları sorgulamak istemiyorsanız bölüm anahtarı filtresi ile bir satır anahtarı filtresini birleştirerek bir aralık belirleyebilirsiniz. Burada, "Smith" bölümünde bulunan ve satır anahtarı (ad) alfabedeki "M" den önceki bir harfle başlayan tüm varlıkları almak için iki filtre kullanırsınız.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

Şimdi sonuçları yazdırmıyorsunuz:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

### <a name="retrieve-a-single-entity"></a>Tek bir varlık alma

Tek, belirli bir varlığı almak üzere bir sorgu yazabilirsiniz. Burada, `TableOperation` "Ben Smith" müşterisini belirtmek için kullanırsınız. Bir koleksiyon yerine, geri alırsınız `Customer` . Bir sorgudaki bölüm anahtarını ve satır anahtarını belirtme, tablo hizmetinden tek bir varlık almanın en hızlı yoludur.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

Şimdi sonuçları yazdırmıyorsunuz:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]

### <a name="replace-an-entity"></a>Bir varlığı değiştirme

Bir varlığı güncelleştirmek için tablo hizmetinden alın, varlık nesnesini değiştirin ve ardından bir işlem kullanarak değişiklikleri tablo hizmetine geri kaydedin `Replace` . Bu, sunucudaki varlık alındıktan sonra değiştirilmemişse varlığın sunucu üzerinde tamamen değiştirilmesini sağlar, bu durumda işlem başarısız olur. Bu hata, uygulamanızın diğer kaynaklardaki değişikliklerin yanlışlıkla üzerine yazılmasını önlemektir.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

### <a name="insert-or-replace-an-entity"></a>Bir varlığı yerleştirme veya değiştirme

Bazen, tabloda bir varlık olup olmadığını bilemezsiniz. Varsa, içinde depolanan geçerli değerlere artık gerek yoktur. `InsertOrReplace`Varlığı oluşturmak için kullanabilirsiniz veya, durumu ne olursa olsun, varsa bunu değiştirebilirsiniz.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L134-L141)]

### <a name="query-a-subset-of-entity-properties"></a>Giriş özellikleri alt kümesi sorgulama

Tablo sorgusu, her biri yerine bir varlıktan yalnızca birkaç özelliği alabilir. Projeksiyon olarak adlandırılan bu teknik, özellikle büyük varlıklar için sorgu performansını iyileştirebilir. Burada yalnızca ve kullanarak e-posta adresleri döndürürler `DynamicTableEntity` `EntityResolver` . Projeksiyon yerel depolama öykünücüsünde desteklenmez, bu nedenle bu kod yalnızca Tablo hizmetinde bir hesap kullanırken çalıştırılır.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L147-L158)]

### <a name="retrieve-entities-in-pages-asynchronously"></a>Sayfalarda zaman uyumsuz olarak varlıkları alma

Çok sayıda varlığı okuyorsanız ve bunların tümünün dönmesini beklemek yerine alındığı gibi işlemek istiyorsanız, bölümlenmiş bir sorgu kullanabilirsiniz. Burada, büyük bir sonuç kümesinin döndürülmesini beklerken yürütmenin engellenmemesi için zaman uyumsuz iş akışı kullanarak sayfalardaki sonuçları döndürüyorsunuz.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L163-L178)]

Artık bu hesaplamayı zaman uyumlu olarak yürütütemezsiniz:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L180-L180)]

### <a name="delete-an-entity"></a>Bir varlığı silme

Bir varlığı aldıktan sonra silebilirsiniz. Bir varlığı güncelleştirmede olduğu gibi, varlık onu aldıktan sonra değiştiyse bu başarısız olur.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L186-L187)]

### <a name="delete-a-table"></a>Bir tablo silme

Bir depolama hesabındaki bir tabloyu silebilirsiniz. Silinen bir tablo, silme işleminin ardından yeniden oluşturma için belirli bir süre kullanılamayacaktır.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L193-L193)]

## <a name="next-steps"></a>Sonraki adımlar

Artık tablo depolamanın temellerini öğrendiğinize göre, daha karmaşık depolama görevleri ve Azure Cosmos DB Tablo API'si hakkında bilgi edinmek için bu bağlantıları izleyin.

- [Azure Cosmos DB Tablo API'si giriş](/azure/cosmos-db/table-introduction)
- [.NET için depolama Istemci kitaplığı başvurusu](/dotnet/api/overview/azure/storage)
- [Azure depolama türü sağlayıcısı](https://fsprojects.github.io/AzureStorageTypeProvider/)
- [Azure Depolama Ekibi Blogu](/archive/blogs/windowsazurestorage/)
- [Bağlantı Dizeleri Yapılandırma](/azure/storage/common/storage-configure-connection-string)
