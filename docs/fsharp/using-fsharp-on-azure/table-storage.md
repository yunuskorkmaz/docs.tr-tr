---
title: 'F # kullanarak Azure tablo depolama ile çalışmaya başlama'
description: Azure tablo depolama veya Azure Cosmos DB kullanarak bulutta yapılandırılmış veri Store.
author: sylvanc
ms.date: 03/26/2018
ms.openlocfilehash: 2d793ba8653833ff384f1824e303b08e05aba69b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43519541"
---
# <a name="get-started-with-azure-table-storage-and-the-azure-cosmos-db-table-api-using-f"></a>Azure tablo depolama ve F # kullanarak Azure Cosmos DB tablo API'si ile çalışmaya başlama # 

Azure tablo depolama bulutta yapılandırılmış NoSQL verileri depolayan bir hizmettir. Tablo depolama, şemasız tasarım ile anahtar/öznitelik deposudur. Table storage şemasız olduğu için ihtiyaçları, uygulama geliştikçe verilerinizi uyarlamak da kolaylaşır. Verilere erişim hızlı ve uygun maliyetli her türden uygulamalar için. Tablo depolama genellikle maliyetini önemli ölçüde benzer veri hacimleri için geleneksel SQL'e daha düşüktür.

Tablo depolama, web uygulamaları, adres defterleri, cihaz bilgileri ve hizmetiniz için gerekli meta verileri başka bir türü için kullanıcı verileri gibi esnek veri kümelerini depolamak için kullanabilirsiniz. Bir tablodaki herhangi bir sayıda varlık depolayabilirsiniz ve bir depolama hesabı herhangi bir sayıda depolama hesabının kapasite sınırına kadar tablo içerebilir.

Azure Cosmos DB, Azure tablo depolaması için yazılmış ve premium özellikler gibi gerektiren uygulamalar için tablo API'sini sağlar:

- Anahtar teslim küresel dağıtım.
- Adanmış aktarım hızı dünya çapında.
- 99. yüzdebirlik dilimde Tek haneli milisaniyelik gecikme süreleri.
- Yüksek kullanılabilirliği garanti ediyoruz.
- Otomatik ikincil dizin oluşturma.

Azure tablo depolaması için yazılmış uygulamalar, kod değişikliği olmadan tablo API'sini kullanarak Azure Cosmos DB'ye geçirilebilir ve premium özelliklerinden yararlanın. Tablo API'si, .NET, Java, Python ve Node.js için İstemci SDK'ları kullanılabilir sahiptir.

