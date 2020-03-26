---
title: 'Nasıl yapilir: MetadataLoadContext kullanarak montaj içeriğini inceleyin'
description: .NET derlemelerini denetim amacıyla yüklemenize olanak tanıyan bir API olan MetadataLoadContext'ı nasıl kullanacağınızı öğrenin.
author: MSDN-WhiteKnight
ms.date: 03/10/2020
ms.technology: dotnet-standard
ms.openlocfilehash: a782b2db4fb62cfaedaa6768e2131bda6bec864c
ms.sourcegitcommit: b75a45f0cfe012b71b45dd9bf723adf32369d40c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80229303"
---
# <a name="how-to-inspect-assembly-contents-using-metadataloadcontext"></a>Nasıl yapilir: MetadataLoadContext kullanarak montaj içeriğini inceleyin

.NET'teki yansıma API'si varsayılan olarak geliştiricilerin ana yürütme bağlamına yüklenen derlemelerin içeriğini denetlemesine olanak tanır. Ancak, bazen bir derlemeyi yürütme bağlamına yüklemek mümkün değildir, örneğin, başka bir platform veya işlemci mimarisi için derlenmiş olduğundan veya bir [başvuru derlemesi](reference-assemblies.md)olduğundan. API, <xref:System.Reflection.MetadataLoadContext?displayProperty=fullName> bu tür derlemeleri yüklemenize ve incelemenize olanak tanır. Yüklenen <xref:System.Reflection.MetadataLoadContext> derlemeler yalnızca meta veri olarak kabul edilir, diğer bir deyişle, derlemedeki türleri inceleyebilirsiniz, ancak içinde bulunan herhangi bir kodu yürütemezsiniz. Ana yürütme bağlamından <xref:System.Reflection.MetadataLoadContext> farklı olarak, geçerli dizinden otomatik olarak bağımlılıklar yüklenmez; bunun <xref:System.Reflection.MetadataAssemblyResolver> yerine, ona geçen tarafından sağlanan özel bağlama mantığını kullanır.

## <a name="prerequisites"></a>Ön koşullar

Kullanmak <xref:System.Reflection.MetadataLoadContext>için [System.Reflection.MetadataLoadContext](https://www.nuget.org/packages/System.Reflection.MetadataLoadContext) NuGet paketini yükleyin. .NET Standard 2.0 uyumlu hedef çerçevede desteklenir, örneğin,.NET Core 2.0 veya .NET Framework 4.6.1.

## <a name="create-metadataassemblyresolver-for-metadataloadcontext"></a>MetadataLoadContext için MetadataAssemblyResolver oluşturma

<xref:System.Reflection.MetadataLoadContext> Oluşturma, <xref:System.Reflection.MetadataAssemblyResolver>'nin örneğini sağlamayı gerektirir. Bir sağlamak için en basit <xref:System.Reflection.PathAssemblyResolver>yolu, montajları montajları verilen toplama derlemesini çözer kullanmaktır. Bu koleksiyon, doğrudan incelemek istediğiniz derlemelerin yanı sıra, gerekli tüm bağımlılıkları da içermelidir. Örneğin, harici bir derlemede bulunan özel özniteliği okumak için, bu derlemeyi eklemeniz gerekir veya bir özel durum atılır. Çoğu durumda, en azından *çekirdek derlemeyi*, yani yerleşik sistem türlerini içeren <xref:System.Object?displayProperty=nameWithType>derlemeyi içermelisiniz. Aşağıdaki kod, denetlenen <xref:System.Reflection.PathAssemblyResolver> derleme ve geçerli çalışma zamanının çekirdek derlemesi oluşan toplama nın nasıl oluşturulacak olduğunu gösterir:

[!code-csharp[](snippets/inspect-contents-using-metadataloadcontext/MetadataLoadContextSnippets.cs#CoreAssembly)]

Tüm BCL türlerine erişmeniz gerekiyorsa, koleksiyona tüm çalışma zamanı derlemelerini ekleyebilirsiniz. Aşağıdaki kod, denetlenen <xref:System.Reflection.PathAssemblyResolver> derlemeve geçerli çalışma zamanının tüm derlemelerinden oluşan koleksiyonun nasıl oluşturulturun nasıl oluşturulacak larını gösterir:

[!code-csharp[](snippets/inspect-contents-using-metadataloadcontext/MetadataLoadContextSnippets.cs#RuntimeAssemblies)]

## <a name="create-metadataloadcontext"></a>MetadataLoadContext oluşturma

Oluşturmak <xref:System.Reflection.MetadataLoadContext>için, daha önce <xref:System.Reflection.MetadataLoadContext.%23ctor%28System.Reflection.MetadataAssemblyResolver%2CSystem.String%29>ilk parametre <xref:System.Reflection.MetadataAssemblyResolver> olarak oluşturulan ve ikinci parametre olarak çekirdek derleme adı geçen, onun oluşturucu çağırmak. Çekirdek derleme adını atlayabilirsiniz, bu durumda oluşturucu varsayılan adları kullanmaya çalışır: "mscorlib", "System.Runtime" veya "netstandard".

Bağlamı oluşturduktan sonra, <xref:System.Reflection.MetadataLoadContext.LoadFromAssemblyPath%2A>derlemeleri '. Kod yürütme içerenler dışında yüklü derlemelerde tüm yansıma API'lerini kullanabilirsiniz. Yöntem <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A> yapıcıların yürütülmesini içerir, bu nedenle <xref:System.Reflection.MemberInfo.GetCustomAttributesData%2A> özel öznitelikleri incelemek için gerektiğinde <xref:System.Reflection.MetadataLoadContext>yerine yöntemi kullanın.

Aşağıdaki kod örneği <xref:System.Reflection.MetadataLoadContext>oluşturur, montaj yükler ve konsola montaj öznitelikleri çıkar:

[!code-csharp[](snippets/inspect-contents-using-metadataloadcontext/MetadataLoadContextSnippets.cs#CreateContext)]

## <a name="example"></a>Örnek

Tam bir kod örneği için [bkz.](https://docs.microsoft.com/samples/dotnet/samples/inspect-assembly-contents-using-metadataloadcontext/)
