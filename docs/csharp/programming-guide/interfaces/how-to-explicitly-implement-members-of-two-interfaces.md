---
title: 'Nasıl yapılır: İki Arabirimin Üyelerini Açıkça Uygulama (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [C#], explicitly implementing interface members
- interfaces [C#], explicitly implementing with inheritance
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
ms.openlocfilehash: c73089fdbf1350c1aff68ac3e8e78be00e21b931
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339046"
---
# <a name="how-to-explicitly-implement-members-of-two-interfaces-c-programming-guide"></a><span data-ttu-id="11557-102">Nasıl yapılır: İki Arabirimin Üyelerini Açıkça Uygulama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="11557-102">How to: Explicitly Implement Members of Two Interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="11557-103">Açık [arabirimi](../../../csharp/language-reference/keywords/interface.md) uygulaması aynı üye adlarının ve ayrı bir uygulama her arabirim üyesini vermek iki arabirimlerini Programcı de sağlar.</span><span class="sxs-lookup"><span data-stu-id="11557-103">Explicit [interface](../../../csharp/language-reference/keywords/interface.md) implementation also allows the programmer to implement two interfaces that have the same member names and give each interface member a separate implementation.</span></span> <span data-ttu-id="11557-104">Bu örnek bir kutusunun boyutlarını ölçüm hem İngilizce birimleri de görüntüler.</span><span class="sxs-lookup"><span data-stu-id="11557-104">This example displays the dimensions of a box in both metric and English units.</span></span> <span data-ttu-id="11557-105">Kutunun [sınıfı](../../../csharp/language-reference/keywords/class.md) IEnglishDimensions ve farklı ölçüm sistemleri temsil eden IMetricDimensions iki arabirimlerini uygular.</span><span class="sxs-lookup"><span data-stu-id="11557-105">The Box [class](../../../csharp/language-reference/keywords/class.md) implements two interfaces IEnglishDimensions and IMetricDimensions, which represent the different measurement systems.</span></span> <span data-ttu-id="11557-106">Her iki arabirimde aynı üye adları, uzunluğu ve genişliği vardır.</span><span class="sxs-lookup"><span data-stu-id="11557-106">Both interfaces have identical member names, Length and Width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11557-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="11557-107">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_1.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="11557-108">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="11557-108">Robust Programming</span></span>  
 <span data-ttu-id="11557-109">Varsayılan ölçümleri İngilizce birimlerinde yapmak istiyorsanız, uzunluğu ve genişliği yöntemleri normalde uygulamak ve açıkça IMetricDimensions arabiriminden uzunluk ve genişlik yöntemleri uygulayın:</span><span class="sxs-lookup"><span data-stu-id="11557-109">If you want to make the default measurements in English units, implement the methods Length and Width normally, and explicitly implement the Length and Width methods from the IMetricDimensions interface:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_2.cs)]  
  
 <span data-ttu-id="11557-110">Bu durumda, İngilizce birimleri sınıfı örnekten erişmek ve ölçüm birimleri arabirimi örneğinden erişebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="11557-110">In this case, you can access the English units from the class instance and access the metric units from the interface instance:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="11557-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="11557-111">See Also</span></span>  
 [<span data-ttu-id="11557-112">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="11557-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="11557-113">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="11557-113">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="11557-114">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="11557-114">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)  
 [<span data-ttu-id="11557-115">Nasıl yapılır: Arabirim Üyelerini Açıkça Uygulama</span><span class="sxs-lookup"><span data-stu-id="11557-115">How to: Explicitly Implement Interface Members</span></span>](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-interface-members.md)
