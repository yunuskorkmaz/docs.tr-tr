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
ms.openlocfilehash: 0d253e917d6f805c471f244cddea44f339343868
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025528"
---
# <a name="types-of-isolation"></a>Yalıtım Türleri
Yalıtılmış Depolama erişimi oluşturan kullanıcıya her zaman kısıtlandırılır. Bu tür bir yalıtım uygulamak için kod deposu açıldığında çalıştığı işlemle ilişkili kimlik olduğu ortak dil çalışma zamanı aynı işletim sistemini algılar, kullanıcı kimlik kavramını kullanır. Bu kimlik, kimliği doğrulanmış kullanıcı kimliği olmakla birlikte kimliğe bürünme dinamik olarak değiştirmek için geçerli kullanıcının kimliğini neden olabilir.  
  
 Yalıtılmış Depolama erişimi de uygulama etki alanı ve derlemeye veya tek başına bir derleme ile ilişkili kimliğine göre sınırlıdır. Çalışma zamanı bu kimlikleri aşağıdaki yollarla alır:  
  
- Etki alanı kimliği, tam bir URL olabilir, bir web uygulaması söz konusu olduğunda, uygulama kanıtı temsil eder. Kabuk barındırılan kodu için etki alanı kimliği uygulama dizini yola göre uyarlanabilir. Örneğin, yürütülebilir dosya yolu C:\Office\MyApp.exe çalışırsa, etki alanı kimliği C:\Office\MyApp.exe olacaktır.  
  
- Derleme, bütünleştirilmiş kanıt kimliğidir. Bu derlemenin olabilen bir şifreleme dijital imzadan gelebilir [tanımlayıcı ad](../../../docs/framework/app-domains/strong-named-assemblies.md), derleme veya URL kimliğini yazılım yayımcısı. Sonra bir derlemenin tanımlayıcı ad hem de bir yazılım yayımcı kimliği varsa yazılım yayımcı kimliği kullanılır. Derleme Internet'ten gelen ve imzasız ise URL kimlik kullanılır. Derlemeler ve güçlü adlar hakkında daha fazla bilgi için bkz. [Derlemelerle programlama](../../../docs/framework/app-domains/programming-with-assemblies.md).  
  
- Gezici depolarda gezici kullanıcı profili olan bir kullanıcı hesabı ile taşıyın. Dosyaları bir ağ dizinine yazılır ve kullanıcının oturum açtığı tüm bilgisayarlara indirilir. Gezici kullanıcı profilleri hakkında daha fazla bilgi için bkz: <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Roaming?displayProperty=nameWithType>.  
  
 Yalıtılmış Depolama, kullanıcı, etki alanı ve derleme kimliği kavramlarını birleştirerek her biri kendi kullanım senaryoları sahip aşağıdaki yollarla veri ayırabilirsiniz:  
  
