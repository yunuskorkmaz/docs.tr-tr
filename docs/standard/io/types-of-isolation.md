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
ms.openlocfilehash: d85625b99603c0bd81346cf2076b8efe0e1bba42
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523881"
---
# <a name="types-of-isolation"></a>Yalıtım Türleri
Yalıtılmış depolama ya da depolama ya da depolama alanı nın erişimini oluşturan kullanıcıyla her zaman sınırlandırılmıştır. Bu tür yalıtımuygulamak için, ortak dil çalışma süresi, işletim sisteminin tanıdığı kullanıcı kimliği kavramını kullanır, bu da depo açıldığında kodun çalıştığı işlemle ilişkili kimliktir. Bu kimlik kimlik doğrulaması kullanıcı kimliğidir, ancak kimliğe bürünme geçerli kullanıcının kimliğinin dinamik olarak değişmesine neden olabilir.  
  
 Yalıtılmış depolamaya erişim, uygulamanın etki alanı ve derlemesiyle ilişkili kimliğe göre veya yalnızca derlemeyle de sınırlıdır. Çalışma zamanı bu kimlikleri aşağıdaki yollarla elde eder:  
  
- Etki alanı kimliği, bir web uygulaması durumunda tam URL olabilir uygulama, kanıt temsil eder. Kabuk barındırılan kod için etki alanı kimliği uygulama dizini yolunu temel alabilir. Örneğin, çalıştırılabilir olan c:\Office\MyApp.exe yolundan çalışıyorsa, etki alanı kimliği C:\Office\MyApp.exe olacaktır.  
  
- Montaj kimliği, derlemenin kanıtıdır. Bu, derlemenin [güçlü adı](../assembly/strong-named.md), derlemenin yazılım yayımcısı veya URL kimliği olabilecek bir şifreleme dijital imzadan gelebilir. Bir derlemenin hem güçlü bir adı hem de yazılım yayımcısı kimliği varsa, yazılım yayımcısı kimliği kullanılır. Derleme Internet'ten geliyorsa ve imzalanmamışsa, URL kimliği kullanılır. Derlemeler ve güçlü adlar hakkında daha fazla bilgi için [Derlemelerle Programlama'ya](/dotnet/standard/assembly/index)bakın.  
  
- Dolaşım mağazaları, dolaşım kullanıcısı profili olan bir kullanıcıyla hareket ettirin. Dosyalar bir ağ dizinine yazılır ve kullanıcının oturum açtırolduğu herhangi bir bilgisayara indirilir. Dolaşım kullanıcı profilleri hakkında daha fazla <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Roaming?displayProperty=nameWithType>bilgi için bkz.  
  
 Kullanıcı, etki alanı ve derleme kimliği kavramlarını birleştirerek, yalıtılmış depolama verileri aşağıdaki şekillerde yalıtabilir ve bunların her birinin kendi kullanım senaryoları vardır:  
  
