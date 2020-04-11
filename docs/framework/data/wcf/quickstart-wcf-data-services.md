---
title: Quickstart (WCF Veri Hizmetleri)
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, quick-start example
- WCF Data Services, Entity Data Model (EDM) service
ms.assetid: 7b18ca1e-d4d6-4c7a-afb9-ce3cebb98a8d
ms.openlocfilehash: f945d33a4fc789b3c73c1c80040fc8527301758b
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121220"
---
# <a name="quickstart-wcf-data-services"></a>Quickstart (WCF Veri Hizmetleri)

Bu hızlı başlangıç, [Başlarken'deki](getting-started-with-wcf-data-services.md)konuları destekleyen bir dizi görev aracılığıyla WCF Veri Hizmetleri ve Açık Veri Protokolü'nü (OData) tanımanıza yardımcı olur.

## <a name="what-youll-learn"></a>Öğrenecekleriniz

Bu hızlı başlatmadaki ilk görev, Northwind örnek veritabanından bir OData akışını ortaya çıkarmak için nasıl bir veri hizmeti oluşturulacağını gösterir. Daha sonraki konularda, bir Web tarayıcısı kullanarak OData akışına erişecek ve istemci kitaplıklarını kullanarak OData akışını tüketen bir Windows Presentation Foundation (WPF) istemci uygulaması oluşturacaksınız.

## <a name="prerequisites"></a>Ön koşullar

Bu hızlı başlatmayı tamamlamak için aşağıdaki bileşenleri yükleyin:

- Visual Studio

- SQL Server örneği. Buna Visual Studio 2015'in varsayılan yüklemesinde veya Visual Studio 2017 veya sonraki yıllarda **veri depolama ve işleme** iş yükünün bir parçası olarak dahil edilen SQL Server Express dahildir.

- Northwind örnek veritabanı. Veritabanını yüklemek [için, Northwind'den](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)Transact-SQL komut dosyasını çalıştırın ve Microsoft SQL Server için pub örnek veritabanlarını çalıştırın.

## <a name="wcf-data-services-quickstart-tasks"></a>WCF veri hizmetleri hızlı başlangıç görevleri

 [Veri Hizmetini Oluşturma](creating-the-data-service.md)

 uygulamaASP.NET tanımlayın, veri modelini tanımlayın, veri hizmeti oluşturun ve kaynaklara erişimi etkinleştirin.

 [Hizmete Bir Web Tarayıcısından Erişin](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

 Hizmeti Visual Studio'dan başlatın ve http GET isteklerini bir Web tarayıcısı aracılığıyla açıkta kalan özet akışına göndererek hizmete erişin.

 [.NET Framework İstemci Uygulamasını Oluştur](creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

 OData akışını tüketmek, verileri Windows denetimlerine bağlamak, bağlı denetimlerde verileri değiştirmek ve değişiklikleri veri hizmetine geri göndermek için bir WPF uygulaması oluşturun.

> [!NOTE]
> Quickstart tamamlanmış bir sürümünden Proje dosyaları [GitHub](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client))indirilebilir.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Hızlı başlatmayı başlatın](creating-the-data-service.md)

## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Entity Framework](../adonet/ef/index.md)