- [Kullanıcı ve derlemeye göre yalıtım](#UserAssembly)  
  
- [Kullanıcı, etki alanı ve derlemeye göre yalıtım](#UserDomainAssembly)  
  
 Ya da bu ayırmayı gezici kullanıcı profili ile birleştirilebilir. Daha fazla bilgi için konudaki [yalıtılmış depolama ve dolaşım](#Roaming).  
  
 Farklı kapsamlarda yalıtılmış depoları nasıl aşağıda gösterilmektedir:  
  
 ![Kullanıcı ve derlemeye göre yalıtım gösteren diyagram.](./media/types-of-isolation/isolated-storage-types.gif)  
  
 Belirli bir bilgisayarın yerel depolama tesislerinin kullandığından depoları Dolaşım dışında yalıtılmış depolama her zaman örtük olarak bilgisayar tarafından izole edilmiş olduğunu unutmayın.  
  
> [!IMPORTANT]
>  Yalıtılmış depolama için uygun değildir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamalar. Bunun yerine, uygulama verisi sınıflarını kullanın `Windows.Storage` yerel verileri ve dosyaları depolamak için Windows çalışma zamanı API içinde bulunan ad alanları. Daha fazla bilgi için [uygulama verileri](https://docs.microsoft.com/previous-versions/windows/apps/hh464917(v=win.10)) Windows geliştirme Merkezi'nde.  
  
<a name="UserAssembly"></a>   
## <a name="isolation-by-user-and-assembly"></a>Kullanıcı ve Derlemeye Göre Yalıtım  
 Söz konusu verileri kullanan derleme etki alanından herhangi bir uygulamanın erişilebilir olması gerekiyor depoladığınızda, kullanıcı ve derlemeye göre yalıtım uygundur. Genellikle, bu durumda, yalıtılmış depolama birden çok uygulamada uygular ve kullanıcının adını veya lisans bilgileri gibi belirli bir uygulama için bağlı değildir verileri depolamak için kullanılır. Kullanıcı ve derlemeye göre yalıtılan depolamaya erişmek için kod uygulamalar arasında bilgi aktarımı yapmak güvenilir olması gerekir. Genellikle, kullanıcı ve derlemeye göre yalıtım, intranet ancak Internet'teki izin verilir. Statik çağırarak <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A?displayProperty=nameWithType> yöntemi ve bir kullanıcı ve bir derleme geçirme <xref:System.IO.IsolatedStorage.IsolatedStorageScope> bu tür bir yalıtım depolamayla döndürür.  
  
 Aşağıdaki kod örneği, kullanıcı ve derlemeye göre yalıtılır bir deposunu alır. Deponun erişilebilir `isoFile` nesne.  
  
 [!code-cpp[Conceptual.IsolatedStorage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#17)]
 [!code-csharp[Conceptual.IsolatedStorage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#17)]
 [!code-vb[Conceptual.IsolatedStorage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#17)]  
  
 Kanıt parametreleri kullanan bir örnek için bkz: <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%28System.IO.IsolatedStorage.IsolatedStorageScope%2CSystem.Security.Policy.Evidence%2CSystem.Type%2CSystem.Security.Policy.Evidence%2CSystem.Type%29>.  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> Aşağıdaki kod örneğinde gösterildiği gibi yöntemi bir kısayol olarak kullanılabilir. Bu kısayol, dolaşım özellikli olan mağazalar açmak için kullanılamaz; kullanma <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> Böyle durumlarda.  
  
 [!code-cpp[Conceptual.IsolatedStorage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#18)]
 [!code-csharp[Conceptual.IsolatedStorage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#18)]
 [!code-vb[Conceptual.IsolatedStorage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#18)]  
  
<a name="UserDomainAssembly"></a>   
## <a name="isolation-by-user-domain-and-assembly"></a>Kullanıcı, Etki Alanı ve Derlemeye Göre Yalıtım  
 Uygulamanız özel bir veri deposu gerektiren bir üçüncü taraf derleme kullanıyorsa, özel verileri depolamak için yalıtılmış depolamayı kullanabilirsiniz. Kullanıcı, etki alanı ve derlemeye göre yalıtım sağlar, bu, yalnızca belirli bir derlemede kod veri erişebilir ve yalnızca derlemenin derleme deposu oluşturduğunuzda çalıştığı uygulama tarafından kullanıldığında ve yalnızca kendisi için deponun oluşturulduğu kullanıcı çalıştırdığında  uygulama. Kullanıcı, etki alanı ve derlemeye göre yalıtım diğer uygulamalara veri sızmasını engellemek üçüncü taraf derleme tutar. Yalıtılmış Depolama kullanmak istiyorsanız ancak kullanmak için yalıtım türünü emin değilseniz biliyorsanız, varsayılan seçim bu yalıtım türü olmalıdır. Statik çağırarak <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> yöntemi <xref:System.IO.IsolatedStorage.IsolatedStorageFile> ve bir kullanıcı, etki alanı ve derlemeye geçirerek <xref:System.IO.IsolatedStorage.IsolatedStorageScope> bu tür bir yalıtım depolamayla döndürür.  
  
 Aşağıdaki kod örneği, kullanıcı, etki alanı ve derlemeye göre yalıtılan bir depo alır. Deponun erişilebilir `isoFile` nesne.  
  
 [!code-cpp[Conceptual.IsolatedStorage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#14)]
 [!code-csharp[Conceptual.IsolatedStorage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#14)]
 [!code-vb[Conceptual.IsolatedStorage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#14)]  
  
 Başka bir yöntem, aşağıdaki kod örneğinde gösterildiği gibi bir kısayol olarak kullanılabilir. Bu kısayol, dolaşım özellikli olan mağazalar açmak için kullanılamaz; kullanma <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> Böyle durumlarda.  
  
 [!code-cpp[Conceptual.IsolatedStorage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#15)]
 [!code-csharp[Conceptual.IsolatedStorage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#15)]
 [!code-vb[Conceptual.IsolatedStorage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#15)]  
  
<a name="Roaming"></a>   
## <a name="isolated-storage-and-roaming"></a>Ayrık Depolama ve Dolaşım  
 Gezici kullanıcı profilleri, bir ağ üzerinde bir kimlik ayarlamak ve herhangi ağ tüm kişiselleştirilmiş ayarları taşıyan bir bilgisayarda oturum açmak için bu kimlik kullanmak bir kullanıcı sağlayan bir Windows özelliğidir. Yalıtılmış depolama kullanan bir derleme, kullanıcının yalıtılmış depolama gezici kullanıcı profili ile taşınmalıdır belirtebilirsiniz. Gezici kullanıcı ve derlemeye göre yalıtım veya yalıtım ile birlikte kullanıcı, etki alanı ve derlemeye göre kullanılabilir. Dolaşım kapsam kullanılmıyorsa, gezici kullanıcı profili kullanıldığında bile depoları gezici olmaz.  
  
 Aşağıdaki kod örneği, kullanıcı ve derlemeye göre yalıtılan bir Dolaşım deposunu alır. Deponun erişilebilir `isoFile` nesne.  
  
 [!code-cpp[Conceptual.IsolatedStorage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#11)]
 [!code-csharp[Conceptual.IsolatedStorage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#11)]
 [!code-vb[Conceptual.IsolatedStorage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#11)]  
  
 Kullanıcı, etki alanınızı ve uygulama tarafından yalıtılmış bir Dolaşım deposu oluşturmak için bir etki alanı kapsamına eklenebilir. Aşağıdaki kod örneği bunu gösterir.  
  
 [!code-cpp[Conceptual.IsolatedStorage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#12)]
 [!code-csharp[Conceptual.IsolatedStorage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#12)]
 [!code-vb[Conceptual.IsolatedStorage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#12)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.IsolatedStorage.IsolatedStorageScope>
- [Yalıtılmış Depolama](../../../docs/standard/io/isolated-storage.md)