- [Kullanıcı ve montaj tarafından yalıtım](#UserAssembly)  
  
- [Kullanıcıya, etki alanına ve derlemeye göre yalıtım](#UserDomainAssembly)  
  
 Bu yalıtımlardan biri dolaşımdaki kullanıcı profiliyle birleştirilebilir. Daha fazla bilgi [için, Yalıtılmış Depolama ve Dolaşım](#Roaming)bölümüne bakın.  
  
 Aşağıdaki resimde, mağazaların farklı kapsamlarda nasıl yalıtılmış olduğu gösterilmiştir:  
  
 ![Kullanıcı ve derlemeye göre yalıtımı gösteren diyagram.](./media/types-of-isolation/isolated-storage-types.gif)  
  
 Dolaşım depoları dışında, yalıtılmış depolamanın, belirli bir bilgisayara yerel olan depolama olanaklarını kullandığından, bilgisayar tarafından her zaman dolaylı olarak yalıtılmış olduğunu unutmayın.  
  
> [!IMPORTANT]
> Windows 8.x Store uygulamaları için yalıtılmış depolama alanı kullanılamaz. Bunun yerine, yerel verileri `Windows.Storage` ve dosyaları depolamak için Windows Runtime API'sında yer alan ad alanlarında uygulama veri sınıflarını kullanın. Daha fazla bilgi için Windows Geliştirme Merkezi'ndeki [Uygulama verilerine](https://docs.microsoft.com/previous-versions/windows/apps/hh464917(v=win.10)) bakın.  
  
<a name="UserAssembly"></a>
## <a name="isolation-by-user-and-assembly"></a>Kullanıcı ve Derlemeye Göre Yalıtım  
 Veri deposunu kullanan derlemenin herhangi bir uygulamanın etki alanından erişilebilir olması gerektiğinde, kullanıcı ve derleme tarafından yalıtım uygundur. Genellikle, bu durumda, yalıtılmış depolama, birden çok uygulama arasında geçerli olan ve kullanıcının adı veya lisans bilgileri gibi belirli bir uygulamaya bağlı olmayan verileri depolamak için kullanılır. Kullanıcı ve derleme tarafından yalıtılmış depolamaya erişmek için, uygulamalar arasında bilgi aktarmak için koda güvenilmelidir. Genellikle, kullanıcı ve derleme tarafından yalıtım ait intranetler üzerinde izin verilir, ancak Internet üzerinde değil. Statik <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A?displayProperty=nameWithType> yöntemi çağırmak ve bir kullanıcı <xref:System.IO.IsolatedStorage.IsolatedStorageScope> ve bir derleme geçen bu tür yalıtım ile depolama döndürür.  
  
 Aşağıdaki kod örneği, kullanıcı ve derleme tarafından yalıtılmış bir depo alır. Mağazaya `isoFile` nesne üzerinden erişilebilir.  
  
 [!code-cpp[Conceptual.IsolatedStorage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#17)]
 [!code-csharp[Conceptual.IsolatedStorage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#17)]
 [!code-vb[Conceptual.IsolatedStorage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#17)]  
  
 Kanıt parametrelerini kullanan bir <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%28System.IO.IsolatedStorage.IsolatedStorageScope%2CSystem.Security.Policy.Evidence%2CSystem.Type%2CSystem.Security.Policy.Evidence%2CSystem.Type%29>örnek için bkz.  
  
 Yöntem, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> aşağıdaki kod örneğinde gösterildiği gibi kısayol olarak kullanılabilir. Bu kısayol, dolaşım alabilen mağazaları açmak için kullanılamaz; bu <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> gibi durumlarda kullanın.  
  
 [!code-cpp[Conceptual.IsolatedStorage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#18)]
 [!code-csharp[Conceptual.IsolatedStorage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#18)]
 [!code-vb[Conceptual.IsolatedStorage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#18)]  
  
<a name="UserDomainAssembly"></a>
## <a name="isolation-by-user-domain-and-assembly"></a>Kullanıcı, Etki Alanı ve Derlemeye Göre Yalıtım  
 Uygulamanız özel bir veri deposu gerektiren bir üçüncü taraf derleme kullanıyorsa, özel verileri depolamak için yalıtılmış depolamayı kullanabilirsiniz. Kullanıcı, etki alanı ve derleme tarafından yalıtım, yalnızca belirli bir derlemedeki kodun verilere erişebilmesini ve yalnızca derleme mağazayı oluşturduğunda çalışan uygulama tarafından kullanıldığında ve yalnızca mağazanın oluşturulduğu kullanıcı uygulamayı çalıştırdığında olmasını sağlar. Kullanıcı, etki alanı ve derleme tarafından yalıtım, üçüncü taraf derlemesinin diğer uygulamalara veri sızdırmasını sağlar. İzole depolama alanı kullanmak istediğinizi ancak hangi yalıtım türünü kullanacağınızdan emin değilseniz, bu yalıtım türü varsayılan tercihiniz olmalıdır. Statik <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> yöntemi çağırmak <xref:System.IO.IsolatedStorage.IsolatedStorageFile> ve bir kullanıcı, etki <xref:System.IO.IsolatedStorage.IsolatedStorageScope> alanı ve derleme de geçen bu tür yalıtım ile depolama döndürür.  
  
 Aşağıdaki kod örneği, kullanıcı, etki alanı ve derleme tarafından yalıtılmış bir depo alır. Mağazaya `isoFile` nesne üzerinden erişilebilir.  
  
 [!code-cpp[Conceptual.IsolatedStorage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#14)]
 [!code-csharp[Conceptual.IsolatedStorage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#14)]
 [!code-vb[Conceptual.IsolatedStorage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#14)]  
  
 Aşağıdaki kod örneğinde gösterildiği gibi, başka bir yöntem kısayol olarak kullanılabilir. Bu kısayol, dolaşım alabilen mağazaları açmak için kullanılamaz; bu <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> gibi durumlarda kullanın.  
  
 [!code-cpp[Conceptual.IsolatedStorage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#15)]
 [!code-csharp[Conceptual.IsolatedStorage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#15)]
 [!code-vb[Conceptual.IsolatedStorage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#15)]  
  
<a name="Roaming"></a>
## <a name="isolated-storage-and-roaming"></a>Ayrık Depolama ve Dolaşım  
 Dolaşım kullanıcı profilleri, kullanıcının ağüzerinde bir kimlik ayarlamasına ve bu kimliği kullanarak tüm kişiselleştirilmiş ayarları taşıyarak herhangi bir ağ bilgisayarında oturum açmasını sağlayan bir Windows özelliğidir. Yalıtılmış depolama kullanan bir derleme, kullanıcının yalıtılmış depolama alanının dolaşımdaki kullanıcı profiliyle birlikte taşınması gerektiğini belirtebilir. Dolaşım, kullanıcı ve montaj tarafından yalıtımla birlikte veya kullanıcı, etki alanı ve montaj tarafından yalıtımla birlikte kullanılabilir. Dolaşım kapsamı kullanılmazsa, dolaşım kullanıcı profili kullanılsa bile mağazalar dolaşmaz.  
  
 Aşağıdaki kod örneği, kullanıcı ve derleme tarafından yalıtılmış bir dolaşım deposu alır. Mağazaya `isoFile` nesne üzerinden erişilebilir.  
  
 [!code-cpp[Conceptual.IsolatedStorage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#11)]
 [!code-csharp[Conceptual.IsolatedStorage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#11)]
 [!code-vb[Conceptual.IsolatedStorage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#11)]  
  
 Kullanıcı, etki alanı ve uygulama tarafından yalıtılmış bir dolaşım mağazası oluşturmak için etki alanı kapsamı eklenebilir. Aşağıdaki kod örneği bunu göstermektedir.  
  
 [!code-cpp[Conceptual.IsolatedStorage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#12)]
 [!code-csharp[Conceptual.IsolatedStorage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#12)]
 [!code-vb[Conceptual.IsolatedStorage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#12)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.IsolatedStorage.IsolatedStorageScope>
- [Yalıtılmış Depolama](../../../docs/standard/io/isolated-storage.md)