Daha fazla bilgi için [Azure Cosmos DB tablo API'sine giriş](https://docs.microsoft.com/azure/cosmos-db/table-introduction).

## <a name="about-this-tutorial"></a>Bu eğitim hakkında

Bu öğreticide, Azure tablo depolama veya Azure Cosmos DB tablo oluşturma ve tablo silme ve ekleme, güncelleştirme, silme ve tablo verilerini sorgulama dahil olmak üzere API'sini kullanarak bazı genel görevleri yapmak için F # kodunun nasıl yazılacağını gösterir.

## <a name="prerequisites"></a>Önkoşullar

Bu kılavuzu kullanmak için önce [bir Azure depolama hesabı oluşturma](/azure/storage/storage-create-storage-account) veya [Azure Cosmos DB hesabı](https://azure.microsoft.com/try/cosmosdb/).


## <a name="create-an-f-script-and-start-f-interactive"></a>Bir F # komut dosyası ve başlangıç F # Etkileşimli oluşturma

Bu makaledeki örnekleri, F # uygulaması veya bir F # komut dosyası kullanılabilir. Bir F # komut dosyası oluşturmak için bir dosya oluşturun. `.fsx` uzantısı, örneğin `tables.fsx`, F # geliştirme ortamınızda.

Ardından, bir [Paket Yöneticisi](package-management.md) gibi [Paket](https://fsprojects.github.io/Paket/) veya [NuGet](https://www.nuget.org/) yüklemek için `WindowsAzure.Storage` paket ve başvuru `WindowsAzure.Storage.dll` bir kullanarakbetiğinizde`#r`yönergesi. Bunu yeniden `Microsoft.WindowsAzure.ConfigurationManager` Microsoft.Azure ad alanını alma için.

### <a name="add-namespace-declarations"></a>Ad alanı bildirimleri ekleme

Aşağıdaki `open` üst tarafına deyimlerini `tables.fsx` dosyası:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-azure-storage-connection-string"></a>Azure depolama bağlantı dizenizi alma

Azure depolama tablo hizmetine bağlanıyorsanız, Bu öğretici için bağlantı dizesi gerekir. Bağlantı dizenizi Azure portalından kopyalayabilirsiniz. Bağlantı dizeleri hakkında daha fazla bilgi için bkz. [depolama bağlantı dizelerini yapılandırma](/azure/storage/storage-configure-connection-string).

### <a name="get-your-azure-cosmos-db-connection-string"></a>Azure Cosmos DB bağlantı dizenizi alma

Azure Cosmos DB'ye bağlanıyorsanız, Bu öğretici için bağlantı dizesi gerekir. Bağlantı dizenizi Azure portalından kopyalayabilirsiniz. Azure portalında, Cosmos DB hesabınıza gidin **ayarları** > **bağlantı dizesi**, tıklatıp **kopyalama** birincil bağlantınızı kopyalamak için düğme Dize. 

Öğretici için aşağıdaki örnekte olduğu gibi komut dosyanızdaki bağlantı dizenizi girin:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

Ancak, bu, **önerilmez** gerçek projeleri. Depolama hesabı anahtarınız depolama hesabınızın kök parolasına benzer. Her zaman depolama hesabı anahtarınızı korumak dikkatli olun. Sabit kodlama veya başkalarının erişebileceği bir düz metin dosyasına kaydederek diğer kullanıcılara dağıtmaktan kaçının. Tehlikeye girmiş olabilecek düşünüyorsanız Azure portalını kullanarak anahtarınızı yeniden oluşturabilirsiniz.

Gerçek uygulamalar, depolama bağlantı dizenizi korumak için en iyi yolu, içinde bir yapılandırma dosyasıdır. Bir yapılandırma dosyasından bağlantı dizesini getirmek için bunu yapabilirsiniz:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

Azure Yapılandırma Yöneticisi'ni kullanmak isteğe bağlıdır. .NET Framework'ün gibi bir API de kullanabilirsiniz `ConfigurationManager` türü.

### <a name="parse-the-connection-string"></a>Bağlantı dizesini ayrıştırma

Bağlantı dizesini ayrıştırmak için kullanın:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

Bu döndürür bir `CloudStorageAccount`.

### <a name="create-the-table-service-client"></a>Tablo hizmeti istemcisi oluşturma

`CloudTableClient` Sınıfı tabloları ve tablo depolama varlıkları almanızı sağlar. Hizmet istemcisini oluşturma yöntemlerinden biri aşağıda verilmiştir:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

Artık, verileri okur ve tablo depolamaya veri yazan kodu yazmaya hazırsınız.

### <a name="create-a-table"></a>Tablo oluşturma

Bu örnek, zaten yoksa, bir tablo oluşturma işlemi gösterilmektedir:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

### <a name="add-an-entity-to-a-table"></a>Tabloya bir varlık ekleme

Öğesinden devralan bir tür bir varlık olan `TableEntity`. Genişletebileceğiniz `TableEntity` istediğiniz gibi ancak türünüz *gerekir* bir parametresiz oluşturucuya sahip. Her ikisi de taşıyan Özellikler `get` ve `set` , Azure tablosunda depolanır.

Bir varlığın bölüm ve sıra anahtarı varlığı tabloda benzersiz şekilde tanımlar. Aynı bölüm anahtarına sahip varlıklar farklı bölüm anahtarlı varlıklara göre daha hızlı sorgulanabilir ancak farklı bölüm anahtarlarının kullanılması paralel işlemler için büyük ölçeklendirme sağlar.

İşte bir örnek bir `Customer` kullanan `lastName` bölüm anahtarı olarak ve `firstName` satır anahtarı olarak.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

Şimdi ekleyin `Customer` tablo. Bunu yapmak için oluşturun bir `TableOperation` tablosunda yürütür. Bu durumda, oluşturduğunuz bir `Insert` işlemi.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

### <a name="insert-a-batch-of-entities"></a>Bir toplu işlem varlık yerleştirme

Varlık, bir tek bir yazma işlemi kullanarak bir tabloya ekleyebilirsiniz. Toplu işlemleri, tek bir yürütme işlemi birleştirmek izin ver, ancak bazı kısıtlamalar sahiptirler:

- Güncelleştirmeler gerçekleştirdiğiniz siler ve aynı toplu işlemde ekler.
- Bir toplu işlem, en fazla 100 varlık içerebilir.
- Bir toplu işlemdeki tüm varlıkların bölüm anahtarları aynı olmalıdır.
- Bir toplu işlemde bir sorgu gerçekleştirmek mümkün olsa da, toplu işlemdeki tek işlem olmalıdır.

İki eklemeleri toplu işlem birleştirir bazı kodlar aşağıda verilmiştir:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

### <a name="retrieve-all-entities-in-a-partition"></a>Bir bölümdeki tüm varlıkları alma

Bir bölümdeki tüm varlıklar için bir tabloyu sorgulamak üzere kullanmak bir `TableQuery` nesne. Burada, "Smith" Bölüm anahtarı olduğu varlıklar için filtreleyin.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L77-L82)]

Artık sonuçlar yazdırma:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]


### <a name="retrieve-a-range-of-entities-in-a-partition"></a>Varlıkları bir bölüme aralığı alınamıyor

