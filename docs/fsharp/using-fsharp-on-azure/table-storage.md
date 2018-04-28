---
title: "F # kullanarak Azure Table storage'ı kullanmaya başlama"
description: Azure Table storage veya Azure Cosmos DB kullanarak bulutta yapılandırılmış veri depolayın.
author: sylvanc
ms.author: phcart
ms.date: 03/26/2018
ms.topic: conceptual
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 50721ca44bbae5c52984b08a30bc87507fbf063d
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="get-started-with-azure-table-storage-and-the-azure-cosmos-db-table-api-using-f"></a>Azure tablo depolaması ve F # kullanarak Azure Cosmos DB tablo API'sini kullanmaya başlama # 

Azure Table storage bulutta yapılandırılmış NoSQL verileri depolayan bir hizmettir. Table storage, şemasız tasarım ile bir anahtar/öznitelik deposudur. Table storage şemasız olduğu için uygulamanızın ihtiyaçları geliştikçe verilerinizi uyarlamak kolaydır. Verilere erişim hızlı ve uygun maliyetli türlü uygulama için. Tablo depolama genellikle maliyetini önemli ölçüde benzer hacimdeki veriler için geleneksel SQL'e daha düşüktür.

Table storage, web uygulamaları, adres defterleri, cihaz bilgilerini ve başka türde bir hizmetiniz için gerekli meta veriler için kullanıcı verileri gibi esnek veri kümelerini depolamak için kullanabilirsiniz. Bir tablodaki herhangi bir sayıda varlık depolayabilirsiniz ve bir depolama hesabı herhangi bir sayı depolama hesabının kapasite sınırını kadar tablo içerebilir.

Azure Cosmos DB Azure tablo depolaması için yazılmıştır ve premium özellikleri gibi gerektiren uygulamalar için tablo API sağlar:

- Anahtar teslimi genel dağıtım.
- Dünya çapında ayrılmış işleme.
- Tek basamaklı milisaniyelik gecikme 99 adresindeki.
- Yüksek oranda kullanılabilirlik garanti.
- Otomatik ikincil dizin.

Azure tablo depolaması için yazılmış uygulamalar için hiçbir kod değişikliklerle tablo API kullanarak Azure Cosmos DB geçirmek ve premium özelliklerinden. Tablo API, .NET, Java, Python ve Node.js için İstemci SDK kullanılabilir sahiptir.

