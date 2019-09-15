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
ms.openlocfilehash: c6c5337fedd13cb18b8e5eeadec48a2e4695a543
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70969348"
---
# <a name="types-of-isolation"></a>Yalıtım Türleri
Yalıtılmış depolamaya erişim, her zaman onu oluşturan kullanıcıyla kısıtlanır. Bu tür yalıtımın uygulanması için ortak dil çalışma zamanı, işletim sisteminin tanıdığı aynı kullanıcı kimliği kavramını kullanır. Bu, mağaza açıldığında kodun çalıştırıldığı işlemle ilişkili kimliktir. Bu kimlik kimliği doğrulanmış bir kullanıcı kimliğidir, ancak kimliğe bürünme geçerli kullanıcının kimliğinin dinamik olarak değişmesine neden olabilir.  
  
 Yalıtılmış depolamaya erişim, uygulamanın etki alanı ve derlemesi ile ilişkili kimliğe veya tek başına derlemeye göre de kısıtlanır. Çalışma zamanı bu kimlikleri aşağıdaki yollarla edinir:  
  
- Etki alanı kimliği, uygulamanın kanıtını temsil eder. Bu, bir Web uygulaması durumunda tam URL olabilir. Kabukta barındırılan kod için etki alanı kimliği, uygulama dizini yolunu temel alabilir. Örneğin, yürütülebilir C:\Office\MyApp.exe yolundan çalışırsa, etki alanı kimliği C:\Office\MyApp.exeolur.  
  
- Bütünleştirilmiş kod kimliği derleme kanıtdır. Bu, derlemenin [tanımlayıcı adı](../assembly/strong-named.md), derlemenin yazılım YAYıMCıSı veya URL kimliği olabilen bir şifrelenmiş dijital imzadan gelebilir. Bir derlemede hem tanımlayıcı adı hem de yazılım yayımcısı kimliği varsa, yazılım yayımcısı kimliği kullanılır. Derleme Internet 'ten geliyorsa ve imzasız ise, URL kimliği kullanılır. Derlemeler ve tanımlayıcı adlar hakkında daha fazla bilgi için bkz. [Derlemelerle programlama](../assembly/program.md).  
  
- Dolaşım depoları, gezici kullanıcı profiline sahip bir kullanıcıyla birlikte taşınır. Dosyalar bir ağ dizinine yazılır ve kullanıcının oturum açtığı herhangi bir bilgisayara indirilir. Gezici Kullanıcı profilleri hakkında daha fazla bilgi için bkz <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Roaming?displayProperty=nameWithType>.  
  
 Yalıtılmış depolama, Kullanıcı, etki alanı ve derleme kimliği kavramlarını birleştirerek verileri aşağıdaki yollarla yalıtabilir, her biri kendi kullanım senaryolarına sahiptir:  
  