Bir bölümdeki tüm varlıkları sorgulamak istemiyorsanız bölüm anahtarı Filtresi ile bir satır anahtarı filtresini birleştirerek bir aralık belirtebilirsiniz. Burada, iki filtre "Smith" bölümünde tüm varlıkları almak için nereye satır anahtarı (ad) alfabede "M"'den önceki bir harfle başlayan kullanırsınız.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

Artık sonuçlar yazdırma:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

### <a name="retrieve-a-single-entity"></a>Tek bir varlık alma

Tek, belirli bir varlığı almak için bir sorgu yazabilirsiniz. Burada kullandığınız bir `TableOperation` "Ben Smith" Müşteri belirtmek için. Bir koleksiyon yerine ulaşırsınız bir `Customer`. Bir sorguda hem Bölüm anahtarı hem de satır anahtarını belirtmek tablo hizmetinden tek bir varlığı almak için en hızlı yoludur.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

Artık sonuçlar yazdırma:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]


### <a name="replace-an-entity"></a>Bir varlığı değiştirme

Bir varlığı güncelleştirmek için tablo hizmetinden alın, varlık nesnesini değiştirin ve değişiklikleri kaydedin geri tablo hizmeti kullanarak bir `Replace` işlemi. Varlığın, bu durumda işlem başarısız alındıktan sonra değiştirilmediği sürece bu sunucu üzerinde tamamen değiştirilmesini varlık neden olur. Değişiklikleri diğer kaynaklardan yanlışlıkla üzerine yazılmasını engellemek üzere bu hatasıdır.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

### <a name="insert-or-replace-an-entity"></a>Ekleme veya değiştirme varlık

Bazı durumlarda, bir varlığı tabloda mevcut olup olmadığını bilmiyorsanız. Ve içinde saklı geçerli değerlerin artık aşması durumunda gereklidir. Kullanabileceğiniz `InsertOrReplace` varlığı oluşturma veya, durumuna bakılmaksızın varsa bunu değiştirin.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L134-L141)]

### <a name="query-a-subset-of-entity-properties"></a>Varlık özelliklerinin bir alt kümesi sorgulama

Tablo sorgusu, bunların tümünü yerine bir varlıktaki birkaç özelliği alabilir. Projeksiyon olarak adlandırılan, bu teknik, özellikle büyük varlıklar için sorgu performansını iyileştirebilir. Burada, yalnızca e-posta adreslerini kullanarak dönüş `DynamicTableEntity` ve `EntityResolver`. Bu nedenle bu kod yalnızca tablo hizmetinde bir hesap kullanırken çalıştırılır projeksiyon yerel depolama öykünücüsünde desteklenmediğini unutmayın.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L147-L158)]

### <a name="retrieve-entities-in-pages-asynchronously"></a>Sayfaları varlıkları zaman uyumsuz olarak alma

Çok sayıda varlık okuyorsanız ve alındıkları gibi bunları yerine tümünü döndürülecek bekleniyor işlemek istiyorsanız, bölümlendirilmiş bir sorgu kullanabilirsiniz. Burada, böylece çok sayıda döndürülecek sonuç için beklerken yürütme engellenip engellenmediğini bir zaman uyumsuz iş akışı kullanarak sayfalarında sonuçları döndürür.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L163-L178)]

Artık bu hesaplamanın eşzamanlı olarak yürütün:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L180-L180)]

### <a name="delete-an-entity"></a>Bir varlığı silme

Bu aldıktan sonra bir varlığı silebilirsiniz. Denge, alınan varlık değişmişse bir varlık olarak güncelleştiriliyor, bu başarısız oluyor.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L186-L187)]

### <a name="delete-a-table"></a>Tablo silme

Bir depolama hesabından bir tablo silebilirsiniz. Silinmiş olan bir tablo silme, bir dönem için yeniden oluşturulması kullanılamaz.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L193-L193)]

## <a name="next-steps"></a>Sonraki adımlar

Table storage'nın temellerini öğrendiğinize göre daha karmaşık depolama görevleri ve Azure Cosmos DB tablo API'si hakkında bilgi edinmek için bu bağlantıları izleyin.

- [Azure Cosmos DB tablo API'sine giriş](https://docs.microsoft.com/azure/cosmos-db/table-introduction)
- [.NET başvurusu için depolama istemcisi kitaplığı](https://docs.microsoft.com/dotnet/api/overview/azure/storage?view=azure-dotnet)
- [Azure depolama tür sağlayıcısı](http://fsprojects.github.io/AzureStorageTypeProvider/)
- [Azure depolama ekibi blogu](https://blogs.msdn.com/b/windowsazurestorage/)
- [Bağlantı dizeleri yapılandırma](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
- [. NET'te Azure tablo depolama kullanmaya başlama](https://azure.microsoft.com/resources/samples/storage-table-dotnet-getting-started/)
