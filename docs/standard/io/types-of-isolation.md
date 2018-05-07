---
title: Yalıtım Türleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- storing data using isolated storage, accessing isolated storage
- storing data using isolated storage, isolation types
- authentication [.NET Framework], isolated storage
- assemblies [.NET Framework], identity
- isolated storage, accessing
- data storage using isolated storage, isolation types
- data storage using isolated storage, accessing isolated storage
- domain identity
- isolated storage, types
- user authentication, isolated storage
ms.assetid: 14812988-473f-44ae-b75f-fd5c2f21fb7b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c0c888181b5f2150c37a87957cd932e10a36f7f4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="types-of-isolation"></a>Yalıtım Türleri
Yalıtılmış Depolama erişimi her zaman oluşturan kullanıcıya sınırlıdır. Bu tür bir yalıtım uygulamak için depolama açıldığında kodu çalıştığı işlemle ilişkili kimlik olduğu ortak dil çalışma zamanı işletim sistemini algılar, kullanıcı kimliği aynı kavramı kullanır. Bu kimlik, kimliği doğrulanmış kullanıcı kimliği olmakla birlikte kimliğe bürünme dinamik olarak değiştirmek için geçerli kullanıcının kimliğini neden olabilir.  
  
 Yalıtılmış Depolama erişimi de uygulama etki alanı ve derleme veya tek başına derleme ile ilişkili kimliğine göre kısıtlanır. Çalışma zamanı bu kimlikleri aşağıdaki yollarla alır:  
  
-   Etki alanı kimliği olabilen bir web uygulaması durumunda tam URL uygulama kanıtı temsil eder. Kabuk barındırılan kodu için etki alanı kimlik uygulama dizini yola göre. Örneğin, yürütülebilir dosya yolu C:\Office\MyApp.exe çalıştırıyorsa, etki alanı kimliği C:\Office\MyApp.exe olur.  
  
-   Derleme, derleme kanıtı kimliğidir. Bu derleme olabilen bir şifreleme dijital imzadan gelebilir [güçlü ad](../../../docs/framework/app-domains/strong-named-assemblies.md), derleme veya URL kimliğini yazılım yayımcısı. Bir derleme tanımlayıcı bir ad ve bir yazılım yayımcı kimliği varsa, yazılım yayımcı kimliği kullanılır. Derleme Internet'ten gelen ve imzasız ise, URL kimliği kullanılır. Derlemeler ve güçlü adları hakkında daha fazla bilgi için bkz: [Derlemelerle programlama](../../../docs/framework/app-domains/programming-with-assemblies.md).  
  
-   Dolaşım depoları gezici kullanıcı profiline sahip bir kullanıcı ile taşıyın. Dosyaları bir ağ dizinine yazılır ve kullanıcının oturum açtığı herhangi bir bilgisayara yüklenir. Gezici kullanıcı profilleri hakkında daha fazla bilgi için bkz: <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Roaming?displayProperty=nameWithType>.  
  
 Yalıtılmış Depolama, kullanıcı, etki alanı ve derleme kimlik kavramlarını birleştirerek, her birinin kendi kullanım senaryoları olan aşağıdaki yollarla veri ayırabilirsiniz:  
  
