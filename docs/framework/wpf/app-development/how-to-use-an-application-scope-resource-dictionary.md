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
ms.openlocfilehash: 6cd3e125b5b1a97f5851d4d1845e3e9e384e3d16
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56748563"
---
# <a name="how-to-use-an-application-scope-resource-dictionary"></a><span data-ttu-id="e9926-102">Nasıl yapılır: Uygulama Kapsamı Kaynak Sözlüğü Kullanma</span><span class="sxs-lookup"><span data-stu-id="e9926-102">How to: Use an Application-Scope Resource Dictionary</span></span>
<span data-ttu-id="e9926-103">Bu örnekte, tanımlamak ve bir özel uygulama kapsamı kaynak sözlüğü kullanma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e9926-103">This example shows how to define and use an application-scope custom resource dictionary.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9926-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="e9926-104">Example</span></span>  
 <span data-ttu-id="e9926-105"><xref:System.Windows.Application> Paylaşılan kaynaklar için bir uygulama kapsamı store kullanıma sunar: <xref:System.Windows.Application.Resources%2A>.</span><span class="sxs-lookup"><span data-stu-id="e9926-105"><xref:System.Windows.Application> exposes an application-scope store for shared resources: <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="e9926-106">Varsayılan olarak, <xref:System.Windows.Application.Resources%2A> örneği ile özelliğinin başlatıldığı <xref:System.Windows.ResourceDictionary> türü.</span><span class="sxs-lookup"><span data-stu-id="e9926-106">By default, the <xref:System.Windows.Application.Resources%2A> property is initialized with an instance of the <xref:System.Windows.ResourceDictionary> type.</span></span> <span data-ttu-id="e9926-107">Almanıza ve ayarlamanıza, uygulama kapsamı özelliklerini kullanarak, bu örneği kullanmak <xref:System.Windows.Application.Resources%2A>.</span><span class="sxs-lookup"><span data-stu-id="e9926-107">You use this instance when you get and set application-scope properties using <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="e9926-108">Daha fazla bilgi için [nasıl yapılır: GET ve Set uygulama kapsamı kaynak](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348547(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="e9926-108">For more information, see [How to: Get and Set an Application-Scope Resource](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348547(v=vs.100)).</span></span>
  
 <span data-ttu-id="e9926-109">Kullanılarak ayarlanan birden fazla kaynak varsa <xref:System.Windows.Application.Resources%2A>, bunun yerine özel bir kaynak sözlüğü bu kaynakları saklamak ve ayarlamak için kullanabileceğiniz <xref:System.Windows.Application.Resources%2A> onunla yerine.</span><span class="sxs-lookup"><span data-stu-id="e9926-109">If you have multiple resources that you set using <xref:System.Windows.Application.Resources%2A>, you can instead use a custom resource dictionary to store those resources and set <xref:System.Windows.Application.Resources%2A> with it instead.</span></span> <span data-ttu-id="e9926-110">XAML kullanarak bir özel kaynak sözlüğü bildirdiğiniz nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="e9926-110">The following shows how you declare a custom resource dictionary using XAML.</span></span>
  
 [!code-xaml[HOWTOResourceDictionaries#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MyResourceDictionary.xaml#1)]  
  
 <span data-ttu-id="e9926-111">Kullanarak tüm kaynak sözlüklerini takas <xref:System.Windows.Application.Resources%2A> uygulama kapsamı Temalar desteklemek, burada her teması saklanmış olduğu tek bir kaynak sözlüğü sağlar.</span><span class="sxs-lookup"><span data-stu-id="e9926-111">Swapping entire resource dictionaries using <xref:System.Windows.Application.Resources%2A> allows you to support application-scope themes, where each theme is encapsulated by a single resource dictionary.</span></span> <span data-ttu-id="e9926-112">Aşağıdaki örnek nasıl ayarlanacağını gösterir <xref:System.Windows.ResourceDictionary>.</span><span class="sxs-lookup"><span data-stu-id="e9926-112">The following example shows how to set the <xref:System.Windows.ResourceDictionary>.</span></span>  
  
 [!code-xaml[HOWTOResourceDictionaries#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/App.xaml#2)]  
  
 <span data-ttu-id="e9926-113">Kaynak sözlüğünden tarafından kullanıma sunulan uygulama kapsamı kaynak nasıl alabileceğiniz aşağıdaki gösterilir <xref:System.Windows.Application.Resources%2A> XAML içinde.</span><span class="sxs-lookup"><span data-stu-id="e9926-113">The following shows how you can get application-scope resources from the resource dictionary exposed by <xref:System.Windows.Application.Resources%2A> in XAML.</span></span>  
  
 [!code-xaml[HOWTOResourceDictionaries#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml#4)]  
  
 <span data-ttu-id="e9926-114">Aşağıdaki nasıl da kaynak kodu alabilirsiniz gösterir.</span><span class="sxs-lookup"><span data-stu-id="e9926-114">The following shows how you can also get the resources in code.</span></span>  
  
 [!code-csharp[HOWTOResourceDictionaries#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml.cs#3)]
 [!code-vb[HOWTOResourceDictionaries#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToResourceDictionaries/VB/MainWindow.xaml.vb#3)]  
  
 <span data-ttu-id="e9926-115">Kullanırken yapmak için iki nokta vardır <xref:System.Windows.Application.Resources%2A>.</span><span class="sxs-lookup"><span data-stu-id="e9926-115">There are two considerations to make when using <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="e9926-116">İlk olarak, sözlük *anahtar* bir nesne olduğundan, bir özellik değerini alırken ve tam olarak aynı nesne örneğini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e9926-116">First, the dictionary *key* is an object, so you must use exactly the same object instance when both setting and getting a property value.</span></span> <span data-ttu-id="e9926-117">(Anahtar bir dize kullanarak büyük küçük harfe duyarlı olduğunu unutmayın.) İkincisi, sözlük *değer* bir nesne olduğundan, bir özellik değeri alınırken değeri istenen türe dönüştürmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="e9926-117">(Note that the key is case-sensitive when using a string.) Second, the dictionary *value* is an object, so you will have to convert the value to the desired type when getting a property value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9926-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9926-118">See also</span></span>
- <xref:System.Windows.ResourceDictionary>
- <xref:System.Windows.Application.Resources%2A>
- [<span data-ttu-id="e9926-119">XAML Kaynakları</span><span class="sxs-lookup"><span data-stu-id="e9926-119">XAML Resources</span></span>](../../../../docs/framework/wpf/advanced/xaml-resources.md)
- [<span data-ttu-id="e9926-120">Birleştirilmiş Kaynak Sözlükleri</span><span class="sxs-lookup"><span data-stu-id="e9926-120">Merged Resource Dictionaries</span></span>](../../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md)
