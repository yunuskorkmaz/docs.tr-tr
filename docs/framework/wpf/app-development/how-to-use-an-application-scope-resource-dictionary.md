---
title: 'Nasıl yapılır: Uygulama Kapsamı Kaynak Sözlüğü Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dictionaries [WPF], resource
- resource dictionaries [WPF], application-scope
- application-scope resource dictionaries
ms.assetid: 53857682-bd2c-4f2c-8f25-1307d0b451a2
ms.openlocfilehash: 5bfb3ed0304598a5acf4b7682bf4a4169c5153d1
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459801"
---
# <a name="how-to-use-an-application-scope-resource-dictionary"></a><span data-ttu-id="61f84-102">Nasıl yapılır: Uygulama Kapsamı Kaynak Sözlüğü Kullanma</span><span class="sxs-lookup"><span data-stu-id="61f84-102">How to: Use an Application-Scope Resource Dictionary</span></span>
<span data-ttu-id="61f84-103">Bu örnek, uygulama kapsamı özel kaynak sözlüğünün nasıl tanımlanacağını ve kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="61f84-103">This example shows how to define and use an application-scope custom resource dictionary.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61f84-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="61f84-104">Example</span></span>  
 <span data-ttu-id="61f84-105"><xref:System.Windows.Application>, paylaşılan kaynaklar için uygulama kapsamı deposunu kullanıma sunar: <xref:System.Windows.Application.Resources%2A>.</span><span class="sxs-lookup"><span data-stu-id="61f84-105"><xref:System.Windows.Application> exposes an application-scope store for shared resources: <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="61f84-106">Varsayılan olarak, <xref:System.Windows.Application.Resources%2A> özelliği <xref:System.Windows.ResourceDictionary> türünün bir örneğiyle başlatılır.</span><span class="sxs-lookup"><span data-stu-id="61f84-106">By default, the <xref:System.Windows.Application.Resources%2A> property is initialized with an instance of the <xref:System.Windows.ResourceDictionary> type.</span></span> <span data-ttu-id="61f84-107"><xref:System.Windows.Application.Resources%2A>kullanarak uygulama kapsamı özelliklerini alırken ve ayarladığınızda bu örneği kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="61f84-107">You use this instance when you get and set application-scope properties using <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="61f84-108">Daha fazla bilgi için bkz. [nasıl yapılır: uygulama kapsamı kaynağı alma ve ayarlama](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348547(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="61f84-108">For more information, see [How to: Get and Set an Application-Scope Resource](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348547(v=vs.100)).</span></span>
  
 <span data-ttu-id="61f84-109"><xref:System.Windows.Application.Resources%2A>kullanarak ayarladığınız birden fazla kaynağınız varsa, bunun yerine bu kaynakları depolamak için özel bir kaynak sözlüğü kullanabilir ve bunun yerine onunla <xref:System.Windows.Application.Resources%2A> ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="61f84-109">If you have multiple resources that you set using <xref:System.Windows.Application.Resources%2A>, you can instead use a custom resource dictionary to store those resources and set <xref:System.Windows.Application.Resources%2A> with it instead.</span></span> <span data-ttu-id="61f84-110">Aşağıda, XAML kullanarak özel bir kaynak sözlüğünün nasıl bildirildiği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="61f84-110">The following shows how you declare a custom resource dictionary using XAML.</span></span>
  
 [!code-xaml[HOWTOResourceDictionaries#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MyResourceDictionary.xaml#1)]  
  
 <span data-ttu-id="61f84-111"><xref:System.Windows.Application.Resources%2A> kullanarak tüm kaynak sözlüklerinin takas işlemi, her temanın tek bir kaynak sözlüğü tarafından kapsüllendiği uygulama kapsamı temalarını desteketmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="61f84-111">Swapping entire resource dictionaries using <xref:System.Windows.Application.Resources%2A> allows you to support application-scope themes, where each theme is encapsulated by a single resource dictionary.</span></span> <span data-ttu-id="61f84-112">Aşağıdaki örnekte <xref:System.Windows.ResourceDictionary>nasıl ayarlanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="61f84-112">The following example shows how to set the <xref:System.Windows.ResourceDictionary>.</span></span>  
  
 [!code-xaml[HOWTOResourceDictionaries#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/App.xaml#2)]  
  
 <span data-ttu-id="61f84-113">Aşağıda, XAML 'de <xref:System.Windows.Application.Resources%2A> tarafından sunulan kaynak sözlüğünden uygulama kapsamı kaynaklarını nasıl alabileceğiniz gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="61f84-113">The following shows how you can get application-scope resources from the resource dictionary exposed by <xref:System.Windows.Application.Resources%2A> in XAML.</span></span>  
  
 [!code-xaml[HOWTOResourceDictionaries#4](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml#4)]  
  
 <span data-ttu-id="61f84-114">Ayrıca, koddaki kaynakların nasıl alınacağını aşağıda görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="61f84-114">The following shows how you can also get the resources in code.</span></span>  
  
 [!code-csharp[HOWTOResourceDictionaries#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml.cs#3)]
 [!code-vb[HOWTOResourceDictionaries#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToResourceDictionaries/VB/MainWindow.xaml.vb#3)]  
  
 <span data-ttu-id="61f84-115"><xref:System.Windows.Application.Resources%2A>kullanırken yapmanız gereken iki önemli noktalar vardır.</span><span class="sxs-lookup"><span data-stu-id="61f84-115">There are two considerations to make when using <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="61f84-116">İlk olarak, sözlük *anahtarı* bir nesnedir, bu nedenle her ikisi de bir özellik değeri ayarlarken ve alırken tam olarak aynı nesne örneğini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="61f84-116">First, the dictionary *key* is an object, so you must use exactly the same object instance when both setting and getting a property value.</span></span> <span data-ttu-id="61f84-117">(Bir dize kullanılırken anahtarın büyük/küçük harfe duyarlı olduğunu unutmayın.) İkincisi, sözlük *değeri* bir nesnedir, bu nedenle bir özellik değeri alırken değeri istenen türe dönüştürmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="61f84-117">(Note that the key is case-sensitive when using a string.) Second, the dictionary *value* is an object, so you will have to convert the value to the desired type when getting a property value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61f84-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="61f84-118">See also</span></span>

- <xref:System.Windows.ResourceDictionary>
- <xref:System.Windows.Application.Resources%2A>
- [<span data-ttu-id="61f84-119">XAML Kaynakları</span><span class="sxs-lookup"><span data-stu-id="61f84-119">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="61f84-120">Birleştirilmiş Kaynak Sözlükleri</span><span class="sxs-lookup"><span data-stu-id="61f84-120">Merged Resource Dictionaries</span></span>](../advanced/merged-resource-dictionaries.md)
