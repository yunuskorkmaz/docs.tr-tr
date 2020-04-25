---
title: 'Nasıl yapılır: MetadataLoadContext kullanarak bütünleştirilmiş kod içeriklerini Inceleme'
description: .NET derlemelerini inceleme amacıyla yüklemeyi sağlayan bir API olan MetadataLoadContext ' i nasıl kullanacağınızı öğrenin.
author: MSDN-WhiteKnight
ms.date: 03/10/2020
ms.technology: dotnet-standard
ms.openlocfilehash: 90c84147c52199afc42a2efc297bc7fe40658ec7
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141195"
---
# <a name="how-to-inspect-assembly-contents-using-metadataloadcontext"></a>Nasıl yapılır: MetadataLoadContext kullanarak bütünleştirilmiş kod içeriklerini Inceleme

.NET ' teki yansıma API 'SI varsayılan olarak, geliştiricilerin ana yürütme bağlamına yüklenen derlemelerin içeriğini incelemesine olanak sağlar. Ancak, bazen bir derlemeyi yürütme bağlamına yüklemek mümkün değildir, örneğin başka bir platform veya işlemci mimarisi için derlenmişse veya bir [başvuru bütünleştirilmiş kodu](reference-assemblies.md). API <xref:System.Reflection.MetadataLoadContext?displayProperty=fullName> , bu derlemeleri yüklemenize ve incelemenize olanak sağlar. İçine <xref:System.Reflection.MetadataLoadContext> yüklenen derlemeler yalnızca meta veri olarak değerlendirilir, diğer bir deyişle, derlemedeki türleri inceleyebilirsiniz, ancak içinde yer alan herhangi bir kodu çalıştıramazsınız. Ana yürütme bağlamından farklı olarak, <xref:System.Reflection.MetadataLoadContext> otomatik olarak geçerli dizinden bağımlılıkları yüklemez; Bunun yerine, <xref:System.Reflection.MetadataAssemblyResolver> geçirilen tarafından verilen özel bağlama mantığını kullanır.

## <a name="prerequisites"></a>Ön koşullar

Kullanmak <xref:System.Reflection.MetadataLoadContext>için [System. Reflection. MetadataLoadContext](https://www.nuget.org/packages/System.Reflection.MetadataLoadContext) NuGet paketini yükler. .NET Standard 2,0 uyumlu hedef çerçevede desteklenir, örneğin .NET Core 2,0 veya .NET Framework 4.6.1.

## <a name="create-metadataassemblyresolver-for-metadataloadcontext"></a>MetadataLoadContext için MetadataAssemblyResolver oluştur

Oluşturmak için <xref:System.Reflection.MetadataLoadContext> öğesinin örneğini sağlaması gerekir <xref:System.Reflection.MetadataAssemblyResolver>. Bir tane sağlamanın en basit yolu, derleme yolu dizelerinin <xref:System.Reflection.PathAssemblyResolver>verilen koleksiyonundan derlemeleri çözümleyen öğesini kullanmaktır. Bu koleksiyon, doğrudan incelemek istediğiniz derlemelerin yanı sıra tüm gerekli bağımlılıkları da içermelidir. Örneğin, bir dış derlemede bulunan özel özniteliği okumak için, söz konusu derlemeyi veya bir özel durumu içermelidir. Çoğu durumda, en azından *çekirdek derleme*, diğer bir deyişle, gibi yerleşik sistem türlerini içeren derleme dahil etmelisiniz <xref:System.Object?displayProperty=nameWithType>. Aşağıdaki kod, incelenen derlemeden ve geçerli çalışma <xref:System.Reflection.PathAssemblyResolver> zamanının temel bütünleştirilmiş kodundan oluşan koleksiyonu kullanarak nasıl oluşturulacağını gösterir:

[!code-csharp[](snippets/inspect-contents-using-metadataloadcontext/MetadataLoadContextSnippets.cs#CoreAssembly)]

Tüm BCL türlerine erişmeniz gerekiyorsa, tüm çalışma zamanı derlemelerini koleksiyona ekleyebilirsiniz. Aşağıdaki kod, incelenen derlemeden ve geçerli çalışma <xref:System.Reflection.PathAssemblyResolver> zamanının tüm derlemelerinden oluşan koleksiyon kullanılarak nasıl oluşturulacağını gösterir:

[!code-csharp[](snippets/inspect-contents-using-metadataloadcontext/MetadataLoadContextSnippets.cs#RuntimeAssemblies)]

## <a name="create-metadataloadcontext"></a>MetadataLoadContext oluştur

Oluşturmak <xref:System.Reflection.MetadataLoadContext>için, oluşturucuyu <xref:System.Reflection.MetadataLoadContext.%23ctor%28System.Reflection.MetadataAssemblyResolver%2CSystem.String%29>çağırın, daha önce ilk parametresi olarak oluşturulan <xref:System.Reflection.MetadataAssemblyResolver> öğesini ve ikinci parametre olarak çekirdek derleme adını geçirerek. Çekirdek derleme adını atlayabilirsiniz, bu durumda oluşturucunun varsayılan adları kullanmayı deneyeceği "mscorlib", "System. Runtime" veya "Netstandard" olması gerekir.

Bağlamı oluşturduktan sonra, gibi yöntemleri kullanarak bu derlemeye Derlemeler yükleyebilirsiniz <xref:System.Reflection.MetadataLoadContext.LoadFromAssemblyPath%2A>. Kod yürütmeyi kapsayan olanlar hariç, yüklenen derlemelerde tüm yansıma API 'Lerini kullanabilirsiniz. <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A> Yöntemi oluşturucuların yürütülmesini içerir, bu nedenle içindeki özel öznitelikleri incelemeniz gerektiğinde <xref:System.Reflection.MemberInfo.GetCustomAttributesData%2A> bunun yerine yöntemini kullanın <xref:System.Reflection.MetadataLoadContext>.

Aşağıdaki kod örneği oluşturur <xref:System.Reflection.MetadataLoadContext>, derlemeyi buna yükler ve derleme özniteliklerini konsola verir:

[!code-csharp[](snippets/inspect-contents-using-metadataloadcontext/MetadataLoadContextSnippets.cs#CreateContext)]

## <a name="example"></a>Örnek

Kod örneği için bkz. [MetadataLoadContext örneği kullanılarak derleme Içeriğini İnceleme](https://docs.microsoft.com/samples/dotnet/samples/inspect-assembly-contents-using-metadataloadcontext/).
