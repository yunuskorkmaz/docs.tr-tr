---
title: 'Nasıl yapılır: bir veri hizmeti isteği (WCF Veri Hizmetleri) istemci kimlik bilgilerini belirtin'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing requests
ms.assetid: 1632f9af-e45f-4363-9222-03823daa8e28
ms.openlocfilehash: d0fbf01de05a02c03782af9e392a79b6dd3e8bee
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43402527"
---
# <a name="how-to-specify-client-credentials-for-a-data-service-request-wcf-data-services"></a>Nasıl yapılır: bir veri hizmeti isteği (WCF Veri Hizmetleri) istemci kimlik bilgilerini belirtin
Varsayılan olarak, kimlik bilgilerini istemci kitaplığı için bir isteği gönderirken sağlamaz bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] hizmeti. Ancak, kimlik bilgilerini sağlayarak istekleri veri hizmeti kimlik doğrulaması gönderilmesi belirtebilirsiniz bir <xref:System.Net.NetworkCredential> için <xref:System.Data.Services.Client.DataServiceContext.Credentials%2A> özelliği <xref:System.Data.Services.Client.DataServiceContext>. Daha fazla bilgi için [WCF Veri Hizmetleri güvenli hale getirme](../../../../docs/framework/data/wcf/securing-wcf-data-services.md). Bu konudaki örnek açıkça tarafından kullanılan kimlik bilgilerini sağlamak üzere nasıl gösterir [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] veriler veri hizmetinden isterken istemci.  
  
 Bu konudaki örnek Northwind örnek veri hizmeti ve otomatik olarak oluşturulan istemci veri hizmeti sınıfları kullanır. Bu hizmet ve istemci veri sınıfları tamamladığınızda oluşturulur [WCF Veri Hizmetleri Hızlı Başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md). Ayrıca [Northwind örnek veri hizmeti](https://go.microsoft.com/fwlink/?LinkId=187426) üzerinde yayımlanan [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Web sitesi; bu örnek verileri hizmeti salt okunur ve değişiklikleri farklı kaydedilmeye çalışılırken bir hata döndürür. Örnek verileri hizmetlerine [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Web sitesine izin ver, anonim kimlik doğrulaması.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, Windows Presentation Framework uygulaması'nın ana sayfasında Extensible Application Markup Language (XAML) dosyası için arka plan kod sayfası arasındadır. Bu örnek görüntüler bir `LoginWindow` örnek kimlik doğrulama toplamak için kullanıcıdan kimlik bilgileri ve daha sonra veri hizmetine istek yaparken, bu kimlik bilgilerini kullanır.  
  
 [!code-csharp[Astoria Northwind Client#ClientCredentials](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/clientcredentials.xaml.cs#clientcredentials)]  
 [!code-vb[Astoria Northwind Client#ClientCredentials](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/clientcredentials.xaml.vb#clientcredentials)]
  
## <a name="example"></a>Örnek  
 WPF Uygulaması'nın ana sayfasında aşağıdaki XAML tanımlar.  
  
 [!code-xaml[Astoria Northwind Client#ClientCredentialsXaml](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/clientcredentials.xaml#clientcredentialsxaml)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, veri hizmetine bir istek yapmadan önce kullanıcıdan kimlik doğrulama bilgilerini toplamak için kullanılan pencere için arka plan kod sayfası arasındadır.  
  
 [!code-csharp[Astoria Northwind Client#ClientCredentialsLogin](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/clientcredentialslogin.xaml.cs#clientcredentialslogin)]  
 [!code-vb[Astoria Northwind Client#ClientCredentialsLogin](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/clientcredentialslogin.xaml.vb#clientcredentialslogin)]
  
## <a name="example"></a>Örnek  
 Aşağıdaki XAML WPF uygulaması oturum açma bilgileri tanımlar.  
  
 [!code-xaml[Astoria Northwind Client#ClientCredentialsLoginXaml](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/clientcredentialslogin.xaml#clientcredentialsloginxaml)]  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Bu konudaki örnek için aşağıdaki güvenlik değerlendirmeleri geçerlidir:  
  
-   Bu örnekte verilen kimlik bilgilerinin çalıştığını doğrulamak için Northwind verileri hizmeti anonim erişim dışında bir kimlik doğrulama şeması kullanması gerekir. Aksi halde, veri hizmetini barındıran Web sitesinin kimlik bilgileri istenmez.  
  
-   Kullanıcı kimlik bilgileri, yürütme sırasında yalnızca istenen ve önbelleğe. Kimlik bilgileri her zaman güvenli bir şekilde depolanması gerekir.  
  
-   Temel ve Özet kimlik doğrulaması ile gönderilen veriler şifrelenmez, bu şekilde verileri bir saldırgan tarafından görülebilir. Ayrıca, temel kimlik doğrulaması kimlik bilgilerini (kullanıcı adı ve parola) düz metin olarak gönderilir ve kesilebilir.  
  
 Daha fazla bilgi için [WCF Veri Hizmetleri güvenli hale getirme](../../../../docs/framework/data/wcf/securing-wcf-data-services.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Veri Hizmetlerinin Güvenliğini Sağlama](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)  
 [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