Daha fazla bilgi için bkz: [Azure Cosmos DB tablo API giriş](https://docs.microsoft.com/azure/cosmos-db/table-introduction).

## <a name="about-this-tutorial"></a>Bu öğretici hakkında

Bu öğretici, Azure Table storage veya Azure Cosmos DB tablo oluşturma ve bir tablo silme ve ekleme, güncelleştirme, silme ve tablo verileri Sorgulama dahil olmak üzere API'sini kullanarak bazı genel görevleri gerçekleştirmek için F # kodunun nasıl yazılacağını gösterir.

## <a name="prerequisites"></a>Önkoşullar

Bu kılavuzu kullanmak için öncelikle [bir Azure depolama hesabı oluşturma](/azure/storage/storage-create-storage-account) veya [Azure Cosmos DB hesap](https://azure.microsoft.com/try/cosmosdb/).


## <a name="create-an-f-script-and-start-f-interactive"></a>Bir F # betiği ve başlangıç F # Etkileşimli oluşturma

Bu makaledeki örnekler, F # uygulaması veya F # betiği kullanılabilir. F # betiği oluşturmak için dosya oluştur `.fsx` uzantısı, örneğin `tables.fsx`, ortamınızdaki F # geliştirme.

Ardından, kullanın bir [Paket Yöneticisi](package-management.md) gibi [Paket](https://fsprojects.github.io/Paket/) veya [NuGet](https://www.nuget.org/) yüklemek için `WindowsAzure.Storage` paket ve başvuru `WindowsAzure.Storage.dll` bir kullanarakkomut`#r`yönergesi. Bunu yeniden `Microsoft.WindowsAzure.ConfigurationManager` Microsoft.Azure ad alanı alabilmek için.

### <a name="add-namespace-declarations"></a>Ad alanı bildirimleri ekleme

Aşağıdakileri ekleyin `open` deyimleri üstüne `tables.fsx` dosyası:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-azure-storage-connection-string"></a>Azure depolama bağlantı dizenizi Al

Azure depolama tablo hizmetine bağlanıyorsanız, bağlantı dizenizi Bu öğretici için gerekir. Bağlantı dizenizi Azure portalından kopyalayabilirsiniz. Bağlantı dizeleri hakkında daha fazla bilgi için bkz: [Storage bağlantı dizelerini yapılandırma](/azure/storage/storage-configure-connection-string).

### <a name="get-your-azure-cosmos-db-connection-string"></a>Azure Cosmos veritabanı bağlantı dizenizi Al

Azure Cosmos Veritabanına bağlanıyorsanız, bağlantı dizenizi Bu öğretici için gerekir. Bağlantı dizenizi Azure portalından kopyalayabilirsiniz. Azure portalında Cosmos DB hesabınıza gidin **ayarları** > **bağlantı dizesi**, tıklatıp **kopyalama** birincil bağlantınızı kopyalamak için düğmesi Dize. 

Öğretici için aşağıdaki örneğe benzer betiğinizin bağlantı dizenizi girin:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

Ancak, bu olduğu **önerilmez** için gerçek projeleri. Depolama hesabı anahtarınız depolama hesabınızın kök parolasına benzer. Her zaman depolama hesabı anahtarınızı korumak dikkatli olun. Sabit kodlama veya başkalarının erişebileceği düz metin dosyasına kaydetme diğer kullanıcılara dağıtmaktan kaçının. Bunu tehlikede olduğunu düşünüyorsanız, Azure Portalı'nı kullanarak anahtarınızı yeniden oluşturabilirsiniz.

İçin gerçek uygulamalar, depolama bağlantı dizenizi korumak için en iyi yapılandırma dosyasında yoludur. Yapılandırma dosyasından bağlantı dizesini almak için bunu yapabilirsiniz:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

Azure Yapılandırma Yöneticisi'ni kullanarak isteğe bağlıdır. .NET Framework'ün gibi bir API de kullanabilirsiniz `ConfigurationManager` türü.

### <a name="parse-the-connection-string"></a>Bağlantı dizesini ayrıştırma

Bağlantı dizesini ayrıştırmak için kullanın:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

Bu döndürür bir `CloudStorageAccount`.

### <a name="create-the-table-service-client"></a>Tablo hizmeti istemcisi oluşturma

`CloudTableClient` Sınıfı tabloları ve varlıkları tablo depolama almanıza olanak sağlar. Hizmet istemcisini oluşturma yöntemlerinden biri aşağıda verilmiştir:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

Şimdi veri okuyan ve tablo depolamaya veri yazan kodu yazmaya hazırsınız.

### <a name="create-a-table"></a>Bir tablo oluştur

Bu örnek, zaten yoksa, bir tablo oluşturulacağını gösterir:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

### <a name="add-an-entity-to-a-table"></a>Tabloya bir varlık ekleme

Öğesinden devralan bir türe sahip bir varlık sahip `TableEntity`. Genişletebilirsiniz `TableEntity` istediğiniz gibi ancak türünüz *gerekir* bir parametresiz oluşturucuya sahip. Yalnızca hem de özellikleri `get` ve `set` Azure tablosunda depolanır.

Bir varlığın bölüm ve sıra anahtarı varlığı tabloda benzersiz şekilde tanımlar. Aynı bölüm anahtarına sahip varlıklar farklı bölüm anahtarlarının göre daha hızlı sorgulanabilir ancak farklı bölüm anahtarlarının kullanılması paralel işlemler daha fazla ölçeklenebilirlik sağlar.

Bir örneği burada verilmiştir bir `Customer` kullanan `lastName` bölüm anahtarı olarak ve `firstName` satır anahtarı olarak.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

Şimdi ekleyin `Customer` tablosu. Bunu yapmak için oluşturun bir `TableOperation` tabloda yürütür. Bu durumda, oluşturduğunuz bir `Insert` işlemi.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

### <a name="insert-a-batch-of-entities"></a>Bir toplu işlem varlık yerleştirme

Toplu işlem varlık bir tek bir yazma işlemini kullanarak bir tabloya ekleyebilirsiniz. Toplu işlemleri, tek bir yürütme işlemlere birleştirmenize izin verir, ancak bazı sınırlamalar vardır:

- Güncelleştirmeleri gerçekleştirme siler ve aynı toplu işlemde ekler.
- Toplu işlem en fazla 100 varlık içerebilir.
- Bir toplu işlemde tüm varlıkların aynı bölüm anahtarına sahip olması gerekir.
- Bir toplu işlemde bir sorgu gerçekleştirmek mümkün olsa da, toplu işlemdeki tek işlem olmalıdır.

Toplu işlem iki eklemeleri birleştirir biraz kod şöyledir:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

### <a name="retrieve-all-entities-in-a-partition"></a>Tüm varlıkları bir bölüme alma

Bir bölümdeki tüm varlıklar için bir tabloyu sorgulamak için kullanın bir `TableQuery` nesnesi. Burada, "Smith" Bölüm anahtarı olduğu varlıklar için filtreleyin.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L77-L82)]

Artık sonuçlar yazdırma:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]


### <a name="retrieve-a-range-of-entities-in-a-partition"></a>Bir dizi varlıkları bir bölüme alma

