---
title: 'Nasıl yapılır: İstemci veri hizmeti sınıfları (WCF Veri Hizmetleri) el ile oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, client library
ms.assetid: b98cb1d6-956a-4e50-add6-67e4f2587346
ms.openlocfilehash: d197088f94614aac007c0adc310500ae4609f757
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56091662"
---
# <a name="how-to-manually-generate-client-data-service-classes-wcf-data-services"></a>Nasıl yapılır: İstemci veri hizmeti sınıfları (WCF Veri Hizmetleri) el ile oluşturma
WCF veri hizmetleri sağlamak kullandığınızda istemci veri hizmeti sınıfları otomatik olarak oluşturmak Visual Studio ile tümleştirilir **hizmet Başvurusu Ekle** bir Visual Studio projenize bir veri hizmetine başvuru eklemek için iletişim kutusu. Daha fazla bilgi için [nasıl yapılır: Bir veri hizmeti başvurusu ekleme](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md). Kod oluşturma aracı kullanılarak el ile de aynı istemci veri hizmeti sınıfları oluşturabilirsiniz `DataSvcUtil.exe`. WCF Veri Hizmetleri ile birlikte, bu aracı, veri hizmeti tanımından .NET Framework sınıfları oluşturur. Veri Hizmeti sınıfları kavramsal model (.csdl) dosyası ve bir Visual Studio projesinde bir Entity Framework modelini temsil eden .edmx dosyası üretmek için de kullanılabilir.

 Bu konudaki örnek Northwind örnek veri hizmetini temel alan istemci veri hizmeti sınıfları oluşturur. Bu hizmet, tamamladığınızda oluşturulur [WCF Veri Hizmetleri Hızlı Başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md). Bu konudaki örnekler için Northwind modeli kavramsal model dosyası gerektirir. Daha fazla bilgi için [nasıl yapılır: Model ve eşleme dosyalarını üretmek için Edmgen.exe'yi kullanın](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md). Bu konudaki örnekler için Northwind modeli .edmx dosyası gerektirir. Daha fazla bilgi için [.edmx dosyasını genel bakış](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)).

### <a name="to-generate-c-classes-that-support-data-binding"></a>Veri bağlamayı destekleyen C# sınıfları oluşturmak için

-   Komut isteminde satır sonları olmadan aşağıdaki komutu yürütün:

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:CSharp /out:Northwind.cs /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    >  İçin sağlanan değer değiştirmelisiniz `/uri:` Northwind örnek veri hizmeti örneğinizi URI parametresiyle.

### <a name="to-generate-visual-basic-classes-that-support-data-binding"></a>Veri bağlamayı destekleyen Visual Basic sınıfları oluşturmak için

-   Komut isteminde satır sonları olmadan aşağıdaki komutu yürütün:

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    >  Sağlanan değer değiştirmelisiniz `/uri:` Northwind örnek veri hizmeti örneğinizi URI parametresiyle.

### <a name="to-generate-c-classes-based-on-the-service-uri"></a>Hizmet URI'si temel C# sınıfları oluşturmak için

-   Komut isteminde satır sonları olmadan aşağıdaki komutu yürütün:

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /language:CSharp /out:northwind.cs /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    >  İçin sağlanan değer değiştirmelisiniz `/uri:` Northwind örnek veri hizmeti örneğinizi URI parametresiyle.

### <a name="to-generate-visual-basic-classes-based-on-the-service-uri"></a>Visual Basic sınıf tabanlı hizmet URI'si oluşturmak için

-   Komut isteminde satır sonları olmadan aşağıdaki komutu yürütün:

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    >  Sağlanan değer değiştirmelisiniz `/uri:` Northwind örnek veri hizmeti örneğinizi URI parametresiyle.

### <a name="to-generate-c-classes-based-on-the-conceptual-model-file-csdl"></a>Kavramsal model dosyasını (CSDL) temel alan C# sınıfları oluşturmak için

-   Komut isteminde satır sonları olmadan aşağıdaki komutu yürütün:

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.csdl /out:Northwind.cs
    ```

### <a name="to-generate-visual-basic-classes-based-on-the-conceptual-model-file-csdl"></a>Kavramsal model dosyasını (CSDL) temel alan Visual Basic sınıflar oluşturmak için

-   Komut isteminde satır sonları olmadan aşağıdaki komutu yürütün:

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.csdl /out:Northwind.vb
    ```

### <a name="to-generate-c-classes-based-on-the-edmx-file"></a>.Edmx dosyasını temel alan C# sınıfları oluşturmak için

-   Komut isteminde satır sonları olmadan aşağıdaki komutu yürütün:

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.edmx /out:c:\northwind.cs
    ```

### <a name="to-generate-visual-basic-classes-based-on-the-edmx-file"></a>.Edmx dosyasını temel alan Visual Basic sınıflar oluşturmak için

-   Komut isteminde satır sonları olmadan aşağıdaki komutu yürütün:

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.edmx /out:c:\northwind.vb
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Hizmeti İstemci Kitaplığı Oluşturma](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)
- [Nasıl yapılır: Bir veri hizmeti başvurusu ekleme](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)
- [WCF Veri Hizmeti İstemci Yardımcı Programı (DataSvcUtil.exe)](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md)