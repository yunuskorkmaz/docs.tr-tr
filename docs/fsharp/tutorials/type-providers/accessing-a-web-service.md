---
title: 'İzlenecek yol - tür sağlayıcıları (F #) kullanarak Web hizmetine erişim'
description: 'Web Hizmetleri Açıklama Dili (WSDL) türü sağlayıcısı F # 3.0 kullanılabilir bir WSDL hizmete erişmek için nasıl kullanılacağını öğrenin.'
keywords: 'Visual f #, f # işlevsel programlama'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 63374fa9-8fb8-43ac-bcb9-ef2290d9f851
ms.openlocfilehash: 2929198172a4e9f908daa64af19208e07859263f
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/10/2018
---
# <a name="walkthrough-accessing-a-web-service-by-using-type-providers"></a>İzlenecek yol: Tür Sağlayıcılarını Kullanarak Web Hizmetine Erişim

> [!NOTE]
Bu kılavuz, F # 3.0 için yazılmıştır ve güncelleştirilir.  Bkz: [FSharp.Data](https://fsharp.github.io/FSharp.Data/) güncel, platformlar arası tür sağlayıcıları için.

> [!NOTE]
API başvuru bağlantılar için MSDN götürür.  Docs.microsoft.com API Başvurusu tamamlanmadı.

Bu kılavuz, F # bir WSDL hizmete erişmek için 3. 0'kullanılabilir Web Hizmetleri Açıklama Dili (WSDL) türü sağlayıcısının nasıl kullanılacağını gösterir. Diğer .NET dilleri tarafından arama svcutil.exe web hizmetine erişmek için kod oluşturmak veya web başvuru ekleyerek, örneğin, C# proje sizin için svcutil.exe çağırmak için Visual Studio almak için. F #'ta, WsdlService tür oluşturan kodu yazma WSDL türü sağlayıcısı kadar kısa sürede, kullanarak ek bir seçeneğiniz vardır, türleri oluşturulur ve kullanılabilir hale gelir. Bu işlem kodu yazarken kullanılabilir olmasını durduracak Hizmeti'ne bağlıdır.

Bu kılavuz aşağıdaki görevler gösterilir. Bu sırada başarılı olması gözden geçirme tamamlamalısınız:


- Projeyi oluşturma
<br />

- Tür sağlayıcısını yapılandırma 
<br />

- Web hizmeti çağıran ve sonuçları işleme
<br />


## <a name="creating-the-project"></a>Projeyi oluşturma
Adımda bir proje oluşturun ve WSDL tür sağlayıcısı kullanmak için uygun başvurular ekleyin.


#### <a name="to-create-and-set-up-an-f-project"></a>Bir F# projesi oluşturmak ve ayarlamak için

1. Yeni bir F # konsol uygulama projesi açın.
<br />

2. İçinde **Çözüm Gezgini**, projenin için kısayol menüsünü açın **başvuru** düğümünü ve ardından **Başvuru Ekle**.
<br />

3. İçinde **derlemeleri** alanı seçin **Framework**ve ardından kullanılabilir derlemeleri listesinden seçip **System.Runtime.Serialization** ve  **System.ServiceModel**.
<br />

4. İçinde **derlemeleri** alanı seçin **uzantıları**.
<br />

5. Kullanılabilir derlemeleri listesinden seçip **FSharp.Data.TypeProviders**ve ardından **Tamam** düğmesi bu derlemelerine başvurular ekleyin.
<br />

## <a name="configuring-the-type-provider"></a>Tür sağlayıcısını yapılandırma 
Bu adımda, TerraServer web hizmeti türleri oluşturmak için WSDL türü sağlayıcısı kullanın.


#### <a name="to-configure-the-type-provider-and-generate-types"></a>Tür sağlayıcısını yapılandırmak ve türleri üretmek için

1. Aşağıdaki türü sağlayıcı ad alanı açmak için kod satırını ekleyin.
<br />

```fsharp
open System
open System.ServiceModel
open Microsoft.FSharp.Linq
open Microsoft.FSharp.Data.TypeProviders
```

2. Aşağıdaki web hizmetiyle türü sağlayıcısı çağırmak için kod satırını ekleyin. Bu örnekte, TerraServer web hizmetini kullanır.
<br />

```fsharp
type TerraService = WsdlService<" HYPERLINK "https://terraserver-usa.com/TerraService2.asmx?WSDL" https://msrmaps.com/TerraService2.asmx?WSDL">
```

  Kırmızı dalgalı hizmet URI'si yanlış yazılmış olup olmadığını hizmeti çalışmıyor veya gerçekleştirme değil, bu kod satırı altında görüntülenir. Kod noktası ise, bir hata iletisi sorununu açıklar. Aynı bilgiler bulabilirsiniz **hata listesi** penceresi veya **çıktı penceresi** oluşturacağınız sonra.
<br />  Proje için app.config dosyasını kullanarak veya statik tür parametreleri tür sağlayıcı bildiriminde kullanarak bir WSDL bağlantısı için yapılandırma ayarlarını belirtmek için iki yolu vardır. Uygun yapılandırma dosyası öğelerini oluşturmak için svcutil.exe kullanma. Bir web hizmeti için yapılandırma bilgilerini oluşturmak için svcutil.exe kullanma hakkında daha fazla bilgi için bkz: [ServiceModel meta veri yardımcı Programracı &#40;Svcutil.exe&#41;](https://msdn.microsoft.com/library/aa347733.aspx). Statik tür parametreleri WSDL türü sağlayıcısı için tam bir açıklaması için bkz: [WsdlService türü sağlayıcısı](https://msdn.microsoft.com/visualfsharpdocs/conceptual/wsdlservice-type-provider-%5bfsharp%5d).
<br />

## <a name="calling-the-web-service-and-processing-the-results"></a>Web hizmeti çağıran ve sonuçları işleme
Her web hizmeti parametreleri olarak kendi yöntem çağrıları için kullanılan türleri kendi kümesi vardır. Bu adımda, bu parametreler hazırlamak, bir web yöntemini çağırın ve bu bilgileri işlem.


#### <a name="to-call-the-web-service-and-process-the-results"></a>Web hizmetini çağırmak ve sonuçları işlemek için

1. Web hizmeti zaman aşımına uğrar veya web hizmeti çağrısı bir özel durum işleme bloğu içinde içermelidir şekilde, çalışmamaya olabilir. Web hizmetinden veri al denemek için aşağıdaki kodu yazın.
<br />

```fsharp
try
  let terraClient = TerraService.GetTerraServiceSoap ()
  let myPlace = new TerraService.ServiceTypes.msrmaps.com.Place(City = "Redmond", State = "Washington", Country = "United States")
  let myLocation = terraClient.ConvertPlaceToLonLatPt(myPlace)
  printfn "Redmond Latitude: %f Longitude: %f" (myLocation.Lat) (myLocation.Lon)
with
| :? ServerTooBusyException as exn ->
  let innerMessage =
    match (exn.InnerException) with
    | null -> ""
    | innerExn -> innerExn.Message
  printfn "An exception occurred:\n %s\n %s" exn.Message innerMessage
| exn -> printfn "An exception occurred: %s" exn.Message
```

Gibi web hizmeti için gerekli olan veri türleri oluşturmak fark **yer** ve **konumu**, iç içe geçmiş türler WsdlService altında yazarken **TerraService**.
<br />


## <a name="see-also"></a>Ayrıca Bkz.
[WsdlService türü sağlayıcısı](https://msdn.microsoft.com/visualfsharpdocs/conceptual/wsdlservice-type-provider-%5bfsharp%5d)

[Tür Sağlayıcıları](index.md)
