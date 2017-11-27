---
title: "Nasıl yapılır: veri hizmeti için bir istek (WCF Veri Hizmetleri) istemci kimlik bilgilerini belirtin"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: WCF Data Services, customizing requests
ms.assetid: 1632f9af-e45f-4363-9222-03823daa8e28
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 88e41101ab9a963ac09610b04afee745aa61c8e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-client-credentials-for-a-data-service-request-wcf-data-services"></a>Nasıl yapılır: veri hizmeti için bir istek (WCF Veri Hizmetleri) istemci kimlik bilgilerini belirtin
Varsayılan olarak, kimlik bilgileri istemci kitaplığı için bir istek gönderirken sağlamıyor bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] hizmet. Bununla birlikte, kimlik bilgileri sağlayarak veri hizmeti isteklerine kimlik doğrulaması gönderilmesi belirtebilirsiniz bir <xref:System.Net.NetworkCredential> için <xref:System.Data.Services.Client.DataServiceContext.Credentials%2A> özelliği <xref:System.Data.Services.Client.DataServiceContext>. Daha fazla bilgi için bkz: [WCF Veri Hizmetleri güvenli hale getirme](../../../../docs/framework/data/wcf/securing-wcf-data-services.md). Bu konudaki örnek açıkça tarafından kullanılan kimlik bilgilerini sağlamak üzere gösterilmiştir [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] veri hizmetinden veri isterken, istemci.  
  
 Bu konudaki örnek Northwind örnek veri hizmeti ve otomatik olarak oluşturulur istemci veri hizmeti sınıflarını kullanır. Bu hizmet ve istemci veri sınıfları tamamladığınızda oluşturduğunuz [WCF Veri Hizmetleri quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md). Aynı zamanda [Northwind örnek veri hizmeti](http://go.microsoft.com/fwlink/?LinkId=187426) üzerinde yayımlanan [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Web sitesi; bu örnek veri hizmetidir salt okunur ve değişikliklerinizi kaydetmeye çalışırken bir hata döndürür. Örnek Veri Hizmetleri üzerinde [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Web sitesinin anonim kimlik doğrulaması izin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, Windows Presentation Framework uygulaması'nın ana sayfasında bir Genişletilebilir uygulama biçimlendirme dili (XAML) dosya için arka plan kod sayfası arasındadır. Bu örnek görüntüler bir `LoginWindow` kimlik doğrulaması toplamak için örnek kullanıcıdan kimlik bilgileri ve ardından veri hizmetine bir istek yaparken, bu kimlik bilgilerini kullanır.  
  
 [!code-csharp[Astoria Northwind Client#ClientCredentials](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/clientcredentials.xaml.cs#clientcredentials)]  
 [!code-vb[Astoria Northwind Client#ClientCredentials](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/clientcredentials.xaml.vb#clientcredentials)]
  
## <a name="example"></a>Örnek  
 Aşağıdaki XAML WPF Uygulaması'nın ana sayfasında tanımlar.  
  
 [!code-xaml[Astoria Northwind Client#ClientCredentialsXaml](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/clientcredentials.xaml#clientcredentialsxaml)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir istek veri hizmeti yapmadan önce kullanıcıdan kimlik doğrulaması bilgilerini toplamak için kullanılan pencere için arka plan kodu sayfanın arasındadır.  
  
 [!code-csharp[Astoria Northwind Client#ClientCredentialsLogin](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/clientcredentialslogin.xaml.cs#clientcredentialslogin)]  
 [!code-vb[Astoria Northwind Client#ClientCredentialsLogin](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/clientcredentialslogin.xaml.vb#clientcredentialslogin)]
  
## <a name="example"></a>Örnek  
 Aşağıdaki XAML WPF uygulaması oturum açma bilgileri tanımlar.  
  
 [!code-xaml[Astoria Northwind Client#ClientCredentialsLoginXaml](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/clientcredentialslogin.xaml#clientcredentialsloginxaml)]  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Bu konudaki örnek için aşağıdaki güvenlik değerlendirmeleri geçerlidir:  
  
-   Bu örnekte sağlanan kimlik bilgileri çalıştığını doğrulamak için Northwind veri hizmeti anonim erişim dışında bir kimlik doğrulama düzeni kullanmanız gerekir. Aksi takdirde, veri hizmeti barındıran Web sitesinin kimlik bilgileri istenmez.  
  
-   Kullanıcı kimlik bilgileri yürütme sırasında yalnızca istenen ve önbelleğe. Kimlik bilgileri her zaman güvenli bir şekilde depolanması gerekir.  
  
-   Verileri bir saldırganın tarafından görülebilir için temel ve Özet kimlik doğrulaması ile gönderilen veriler şifrelenmez. Ayrıca, temel kimlik doğrulaması kimlik bilgilerini (kullanıcı adı ve parola) temiz metin olarak gönderilir ve geçirilebilir.  
  
 Daha fazla bilgi için bkz: [WCF Veri Hizmetleri güvenli hale getirme](../../../../docs/framework/data/wcf/securing-wcf-data-services.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Veri Hizmetleri güvenli hale getirme](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)  
 [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