Bir bölümdeki tüm varlıkları sorgulamak istemiyorsanız bölüm anahtarı Filtresi ile bir satır anahtarı filtresini birleştirerek bir aralık belirtebilirsiniz. Burada, iki filtre "Smith" bölümünde tüm varlıkları almak için burada satır anahtarı (ad) alfabede "M"'den önceki bir harfle başlayan kullanın.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

Artık sonuçlar yazdırma:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

### <a name="retrieve-a-single-entity"></a>Tek bir varlık alma

Tek, belirli bir varlığı almak üzere bir sorgu yazabilirsiniz. Burada, kullandığınız bir `TableOperation` "Ben Smith" Müşteri belirtmek için. Bir koleksiyon yerine ulaşırsınız bir `Customer`. Bir sorguda hem Bölüm anahtarı hem de satır anahtarını belirtmek tablo hizmetinden tek bir varlık almak için en hızlı yoludur.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

Artık sonuçlar yazdırma:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]


### <a name="replace-an-entity"></a>Bir varlığı değiştirme

Bir varlığı güncelleştirmek için tablo hizmetinden alın, varlık nesnesini değiştirin ve sonra geri tablo hizmeti kullanmaya değişiklikleri kaydetmek bir `Replace` işlemi. Bu, bu durumda işlem başarısız alındığından beri sunucunun varlıkta değiştirilmediği sürece bu sunucu üzerinde tamamen değiştirilmesini varlık neden olur. Bu hata uygulamanızı değişiklikler diğer kaynaklardan yanlışlıkla üzerine yazılmasını önlemektir.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

### <a name="insert-or-replace-an-entity"></a>Ekleme veya değiştirme bir varlık

Bazı durumlarda, bir varlık tablosunda var olup olmadığını bilemeyebilirsiniz. Ve içinde saklı geçerli değerlerin bulursa, artık gerekli değildir. Kullanabileceğiniz `InsertOrReplace` varlığı oluşturun veya, durumuna bakılmaksızın varsa değiştirin.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L134-L141)]

### <a name="query-a-subset-of-entity-properties"></a>Varlık özelliklerinin bir alt sorgu

Tablo sorgusu, bunların tümü yerine bir varlıktaki birkaç özelliği alabilir. Projeksiyon, olarak adlandırılan bu teknik özellikle büyük varlıklar için sorgu performansını iyileştirebilir. Burada, yalnızca e-posta adresleri kullanarak dönmek `DynamicTableEntity` ve `EntityResolver`. Bu kod yalnızca tablo hizmetinde bir hesap kullanırken çalıştırılır şekilde projeksiyon yerel depolama öykünücüsünde desteklenmez unutmayın.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L147-L158)]

### <a name="retrieve-entities-in-pages-asynchronously"></a>Varlıkları sayfalarda zaman uyumsuz olarak Al

Çok sayıda varlık okuyorsanız ve bunları alındıktan gibi yerine tümünü döndürmek beklenirken işlem yapmak istediğiniz, bölümlendirilmiş bir sorgu kullanabilirsiniz. Burada, büyük bir döndürmek için sonuç kümesi için beklerken çalıştırmanın engellenmemesi bir zaman uyumsuz iş akışı kullanarak sayfalarında sonuçları döndürür.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L163-L178)]

Artık bu hesaplama zaman uyumlu olarak yürütün:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L180-L180)]

### <a name="delete-an-entity"></a>Bir varlığı silme

Bunu aldıktan sonra bir varlık silebilirsiniz. Siz aldıktan sonra varlık değiştirilmiş güncelleştirmeyle bir varlık gibi bu başarısız olur.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L186-L187)]

### <a name="delete-a-table"></a>Tablo silme

Bir depolama hesabından bir tablo silebilirsiniz. Silinmiş bir tablo silme işlemi şu süre boyunca yeniden oluşturma kullanılamaz.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L193-L193)]

## <a name="next-steps"></a>Sonraki adımlar

Table Storage öğrendiğinize göre daha karmaşık depolama görevleri ve Azure Cosmos DB tablo API hakkında bilgi edinmek için aşağıdaki bağlantıları izleyin.

- [Azure Cosmos DB tablo API giriş](https://docs.microsoft.com/azure/cosmos-db/table-introduction)
- [.NET başvurusu için depolama istemci kitaplığı](https://docs.microsoft.com/dotnet/api/overview/azure/storage?view=azure-dotnet)
- [Azure depolama türü sağlayıcısı](http://fsprojects.github.io/AzureStorageTypeProvider/)
- [Azure depolama ekibi blogu](http://blogs.msdn.com/b/windowsazurestorage/)
- [Bağlantı dizeleri yapılandırma](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
- [.NET içinde Azure tablo depolaması ile çalışmaya başlama](https://azure.microsoft.com/resources/samples/storage-table-dotnet-getting-started/)
