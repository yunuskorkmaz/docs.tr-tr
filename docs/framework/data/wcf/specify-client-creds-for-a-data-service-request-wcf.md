---
title: 'Nasıl yapılır: Bir veri hizmeti Isteği için Istemci kimlik bilgilerini belirtin (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing requests
ms.assetid: 1632f9af-e45f-4363-9222-03823daa8e28
ms.openlocfilehash: 4177b7f5138bd3e3ddd63e4a0d8d4bcb2be01fbb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790328"
---
# <a name="how-to-specify-client-credentials-for-a-data-service-request-wcf-data-services"></a>Nasıl yapılır: Bir veri hizmeti Isteği için Istemci kimlik bilgilerini belirtin (WCF Veri Hizmetleri)
Varsayılan olarak, istemci kitaplığı bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] hizmete istek gönderilirken kimlik bilgileri sağlamaz. Ancak, <xref:System.Net.NetworkCredential> <xref:System.Data.Services.Client.DataServiceContext>için bir <xref:System.Data.Services.Client.DataServiceContext.Credentials%2A> özelliği sağlayarak veri hizmetine isteklerin kimliğini doğrulamak üzere kimlik bilgilerinin gönderilmesini belirtebilirsiniz. Daha fazla bilgi için bkz. [güvenliği WCF veri Hizmetleri](securing-wcf-data-services.md). Bu konudaki örnekte, veri hizmetinden veri istenirken [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] istemci tarafından kullanılan kimlik bilgilerinin açık bir şekilde nasıl sağlanması gösterilmektedir.  
  
 Bu konudaki örnek, Northwind örnek veri hizmeti ve otomatik olarak istemci veri hizmeti sınıflarını kullanır. Bu hizmet ve istemci veri sınıfları, [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Web sitesinde yayımlanan [Northwind örnek veri hizmetini](https://go.microsoft.com/fwlink/?LinkId=187426) de kullanabilirsiniz; Bu örnek veri hizmeti salt okunurdur ve değişiklikler kaydedilmeye çalışıldığında bir hata döndürülür. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Web sitesindeki örnek veri hizmetleri anonim kimlik doğrulamasına izin verir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, Windows Presentation Framework uygulamasının ana sayfası olan bir Extensible Application Markup Language (XAML) dosyası için arka plan kod sayfasından oluşur. Bu örnek, kullanıcıdan `LoginWindow` kimlik doğrulama kimlik bilgilerini toplamak için bir örnek görüntüler ve ardından veri hizmetine bir istek yaparken bu kimlik bilgilerini kullanır.  
  
 [!code-csharp[Astoria Northwind Client#ClientCredentials](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/clientcredentials.xaml.cs#clientcredentials)]  
 [!code-vb[Astoria Northwind Client#ClientCredentials](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/clientcredentials.xaml.vb#clientcredentials)]
  
## <a name="example"></a>Örnek  
 Aşağıdaki XAML WPF uygulamasının ana sayfasını tanımlar.  
  
 [!code-xaml[Astoria Northwind Client#ClientCredentialsXaml](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/clientcredentials.xaml#clientcredentialsxaml)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, veri hizmetine bir istek yapmadan önce kullanıcıdan kimlik doğrulama kimlik bilgilerini toplamak için kullanılan pencere için arka plan kod sayfasından verilmiştir.  
  
 [!code-csharp[Astoria Northwind Client#ClientCredentialsLogin](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/clientcredentialslogin.xaml.cs#clientcredentialslogin)]  
 [!code-vb[Astoria Northwind Client#ClientCredentialsLogin](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/clientcredentialslogin.xaml.vb#clientcredentialslogin)]
  
## <a name="example"></a>Örnek  
 Aşağıdaki XAML WPF uygulamasının oturum açma bilgilerini tanımlar.  
  
 [!code-xaml[Astoria Northwind Client#ClientCredentialsLoginXaml](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/clientcredentialslogin.xaml#clientcredentialsloginxaml)]  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Bu konudaki örnek için aşağıdaki güvenlik konuları geçerlidir:  
  
- Bu örnekte sağlanan kimlik bilgilerinin çalıştığını doğrulamak için, Northwind veri hizmetinin anonim erişim dışında bir kimlik doğrulama düzeni kullanması gerekir. Aksi halde, veri hizmetini barındıran Web sitesi kimlik bilgileri istemeyecektir.  
  
- Kullanıcı kimlik bilgileri yalnızca yürütme sırasında istenir ve önbelleğe alınmamalıdır. Kimlik bilgilerinin her zaman güvenli bir şekilde depolanması gerekir.  
  
- Temel ve Özet kimlik doğrulamasıyla gönderilen veriler şifrelenmemiştir, bu nedenle veriler bir saldırgan tarafından görülebilir. Ayrıca, temel kimlik doğrulama kimlik bilgileri (Kullanıcı adı ve parola) düz metin olarak gönderilir ve yakalanabilir.  
  
 Daha fazla bilgi için bkz. [güvenliği WCF veri Hizmetleri](securing-wcf-data-services.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetlerinin Güvenliğini Sağlama](securing-wcf-data-services.md)
- [WCF Veri Hizmetleri İstemci Kitaplığı](wcf-data-services-client-library.md)
