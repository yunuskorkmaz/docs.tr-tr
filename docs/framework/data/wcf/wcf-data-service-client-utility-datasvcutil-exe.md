---
title: WCF Veri Hizmeti İstemci Yardımcı Programı (DataSvcUtil.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, generating client data classes
- WCF Data Services, client library
- WCF Data Services, consuming
ms.assetid: 9d0af606-929b-4c03-b307-3ef5f705afce
ms.openlocfilehash: 97e9502176e0cc2f36d67ee3dc8e8d0739a009b2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790201"
---
# <a name="wcf-data-service-client-utility-datasvcutilexe"></a>WCF Veri Hizmeti İstemci Yardımcı Programı (DataSvcUtil.exe)

DataSvcUtil. exe, bir [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] akışı tüketen ve bir .NET Framework istemci uygulamasından bir veri hizmetine erişmek için gereken istemci veri hizmeti sınıflarını üreten WCF veri Hizmetleri tarafından sunulan bir komut satırı aracıdır. Bu yardımcı program, aşağıdaki meta veri kaynaklarını kullanarak veri sınıfları oluşturabilir:

- Veri hizmetinin kök URI 'SI. Yardımcı programı, veri hizmeti tarafından açığa çıkarılan veri modelini açıklayan hizmet meta verileri belgesini ister. Daha fazla bilgi için bkz [. OData: Hizmet meta verileri](https://go.microsoft.com/fwlink/?LinkId=186070)belgesi.

- Bir veri modeli dosyası (. csdl), [ \[mc-csdl\]içinde tanımlandığı şekilde kavramsal şema tanım dili (csdl) kullanılarak tanımlanır: Kavramsal şema tanım dosyası biçim](https://go.microsoft.com/fwlink/?LinkID=159072) belirtimi.

- Entity Framework ile birlikte sunulan Varlık Veri Modeli araçları kullanılarak oluşturulan bir. edmx dosyası. Daha fazla bilgi için bkz [ \[. mc-edmx\]: Veri Hizmetleri paketleme biçimi](https://go.microsoft.com/fwlink/?LinkID=178833) belirtimi için varlık veri modeli.

Daha fazla bilgi için [nasıl yapılır: Istemci veri hizmeti sınıflarını](how-to-manually-generate-client-data-service-classes-wcf-data-services.md)el ile oluşturun.

DataSvcUtil. exe aracı .NET Framework dizinine yüklenir. Çoğu durumda bu, *C:\Windows\Microsoft.NET\Framework\v4.0*' de bulunur. 64 bit sistemler için bu *C:\Windows\Microsoft.NET\Framework64\v4.0*konumunda bulunur. DataSvcUtil. exe aracına Visual Studio için Geliştirici Komut İstemi de erişebilirsiniz.

## <a name="syntax"></a>Sözdizimi

```
datasvcutil /out:file [/in:file | /uri:serviceuri] [/dataservicecollection] [/language:devlang] [/nologo] [/version:ver] [/help]
```

## <a name="parameters"></a>Parametreler

|Seçenek|Açıklama|
|------------|-----------------|
|`/dataservicecollection`|Nesneleri denetimlere bağlamak için gereken kodun de oluşturulduğunu belirtir.|
|`/help`<br /><br /> -veya-<br /><br /> `/?`|Araç için komut sözdizimini ve seçenekleri görüntüler.|
|`/in:` *Dosya\<>*|. Csdl veya. edmx dosyasını ya da dosyanın bulunduğu bir dizini belirtir.|
|`/language:`[VB&#124;CSharp]|Oluşturulan kaynak kodu dosyalarının dilini belirtir. Dil varsayılan olarak C#olur.|
|`/nologo`|Telif hakkı iletisinin görüntülenmesini önler.|
|`/out:` *Dosya\<>*|Oluşturulan istemci veri hizmeti sınıflarını içeren kaynak kodu dosyasının adını belirtir.|
|`/uri:` *dize\<>*|OData akışı URI 'SI.|
|`/version:`[1.0&#124;2.0]|En yüksek kabul edilen OData sürümünü belirtir. Sürüm, döndürülen veri hizmeti meta verilerindeki `DataServiceVersion` DataService öğesinin özniteliğine göre belirlenir. Daha fazla bilgi için bkz. [veri hizmeti sürümü oluşturma](data-service-versioning-wcf-data-services.md). `/dataservicecollection` Parametresini belirttiğinizde veri bağlamayı etkinleştirmek için de belirtmeniz `/version:2.0` gerekir.|

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Hizmeti İstemci Kitaplığı Oluşturma](generating-the-data-service-client-library-wcf-data-services.md)
- [Nasıl yapılır: Veri hizmeti başvurusu ekleme](how-to-add-a-data-service-reference-wcf-data-services.md)
