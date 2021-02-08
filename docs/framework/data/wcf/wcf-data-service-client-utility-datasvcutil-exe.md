---
description: 'Daha fazla bilgi edinin: WCF veri hizmeti Istemci yardımcı programı (DataSvcUtil.exe)'
title: WCF Veri Hizmeti İstemci Yardımcı Programı (DataSvcUtil.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, generating client data classes
- WCF Data Services, client library
- WCF Data Services, consuming
ms.assetid: 9d0af606-929b-4c03-b307-3ef5f705afce
ms.openlocfilehash: 1e232538284072d82eed3f1b9e8d41f2ae950adf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791705"
---
# <a name="wcf-data-service-client-utility-datasvcutilexe"></a>WCF Veri Hizmeti İstemci Yardımcı Programı (DataSvcUtil.exe)

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

DataSvcUtil.exe, bir açık veri Protokolü (OData) akışı tüketen ve bir .NET Framework istemci uygulamasından bir veri hizmetine erişmek için gereken istemci veri hizmeti sınıflarını oluşturan WCF Veri Hizmetleri tarafından sunulan bir komut satırı aracıdır. Bu yardımcı program, aşağıdaki meta veri kaynaklarını kullanarak veri sınıfları oluşturabilir:

- Veri hizmetinin kök URI 'SI. Yardımcı programı, veri hizmeti tarafından açığa çıkarılan veri modelini açıklayan hizmet meta verileri belgesini ister. Daha fazla bilgi için bkz. [AtomPub (RFC5023)](https://tools.ietf.org/html/rfc5023#section-8).

- , [ \[ Mc-csdl \] : kavramsal şema tanımı dosya biçimi](/openspecs/windows_protocols/mc-csdl/c03ad8c3-e8b7-4306-af96-a9e52bb3df12) belirtiminde tanımlandığı şekilde kavramsal şema tanım dili (csdl) kullanılarak tanımlanan bir veri modeli dosyası (. csdl).

- Entity Framework ile birlikte sunulan Varlık Veri Modeli araçları kullanılarak oluşturulan bir. edmx dosyası. Daha fazla bilgi için bkz. [ \[ mc-EDMX \] : varlık veri modeli for Data Services paketleme biçim](/openspecs/windows_protocols/mc-edmx/5dff5e25-56a1-408b-9d44-bff6634c7d16) belirtimi.

Daha fazla bilgi için bkz. [nasıl yapılır: El Ile Istemci veri hizmeti sınıfları oluşturma](how-to-manually-generate-client-data-service-classes-wcf-data-services.md).

DataSvcUtil.exe aracı .NET Framework dizinine yüklenir. Çoğu durumda bu, *C:\Windows\Microsoft.NET\Framework\v4.0*' de bulunur. 64 bit sistemler için bu *C:\Windows\Microsoft.NET\Framework64\v4.0* konumunda bulunur. Visual Studio için Geliştirici Komut İstemi DataSvcUtil.exe aracına da erişebilirsiniz.

## <a name="syntax"></a>Sözdizimi

```console
datasvcutil /out:file [/in:file | /uri:serviceuri] [/dataservicecollection] [/language:devlang] [/nologo] [/version:ver] [/help]
```

## <a name="parameters"></a>Parametreler

|Seçenek|Açıklama|
|------------|-----------------|
|`/dataservicecollection`|Nesneleri denetimlere bağlamak için gereken kodun de oluşturulduğunu belirtir.|
|`/help`<br /><br /> -veya-<br /><br /> `/?`|Araç için komut sözdizimini ve seçenekleri görüntüler.|
|`/in:` *\<file>*|. Csdl veya. edmx dosyasını ya da dosyanın bulunduğu bir dizini belirtir.|
|`/language:`[VB&#124;CSharp]|Oluşturulan kaynak kodu dosyalarının dilini belirtir. Dil varsayılan olarak C# ' dir.|
|`/nologo`|Telif hakkı iletisinin görüntülenmesini önler.|
|`/out:` *\<file>*|Oluşturulan istemci veri hizmeti sınıflarını içeren kaynak kodu dosyasının adını belirtir.|
|`/uri:` *\<string>*|OData akışı URI 'SI.|
|`/version:`[1,0&#124;2,0]|En yüksek kabul edilen OData sürümünü belirtir. Sürüm, `DataServiceVersion` döndürülen veri hizmeti meta verilerindeki DataService öğesinin özniteliğine göre belirlenir. Daha fazla bilgi için bkz. [veri hizmeti sürümü oluşturma](data-service-versioning-wcf-data-services.md). `/dataservicecollection`Parametresini belirttiğinizde `/version:2.0` veri bağlamayı etkinleştirmek için de belirtmeniz gerekir.|

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Hizmeti İstemci Kitaplığı Oluşturma](generating-the-data-service-client-library-wcf-data-services.md)
- [Nasıl yapılır: Veri Hizmeti Başvurusu Ekleme](how-to-add-a-data-service-reference-wcf-data-services.md)
