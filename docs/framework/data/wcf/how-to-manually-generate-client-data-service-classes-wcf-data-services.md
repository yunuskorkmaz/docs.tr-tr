---
title: "Nasıl yapılır: istemci verileri hizmet sınıfları (WCF Veri Hizmetleri) el ile oluştur"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, client library
ms.assetid: b98cb1d6-956a-4e50-add6-67e4f2587346
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f72f898b2a80d7d88a74deabe013e2eecc298bdd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-manually-generate-client-data-service-classes-wcf-data-services"></a>Nasıl yapılır: istemci verileri hizmet sınıfları (WCF Veri Hizmetleri) el ile oluştur
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]İstemci veri hizmeti sınıfları kullandığınızda otomatik olarak oluşturmak üzere etkinleştirmek için Visual Studio ile tümleşir **hizmet Başvurusu Ekle** bir başvuru veri hizmeti için bir Visual Studio projesi eklemek için iletişim kutusu. Daha fazla bilgi için bkz: [nasıl yapılır: bir veri hizmet Başvurusu Ekle](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md). Kod oluşturma aracı kullanarak el ile de aynı istemci veri hizmeti sınıfları oluşturabilirsiniz `DataSvcUtil.exe`. Bu araç ile birlikte [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], .NET Framework sınıfları veri hizmeti tanımı oluşturur. Ayrıca, kavramsal model (.csdl) dosyası ve bir Visual Studio projesi Entity Framework modelinde temsil eden .edmx dosyasının'ndan veri hizmeti sınıfları oluşturmak için de kullanılabilir.  
  
 Bu konudaki örnek Northwind örnek veri hizmetini temel alan istemci veri hizmeti sınıfları oluşturur. Bu hizmeti tamamladığınızda oluşturulan [WCF Veri Hizmetleri quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md). Bu konudaki bazı örnekler Northwind modeli için kavramsal model dosyası gerektirir. Daha fazla bilgi için bkz: [nasıl yapılır: dosya eşleme ve Model oluşturmak için kullanım EdmGen.exe](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md). Bu konudaki bazı örnekler için Northwind modeli .edmx dosyasının gerektirir. Daha fazla bilgi için bkz: [.edmx dosyasının genel bakış](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4).  
  
### <a name="to-generate-c-classes-that-support-data-binding"></a>Veri bağlamayı destekleyen C# sınıfları oluşturmak için  
  
-   Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:CSharp /out:Northwind.cs /uri:http://localhost:12345/Northwind.svc  
    ```  
  
    > [!NOTE]
    >  İçin sağlanan değer değiştirmelisiniz `/uri:` Northwind örnek veri hizmeti örneğiniz URI'sini parametresiyle.  
  
### <a name="to-generate-visual-basic-classes-that-support-data-binding"></a>Veri bağlamayı destekleyen Visual Basic sınıfları oluşturmak için  
  
-   Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc  
    ```  
  
    > [!NOTE]
    >  İçin sağlanan değer değiştirmelisiniz `/uri:` Northwind örnek veri hizmeti örneğiniz URI'sini parametresiyle.  
  
### <a name="to-generate-c-classes-based-on-the-service-uri"></a>Hizmet URI'si temel C# sınıfları oluşturmak için  
  
-   Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /language:CSharp /out:northwind.cs /uri:http://localhost:12345/Northwind.svc  
    ```  
  
    > [!NOTE]
    >  İçin sağlanan değer değiştirmelisiniz `/uri:` Northwind örnek veri hizmeti örneğiniz URI'sini parametresiyle.  
  
### <a name="to-generate-visual-basic-classes-based-on-the-service-uri"></a>Visual Basic sınıfları URI hizmetini temel alan oluşturmak için  
  
-   Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc  
    ```  
  
    > [!NOTE]
    >  İçin sağlanan değer değiştirmelisiniz `/uri:` Northwind örnek veri hizmeti örneğiniz URI'sini parametresiyle.  
  
### <a name="to-generate-c-classes-based-on-the-conceptual-model-file-csdl"></a>Kavramsal model dosyasını (CSDL) temel alan C# sınıfları oluşturmak için  
  
-   Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.csdl /out:Northwind.cs  
    ```  
  
### <a name="to-generate-visual-basic-classes-based-on-the-conceptual-model-file-csdl"></a>Visual Basic sınıfları kavramsal model dosyasını (CSDL) temel alan oluşturmak için  
  
-   Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.csdl /out:Northwind.vb  
    ```  
  
### <a name="to-generate-c-classes-based-on-the-edmx-file"></a>.Edmx dosyasını temel alarak C# sınıfları oluşturmak için  
  
-   Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.edmx /out:c:\northwind.cs   
    ```  
  
### <a name="to-generate-visual-basic-classes-based-on-the-edmx-file"></a>Visual Basic sınıfları .edmx dosyasını temel alan oluşturmak için  
  
-   Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.edmx /out:c:\northwind.vb   
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Hizmeti İstemci Kitaplığı Oluşturma](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)  
 [Nasıl yapılır: Veri Hizmeti Başvurusu Ekleme](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)  
 [WCF Veri Hizmeti İstemci Yardımcı Programı (DataSvcUtil.exe)](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md)