- [Kullanıcı ve derlemeye göre yalıtım](#UserAssembly)  
  
- [Kullanıcı, etki alanı ve derlemeye göre yalıtım](#UserDomainAssembly)  
  
 Bu ısodılardan biri, bir dolaşım kullanıcı profiliyle birleştirilebilir. Daha fazla bilgi için, [yalıtılmış depolama ve dolaşım](#Roaming)bölümüne bakın.  
  
 Aşağıdaki çizimde, mağazaların farklı kapsamlarda nasıl yalıtımlı gösterilmektedir:  
  
 ![Kullanıcı ve derlemeye göre yalıtımı gösteren diyagram.](./media/types-of-isolation/isolated-storage-types.gif)  
  
 Dolaşım depoları hariç, belirli bir bilgisayarda yerel olan depolama olanaklarını kullandığından yalıtılmış depolamanın her zaman bilgisayar tarafından örtük olarak yalıtılmış olduğunu unutmayın.  
  
> [!IMPORTANT]
> Yalıtılmış depolama, uygulamalar için [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] kullanılamaz. Bunun yerine, yerel verileri ve dosyaları depolamak için `Windows.Storage` Windows çalışma zamanı API 'sinde bulunan ad alanlarında uygulama veri sınıflarını kullanın. Daha fazla bilgi için bkz. Windows Geliştirme Merkezi 'nde [uygulama verileri](https://docs.microsoft.com/previous-versions/windows/apps/hh464917(v=win.10)) .  
  
<a name="UserAssembly"></a>   
## <a name="isolation-by-user-and-assembly"></a>Kullanıcı ve Derlemeye Göre Yalıtım  
 Veri deposunu kullanan derlemeye herhangi bir uygulamanın etki alanından erişilebilir olması gerektiğinde, Kullanıcı ve derlemeye göre yalıtım uygundur. Genellikle, bu durumda, yalıtılmış depolama, birden fazla uygulama için geçerli olan ve kullanıcının adı ya da lisans bilgileri gibi belirli bir uygulamaya bağlı olmayan verileri depolamak için kullanılır. Kullanıcı ve derlemeye göre yalıtılmış depolamaya erişmek için, kodun uygulamalar arasında aktarılmasını sağlamak üzere koda güvenilmesi gerekir. Genellikle, Kullanıcı ve derlemeye göre yalıtım için Internet 'te değil, intranet üzerinde izin verilir. Statik <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A?displayProperty=nameWithType> yöntemi çağırmak ve bir kullanıcıya geçirmek, bir derlemeyi <xref:System.IO.IsolatedStorage.IsolatedStorageScope> bu tür yalıtımına sahip bir depolama döndürür.  
  
 Aşağıdaki kod örneği, Kullanıcı ve derleme tarafından yalıtılmış bir depo alır. Depoya `isoFile` nesne üzerinden erişilebilir.  
  
 [!code-cpp[Conceptual.IsolatedStorage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#17)]
 [!code-csharp[Conceptual.IsolatedStorage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#17)]
 [!code-vb[Conceptual.IsolatedStorage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#17)]  
  
 Kanıt parametrelerini kullanan bir örnek için bkz <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%28System.IO.IsolatedStorage.IsolatedStorageScope%2CSystem.Security.Policy.Evidence%2CSystem.Type%2CSystem.Security.Policy.Evidence%2CSystem.Type%29>.  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> Yöntemi, aşağıdaki kod örneğinde gösterildiği gibi bir kısayol olarak kullanılabilir. Bu kısayol, dolaşım yeteneğine sahip olan mağazaları açmak için kullanılamaz; Bu <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> gibi durumlarda kullanın.  
  
 [!code-cpp[Conceptual.IsolatedStorage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#18)]
 [!code-csharp[Conceptual.IsolatedStorage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#18)]
 [!code-vb[Conceptual.IsolatedStorage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#18)]  
  
<a name="UserDomainAssembly"></a>   
## <a name="isolation-by-user-domain-and-assembly"></a>Kullanıcı, Etki Alanı ve Derlemeye Göre Yalıtım  
 Uygulamanız özel veri deposu gerektiren bir üçüncü taraf derleme kullanıyorsa, özel verileri depolamak için yalıtılmış depolamayı kullanabilirsiniz. Kullanıcı, etki alanı ve derlemeye göre yalıtım, yalnızca belirli bir derlemedeki kodun verilere erişebilmesini ve yalnızca derlemenin depoyu oluştururken çalışan uygulama tarafından kullanıldığı ve yalnızca deponun oluşturulduğu Kullanıcı tarafından çalıştırıldığı zaman  Uygulamanızı. Kullanıcı, etki alanı ve derlemeye göre yalıtım, üçüncü taraf derlemenin diğer uygulamalara veri sızmasını önler. Yalıtılmış depolama kullanmak istediğinizi bildiğiniz ancak hangi tür yalıtımın kullanılacağı konusunda emin değilseniz, bu yalıtım türü varsayılan seçiminiz olmalıdır. Statik <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> <xref:System.IO.IsolatedStorage.IsolatedStorageScope> yöntemini çağırmak ve bir Kullanıcı, etki alanı ve derlemeye geçirmek bu tür yalıtımına sahip depolama döndürür. <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
  
 Aşağıdaki kod örneği, Kullanıcı, etki alanı ve derleme tarafından yalıtılmış bir depoyu alır. Depoya `isoFile` nesne üzerinden erişilebilir.  
  
 [!code-cpp[Conceptual.IsolatedStorage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#14)]
 [!code-csharp[Conceptual.IsolatedStorage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#14)]
 [!code-vb[Conceptual.IsolatedStorage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#14)]  
  
 Aşağıdaki kod örneğinde gösterildiği gibi başka bir yöntem kısayol olarak kullanılabilir. Bu kısayol, dolaşım yeteneğine sahip olan mağazaları açmak için kullanılamaz; Bu <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> gibi durumlarda kullanın.  
  
 [!code-cpp[Conceptual.IsolatedStorage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#15)]
 [!code-csharp[Conceptual.IsolatedStorage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#15)]
 [!code-vb[Conceptual.IsolatedStorage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#15)]  
  
<a name="Roaming"></a>   
## <a name="isolated-storage-and-roaming"></a>Ayrık Depolama ve Dolaşım  
 Gezici Kullanıcı profilleri, bir kullanıcının ağ üzerinde bir kimlik ayarlaması ve bu kimliği herhangi bir ağ bilgisayarında oturum açmak için, tüm kişiselleştirilmiş ayarları yerine getiren bir Windows özelliğidir. Yalıtılmış depolama kullanan bir derleme, kullanıcının yalıtılmış depolamanın gezici kullanıcı profili ile hareket etmesi gerektiğini belirtebilir. Dolaşım, Kullanıcı ve derlemeye göre yalıtım ile veya Kullanıcı, etki alanı ve derlemeye göre yalıtımla birlikte kullanılabilir. Dolaşım kapsamı kullanılmazsa, bir dolaşım Kullanıcı profili kullanılsa bile depolar dolaşımda olmaz.  
  
 Aşağıdaki kod örneği, Kullanıcı ve derleme tarafından yalıtılmış bir dolaşım deposu alır. Depoya `isoFile` nesne üzerinden erişilebilir.  
  
 [!code-cpp[Conceptual.IsolatedStorage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#11)]
 [!code-csharp[Conceptual.IsolatedStorage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#11)]
 [!code-vb[Conceptual.IsolatedStorage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#11)]  
  
 Kullanıcı, etki alanı ve uygulama tarafından yalıtılmış bir dolaşım deposu oluşturmak için bir etki alanı kapsamı eklenebilir. Aşağıdaki kod örneği bunu gösterir.  
  
 [!code-cpp[Conceptual.IsolatedStorage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#12)]
 [!code-csharp[Conceptual.IsolatedStorage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#12)]
 [!code-vb[Conceptual.IsolatedStorage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#12)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.IsolatedStorage.IsolatedStorageScope>
- [Yalıtılmış Depolama](../../../docs/standard/io/isolated-storage.md)
