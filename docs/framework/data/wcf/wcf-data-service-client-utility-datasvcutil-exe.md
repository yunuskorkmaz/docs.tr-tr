---
title: WCF Veri Hizmeti İstemci Yardımcı Programı (DataSvcUtil.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, generating client data classes
- WCF Data Services, client library
- WCF Data Services, consuming
ms.assetid: 9d0af606-929b-4c03-b307-3ef5f705afce
ms.openlocfilehash: de260e1a6b58fdbac1a2f0f40c7ec2e50b13644e
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975079"
---
# <a name="wcf-data-service-client-utility-datasvcutilexe"></a>WCF Veri Hizmeti İstemci Yardımcı Programı (DataSvcUtil.exe)

DataSvcUtil. exe, bir açık veri Protokolü (OData) akışı tüketen ve bir .NET Framework istemci uygulamasından bir veri hizmetine erişmek için gereken istemci veri hizmeti sınıflarını oluşturan WCF Veri Hizmetleri tarafından sunulan bir komut satırı aracıdır. Bu yardımcı program, aşağıdaki meta veri kaynaklarını kullanarak veri sınıfları oluşturabilir:

- Veri hizmetinin kök URI 'SI. Yardımcı programı, veri hizmeti tarafından açığa çıkarılan veri modelini açıklayan hizmet meta verileri belgesini ister. Daha fazla bilgi için bkz. [OData: hizmet meta verileri belgesi](https://go.microsoft.com/fwlink/?LinkId=186070).

- [\[mc-csdl\]: kavramsal şema tanımı dosya biçimi](https://go.microsoft.com/fwlink/?LinkID=159072) belirtiminde tanımlanan kavramsal şema tanım DILI (csdl) kullanılarak tanımlanan bir veri modeli dosyası (. csdl).

- Entity Framework ile birlikte sunulan Varlık Veri Modeli araçları kullanılarak oluşturulan bir. edmx dosyası. Daha fazla bilgi için bkz. [\[mc-EDMX\]: varlık veri modeli veri Hizmetleri paketleme biçimi](https://go.microsoft.com/fwlink/?LinkID=178833) belirtimi.

Daha fazla bilgi için bkz. [nasıl yapılır: El Ile Istemci veri hizmeti sınıfları oluşturma](how-to-manually-generate-client-data-service-classes-wcf-data-services.md).

DataSvcUtil. exe aracı .NET Framework dizinine yüklenir. Çoğu durumda bu, *C:\Windows\Microsoft.NET\Framework\v4.0*' de bulunur. 64 bit sistemler için bu *C:\Windows\Microsoft.NET\Framework64\v4.0*konumunda bulunur. DataSvcUtil. exe aracına Visual Studio için Geliştirici Komut İstemi de erişebilirsiniz.

## <a name="syntax"></a>Sözdizimi

```console
datasvcutil /out:file [/in:file | /uri:serviceuri] [/dataservicecollection] [/language:devlang] [/nologo] [/version:ver] [/help]
```

## <a name="parameters"></a>Parametreler

|Seçenek|Açıklama|
|------------|-----------------|
|`/dataservicecollection`|Nesneleri denetimlere bağlamak için gereken kodun de oluşturulduğunu belirtir.|
|`/help`<br /><br /> veya<br /><br /> `/?`|Araç için komut sözdizimini ve seçenekleri görüntüler.|
|`/in:` *\<dosya >*|. Csdl veya. edmx dosyasını ya da dosyanın bulunduğu bir dizini belirtir.|
|`/language:`[VB&#124;CSharp]|Oluşturulan kaynak kodu dosyalarının dilini belirtir. Dil varsayılan olarak C#olur.|
|`/nologo`|Telif hakkı iletisinin görüntülenmesini önler.|
|`/out:` *\<dosya >*|Oluşturulan istemci veri hizmeti sınıflarını içeren kaynak kodu dosyasının adını belirtir.|
|`/uri:` *\<dize >*|OData akışı URI 'SI.|
|`/version:`[1,0&#124;2,0]|En yüksek kabul edilen OData sürümünü belirtir. Sürüm, döndürülen veri hizmeti meta verilerindeki DataService öğesinin `DataServiceVersion` özniteliğine göre belirlenir. Daha fazla bilgi için bkz. [veri hizmeti sürümü oluşturma](data-service-versioning-wcf-data-services.md). `/dataservicecollection` parametresini belirttiğinizde veri bağlamayı etkinleştirmek için `/version:2.0` de belirtmeniz gerekir.|

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Hizmeti İstemci Kitaplığı Oluşturma](generating-the-data-service-client-library-wcf-data-services.md)
- [Nasıl yapılır: Veri Hizmeti Başvurusu Ekleme](how-to-add-a-data-service-reference-wcf-data-services.md)