-   [Kullanıcı ve derlemeye göre yalıtım](#UserAssembly)  
  
-   [Kullanıcı, etki alanı ve derlemeye göre yalıtım](#UserDomainAssembly)  
  
 Bu ayırmayı birini bir gezici kullanıcı profili ile birleştirilebilir. Daha fazla bilgi için bkz [yalıtılmış depolama ve gezici](#Roaming).  
  
 Depoları farklı kapsamlarda nasıl yalıtılır aşağıdaki çizimde gösterilmektedir.  
  
 ![Kullanıcı ve derlemeye göre yalıtım](../../../docs/standard/io/media/typesofisolation.gif "typesofisolation")  
Yalıtılmış Depolama türleri  
  
 Belirli bir bilgisayarın yerel depolama tesisleri kullandığından depoları gezici dışında yalıtılmış depolama her zaman örtük olarak bilgisayar tarafından yalıtılır olduğunu unutmayın.  
  
> [!IMPORTANT]
>  Yalıtılmış depolama için kullanılabilir olmadığından [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamalar. Bunun yerine, uygulama veri sınıflarında kullanın `Windows.Storage` ad alanlarını dahil [!INCLUDE[wrt](../../../includes/wrt-md.md)] yerel verileri ve dosyaları depolamak için API. Daha fazla bilgi için bkz: [uygulama verilerini](/previous-versions/windows/apps/hh464917(v=win.10)) Windows geliştirme Merkezi'ndeki.  
  
<a name="UserAssembly"></a>   
## <a name="isolation-by-user-and-assembly"></a>Kullanıcı ve Derlemeye Göre Yalıtım  
 Veri kullanan derleme hiçbir uygulamanın etki alanından erişilebilir olması gerekiyor depoladığınızda, kullanıcı ve derlemeye göre yalıtım uygundur. Genellikle, bu durumda, yalıtılmış depolama birden çok uygulama arasında geçerlidir ve kullanıcının adını veya lisans bilgileri gibi belirli bir uygulama için bağlı değildir verileri depolamak için kullanılır. Kullanıcı ve derlemeye göre yalıtılmış depolama erişmek için kod uygulamalar arasında bilgi aktarımı yapmak için güvenilir olması gerekir. Genellikle, kullanıcı ve derlemeye göre yalıtım intranetler ancak Internet'te izin verilir. Statik çağırma <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A?displayProperty=nameWithType> yöntemi ve bir kullanıcı hem bir derlemeyi bilgilerinde <xref:System.IO.IsolatedStorage.IsolatedStorageScope> storage bu tür bir yalıtım ile döndürür.  
  
 Aşağıdaki kod örneğinde, kullanıcı ve derlemeye göre yalıtılmış bir mağaza alır. Mağaza üzerinden erişilen `isoFile` nesnesi.  
  
 [!code-cpp[Conceptual.IsolatedStorage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#17)]
 [!code-csharp[Conceptual.IsolatedStorage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#17)]
 [!code-vb[Conceptual.IsolatedStorage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#17)]  
  
 Kanıt parametreleri kullanan bir örnek için bkz: <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%28System.IO.IsolatedStorage.IsolatedStorageScope%2CSystem.Security.Policy.Evidence%2CSystem.Type%2CSystem.Security.Policy.Evidence%2CSystem.Type%29>.  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> Aşağıdaki kod örneğinde gösterildiği gibi yöntemi bir kısayol olarak kullanılabilir. Bu kısayol, dolaşım özellikli depoları'nı açmak için kullanılamaz; kullanmak <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> bu gibi durumlarda.  
  
 [!code-cpp[Conceptual.IsolatedStorage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#18)]
 [!code-csharp[Conceptual.IsolatedStorage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#18)]
 [!code-vb[Conceptual.IsolatedStorage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#18)]  
  
<a name="UserDomainAssembly"></a>   
## <a name="isolation-by-user-domain-and-assembly"></a>Kullanıcı, Etki Alanı ve Derlemeye Göre Yalıtım  
 Uygulamanız bir özel veri deposu gerektiren bir üçüncü taraf derleme kullanıyorsa, yalıtılmış depolama özel verileri depolamak için kullanabilirsiniz. Kullanıcı, etki alanı ve derlemeye göre yalıtım sağlar, bu, yalnızca belirli bir bütünleştirilmiş kodda veri erişebilir ve yalnızca derleme derleme deposu oluşturduğunuzda çalışan uygulama tarafından kullanıldığında ve yalnızca kendisi için depo oluşturuldu kullanıcı çalıştırdığında  uygulama. Kullanıcı, etki alanı ve derlemeye göre yalıtım diğer uygulamalara veri sızıntısı gelen üçüncü taraf derleme tutar. Yalıtılmış Depolama kullanmak istiyorsanız ancak kullanmak için yalıtım türünü emin değilseniz biliyorsanız, bu yalıtım türü varsayılan tercih ettiğiniz olmalıdır. Statik çağırma <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> yöntemi <xref:System.IO.IsolatedStorage.IsolatedStorageFile> ve bir kullanıcı, etki alanı ve derleme geçirme <xref:System.IO.IsolatedStorage.IsolatedStorageScope> storage bu tür bir yalıtım ile döndürür.  
  
 Aşağıdaki kod örneğinde, kullanıcı, etki alanı ve derleme tarafından yalıtılmış bir deposunu alır. Mağaza üzerinden erişilen `isoFile` nesnesi.  
  
 [!code-cpp[Conceptual.IsolatedStorage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#14)]
 [!code-csharp[Conceptual.IsolatedStorage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#14)]
 [!code-vb[Conceptual.IsolatedStorage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#14)]  
  
 Başka bir yöntem, aşağıdaki kod örneğinde gösterildiği gibi bir kısayol olarak kullanılabilir. Bu kısayol, dolaşım özellikli depoları'nı açmak için kullanılamaz; kullanmak <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> bu gibi durumlarda.  
  
 [!code-cpp[Conceptual.IsolatedStorage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#15)]
 [!code-csharp[Conceptual.IsolatedStorage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#15)]
 [!code-vb[Conceptual.IsolatedStorage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#15)]  
  
<a name="Roaming"></a>   
## <a name="isolated-storage-and-roaming"></a>Ayrık Depolama ve Dolaşım  
 Gezici kullanıcı profilleri ağ üzerinde bir kimlik ayarlama ve kimliğe herhangi ağ tüm kişiselleştirilmiş ayarları taşıyan bir bilgisayarda oturum açın, bir kullanıcının sağlayan bir Windows özelliğidir. Yalıtılmış depolama kullanan bir derlemeyi kullanıcının yalıtılmış depolama gezici kullanıcı profili ile taşımalısınız belirtebilirsiniz. Gezici kullanıcı ve derlemeye göre yalıtım veya yalıtım ile birlikte kullanıcı, etki alanı ve derleme tarafından kullanılabilir. Gezici bir kapsam kullanılmazsa, gezici kullanıcı profili kullanılsa bile depoları gezici olmaz.  
  
 Aşağıdaki kod örneğinde, kullanıcı ve derlemeye göre yalıtılmış bir gezici deposunu alır. Mağaza üzerinden erişilen `isoFile` nesnesi.  
  
 [!code-cpp[Conceptual.IsolatedStorage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#11)]
 [!code-csharp[Conceptual.IsolatedStorage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#11)]
 [!code-vb[Conceptual.IsolatedStorage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#11)]  
  
 Kullanıcı, etki alanı ve uygulama tarafından yalıtılmış bir gezici deposu oluşturmak için bir etki alanı kapsamı eklenebilir. Aşağıdaki kod örneğinde bu gösterir.  
  
 [!code-cpp[Conceptual.IsolatedStorage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#12)]
 [!code-csharp[Conceptual.IsolatedStorage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#12)]
 [!code-vb[Conceptual.IsolatedStorage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#12)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IO.IsolatedStorage.IsolatedStorageScope>  
 [Yalıtılmış Depolama](../../../docs/standard/io/isolated-storage.md)
