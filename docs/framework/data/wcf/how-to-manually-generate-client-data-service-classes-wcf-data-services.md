---
title: 'Nasıl yapılır: Istemci veri hizmeti sınıflarını el ile oluştur (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, client library
ms.assetid: b98cb1d6-956a-4e50-add6-67e4f2587346
ms.openlocfilehash: 2a827e4909b18d9cca74fc20a2d83d2730ea0cd9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952291"
---
# <a name="how-to-manually-generate-client-data-service-classes-wcf-data-services"></a>Nasıl yapılır: Istemci veri hizmeti sınıflarını el ile oluştur (WCF Veri Hizmetleri)
WCF Veri Hizmetleri, Visual Studio projesindeki bir veri hizmetine bir başvuru eklemek için **hizmet başvurusu Ekle** iletişim kutusunu kullandığınızda istemci veri hizmeti sınıflarını otomatik olarak oluşturmanıza olanak tanımak üzere Visual Studio ile tümleşir. Daha fazla bilgi için [nasıl yapılır: Veri hizmeti başvurusu](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)ekleyin. Ayrıca, `DataSvcUtil.exe`kod oluşturma aracını kullanarak aynı istemci veri hizmeti sınıflarını el ile oluşturabilirsiniz. WCF Veri Hizmetleri ile birlikte bulunan bu araç, veri hizmeti tanımından .NET Framework sınıfları oluşturur. Ayrıca, kavramsal model (. csdl) dosyasından ve Visual Studio projesindeki bir Entity Framework modeli temsil eden. edmx dosyasından veri hizmeti sınıfları oluşturmak için de kullanılabilir.

 Bu konudaki örnek, Northwind örnek veri hizmeti temel alınarak istemci veri hizmeti sınıfları oluşturur. Bu hizmet, [WCF veri hizmetleri hızlı](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur. Bu konudaki bazı örneklerde, Northwind modeli için kavramsal model dosyası gereklidir. Daha fazla bilgi için [nasıl yapılır: Modeli ve eşleme dosyalarını](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)oluşturmak Için EdmGen. exe ' yi kullanın. Bu konudaki bazı örnekler, Northwind modeli için. edmx dosyasını gerektirir. Daha fazla bilgi için bkz [. edmx dosyasına genel bakış](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)).

### <a name="to-generate-c-classes-that-support-data-binding"></a>Veri bağlamayı C# destekleyen sınıflar oluşturmak için

- Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:CSharp /out:Northwind.cs /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    > Verilen değeri, Northwind örnek veri hizmeti örneğinizin `/uri:` URI 'siyle parametreye değiştirmelisiniz.

### <a name="to-generate-visual-basic-classes-that-support-data-binding"></a>Veri bağlamayı destekleyen Visual Basic sınıfları oluşturmak için

- Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    > Sağlanan değeri, Northwind örnek veri hizmeti `/uri:` örneğinizin URI 'siyle parametreye değiştirmelisiniz.

### <a name="to-generate-c-classes-based-on-the-service-uri"></a>Hizmet URI C# 'sini temel alan sınıflar oluşturmak için

- Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /language:CSharp /out:northwind.cs /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    > Verilen değeri, Northwind örnek veri hizmeti örneğinizin `/uri:` URI 'siyle parametreye değiştirmelisiniz.

### <a name="to-generate-visual-basic-classes-based-on-the-service-uri"></a>Hizmet URI 'sini temel alan Visual Basic sınıfları oluşturmak için

- Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    > Sağlanan değeri, Northwind örnek veri hizmeti `/uri:` örneğinizin URI 'siyle parametreye değiştirmelisiniz.

### <a name="to-generate-c-classes-based-on-the-conceptual-model-file-csdl"></a>Kavramsal model C# DOSYASıNA (csdl) göre sınıflar oluşturmak için

- Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.csdl /out:Northwind.cs
    ```

### <a name="to-generate-visual-basic-classes-based-on-the-conceptual-model-file-csdl"></a>Kavramsal model dosyasına (CSDL) göre Visual Basic sınıfları oluşturmak için

- Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.csdl /out:Northwind.vb
    ```

### <a name="to-generate-c-classes-based-on-the-edmx-file"></a>. Edmx C# dosyasını temel alan sınıflar oluşturmak için

- Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.edmx /out:c:\northwind.cs
    ```

### <a name="to-generate-visual-basic-classes-based-on-the-edmx-file"></a>. Edmx dosyasına göre Visual Basic sınıfları oluşturmak için

- Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.edmx /out:c:\northwind.vb
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Hizmeti İstemci Kitaplığı Oluşturma](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)
- [Nasıl yapılır: Veri hizmeti başvurusu ekleme](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)
- [WCF Veri Hizmeti İstemci Yardımcı Programı (DataSvcUtil.exe)](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md)
