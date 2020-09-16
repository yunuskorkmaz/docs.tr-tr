---
title: 'Nasıl yapılır: MetadataLoadContext kullanarak bütünleştirilmiş kod içeriklerini Inceleme'
description: .NET derlemelerini inceleme amacıyla yüklemeyi sağlayan bir API olan MetadataLoadContext ' i nasıl kullanacağınızı öğrenin.
author: MSDN-WhiteKnight
ms.date: 03/10/2020
ms.technology: dotnet-standard
ms.openlocfilehash: 7f90149a98632ea57e8d241a0ccdf4b50264ac5c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90552030"
---
# <a name="how-to-inspect-assembly-contents-using-metadataloadcontext"></a>Nasıl yapılır: MetadataLoadContext kullanarak bütünleştirilmiş kod içeriklerini Inceleme

.NET ' teki yansıma API 'SI varsayılan olarak, geliştiricilerin ana yürütme bağlamına yüklenen derlemelerin içeriğini incelemesine olanak sağlar. Ancak, bazen bir derlemeyi yürütme bağlamına yüklemek mümkün değildir, örneğin başka bir platform veya işlemci mimarisi için derlenmişse veya bir [başvuru bütünleştirilmiş kodu](reference-assemblies.md). <xref:System.Reflection.MetadataLoadContext?displayProperty=fullName>API, bu derlemeleri yüklemenize ve incelemenize olanak sağlar. İçine yüklenen derlemeler <xref:System.Reflection.MetadataLoadContext> yalnızca meta veri olarak değerlendirilir, diğer bir deyişle, derlemedeki türleri inceleyebilirsiniz, ancak içinde yer alan herhangi bir kodu çalıştıramazsınız. Ana yürütme bağlamından farklı olarak, <xref:System.Reflection.MetadataLoadContext> otomatik olarak geçerli dizinden bağımlılıkları yüklemez; bunun yerine, geçirilen tarafından verilen özel bağlama mantığını kullanır <xref:System.Reflection.MetadataAssemblyResolver> .

## <a name="prerequisites"></a>Önkoşullar

Kullanmak için <xref:System.Reflection.MetadataLoadContext> [System. Reflection. MetadataLoadContext](https://www.nuget.org/packages/System.Reflection.MetadataLoadContext) NuGet paketini yükler. .NET Standard 2,0 uyumlu hedef çerçevede desteklenir, örneğin .NET Core 2,0 veya .NET Framework 4.6.1.

## <a name="create-metadataassemblyresolver-for-metadataloadcontext"></a>MetadataLoadContext için MetadataAssemblyResolver oluştur

Oluşturmak için <xref:System.Reflection.MetadataLoadContext> öğesinin örneğini sağlaması gerekir <xref:System.Reflection.MetadataAssemblyResolver> . Bir tane sağlamanın en basit yolu, <xref:System.Reflection.PathAssemblyResolver> derleme yolu dizelerinin verilen koleksiyonundan derlemeleri çözümleyen öğesini kullanmaktır. Bu koleksiyon, doğrudan incelemek istediğiniz derlemelerin yanı sıra tüm gerekli bağımlılıkları da içermelidir. Örneğin, bir dış derlemede bulunan özel özniteliği okumak için, söz konusu derlemeyi veya bir özel durumu içermelidir. Çoğu durumda, en azından *çekirdek derleme*, diğer bir deyişle, gibi yerleşik sistem türlerini içeren derleme dahil etmelisiniz <xref:System.Object?displayProperty=nameWithType> . Aşağıdaki kod, <xref:System.Reflection.PathAssemblyResolver> incelenen derlemeden ve geçerli çalışma zamanının temel bütünleştirilmiş kodundan oluşan koleksiyonu kullanarak nasıl oluşturulacağını gösterir:

[!code-csharp[](snippets/inspect-contents-using-metadataloadcontext/MetadataLoadContextSnippets.cs#CoreAssembly)]

Tüm BCL türlerine erişmeniz gerekiyorsa, tüm çalışma zamanı derlemelerini koleksiyona ekleyebilirsiniz. Aşağıdaki kod, <xref:System.Reflection.PathAssemblyResolver> incelenen derlemeden ve geçerli çalışma zamanının tüm derlemelerinden oluşan koleksiyon kullanılarak nasıl oluşturulacağını gösterir:

[!code-csharp[](snippets/inspect-contents-using-metadataloadcontext/MetadataLoadContextSnippets.cs#RuntimeAssemblies)]

## <a name="create-metadataloadcontext"></a>MetadataLoadContext oluştur

Oluşturmak için, <xref:System.Reflection.MetadataLoadContext> oluşturucuyu çağırın <xref:System.Reflection.MetadataLoadContext.%23ctor%28System.Reflection.MetadataAssemblyResolver%2CSystem.String%29> , daha önce <xref:System.Reflection.MetadataAssemblyResolver> ilk parametresi olarak oluşturulan öğesini ve ikinci parametre olarak çekirdek derleme adını geçirerek. Çekirdek derleme adını atlayabilirsiniz, bu durumda oluşturucunun varsayılan adları kullanmayı deneyeceği "mscorlib", "System. Runtime" veya "Netstandard" olması gerekir.

Bağlamı oluşturduktan sonra, gibi yöntemleri kullanarak bu derlemeye Derlemeler yükleyebilirsiniz <xref:System.Reflection.MetadataLoadContext.LoadFromAssemblyPath%2A> . Kod yürütmeyi kapsayan olanlar hariç, yüklenen derlemelerde tüm yansıma API 'Lerini kullanabilirsiniz. <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A>Yöntemi oluşturucuların yürütülmesini içerir, bu nedenle <xref:System.Reflection.MemberInfo.GetCustomAttributesData%2A> içindeki özel öznitelikleri incelemeniz gerektiğinde bunun yerine yöntemini kullanın <xref:System.Reflection.MetadataLoadContext> .

Aşağıdaki kod örneği oluşturur <xref:System.Reflection.MetadataLoadContext> , derlemeyi buna yükler ve derleme özniteliklerini konsola verir:

[!code-csharp[](snippets/inspect-contents-using-metadataloadcontext/MetadataLoadContextSnippets.cs#CreateContext)]

## <a name="example"></a>Örnek

Kod örneği için bkz. [MetadataLoadContext örneği kullanılarak derleme Içeriğini İnceleme](/samples/dotnet/samples/inspect-assembly-contents-using-metadataloadcontext/).
